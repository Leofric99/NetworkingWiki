---
tags:
  - Studies
  - CyberSecurity
  - Theory
description: A set of rules that an IDS or IPS uses to detect malicious activity.
---
The network must be able to identify incoming malicious traffic in order to stop it. Fortunately, malicious traffic displays distinct characteristics or “signatures”.

[[IPS]] sensors in-particular must be tuned to look for matching signatures or ==abnormal traffic patterns==. As sensors scan network packets, they use signatures to detect known attacks and respond with predefined actions.

## Signature Attributes

These signatures have three distinctive attributes. [[IDS and IPS Signatures#Signature Type|Type]], [[IDS and IPS Signatures#Signature Triggers|Trigger]], and [[IDS and IPS Signatures#Signature Actions|Actions]]. The type is the type of signature. Either atomic, or composite. The trigger is also known as the alarm, and the action is what the IPS will do.

### Signature Type

Some threats can be identified in one packet while other threats may require many packets and their state information to identify a threat. This is what the *type* determines

There are two *types* of signature:

**Atomic Signatures**, as the name would suggest, are the signatures which are 'given off' from [[Atomic Attacks]]. With this signature, the IPS does not need to maintain state information and traffic analysis can usually be ==performed very quickly== and efficiently.

**Composite Signatures**, also called a stateful signature, ==requires several pieces of data== to match an attack signature. The IPS must also maintain state information, which is referred to as the event horizon. The length of an event horizon varies from one signature to the next.

### Signature Triggers

The [[IPS]] signature alarm is analogous to the alarm in a home security system. The triggering mechanism for a burglar alarm could be a motion detector. When the burglar alarm is enabled, the movement of an individual entering a room is detected. This triggers the alarm.

here are four general IPS signature trigger categories as listed in the table.

| Trigger Type | Information |
| :--- | :--- |
| Pattern-Based | Also known as signature-based detection.<br><br>Has the ==simplest triggering mechanism== as it searches for a specific and pre-defined atomic or composite pattern.<br><br>The IPS sensor compares the network traffic to a database of known attacks, and triggers an alarm or prevents communication if a match is found. |
| Anomaly-Based | Also known as profile-based detection.<br><br>Involves first defining a ==profile of what is considered normal== network or host activity.<br><br>Once defined, any activity beyond a specified threshold in the normal profile will generate a signature trigger and action. |
| Policy-Based | Also known as behaviour-based detection.<br><br>Although similar to pattern-based detection, an ==administrator manually defines== behaviours that are suspicious based on historical analysis.<br><br>The use of behaviours enables a single signature to cover an entire class of activities without having to specify each individual situation. |
| Honey Pot-Based | Honey pot-based detection ==uses a server as a decoy== server to attract attacks.<br><br>Allows administrators time to analyse incoming attacks and malicious traffic patterns to tune their sensor signatures. |
### Signature Actions

When a signature detects the activity for which it is configured, the signature ==triggers one or more actions==.

Depending on the IPS sensor, ==various actions can be enabled==. The table lists some actions that an IPS sensor may provide.

| Alert Category | Specific Action | Description |
| :--- | :--- | :--- |
| Generate an alert | Produce alert | The IPS sends events as alerts. |
| Generate an alert | Produce verbose alert | The IPS sends a detailed event alert. |
| Log the activity | Log attacker packets | Logs packets from the attacker IP address and sends an alert. |
| Log the activity | Log pair packets | Logs packets from the victim and attacker IP addresses and sends an alert. |
| Log the activity | Log victim packets | Logs packets from the victim IP address and sends an alert. |
| Deny the activity | Deny packet inline | Terminates the packet. |
| Deny the activity | Deny connection inline | Terminates the current packet and future packets on this TCP flow. |
| Deny the activity | Deny attacker inline | Terminates the current packet and future packets from this attacker address for a specified period of time. |
| Reset the TCP connection | Reset TCP connection | Sends TCP resets to hijack and terminate the TCP flow. |
| Block future activity | Request block connection | Sends a request to a blocking device to block this connection. |
| Block future activity | Request block host | Sends a request to a blocking device to block this attacker host. |
| Block future activity | Request SNMP trap | Sends a request to the notification application component of the sensor to perform SNMP notification. |

*Note: The available actions depend on the signature type and the platform.*

## Evaluating Alerts

Triggering mechanisms can generate alarms that are false positives or false negatives. These alarms must be addressed when implementing an IPS sensor. 

True positives and true negatives are desirable and indicate the IPS is functioning properly. ==False positives and false negatives are undesirable== and must be investigated.

The table summarises the following four types of alarms:

|Alarm Type|Network Activity|IPS Activity|Outcome|
|---|---|---|---|
|True positive |Attack traffic|Alarm generated|Ideal setting|
|True negative |Normal user traffic|No alarm generated|Ideal setting|
|False positive |Normal user traffic|Alarm generated|Tune alarm|
|False negative |Attack traffic|No alarm generated|Tune alarm|
#### True Positives

This is used when the [[IPS]] generates an alarm because it detected known attack traffic. The alert has been verified to be an actual security incident and also indicates that the ==IPS rule worked correctly==.

#### True Negatives

This is used when the system is performing as expected. No alerts are issued because the traffic that is passing through the system is ==clear of threats==.

#### False Positives

This is used when an IPS generates an alarm after processing normal user traffic that should not have triggered an alarm. ==The IPS must be tuned== to change these alarm types to true negatives. 

The alert ~~does not~~ indicate an actual security incident. Benign activity that results in a false positive is sometimes referred to as a benign trigger. False positives are costly because they must be investigated.

#### False Negatives

This is used when an ==IPS fails to generate an alarm== and known attacks are not being detected. This means that exploits are not being detected by the security systems that are in place. 

These incidents could go undetected for a long time, and ongoing data loss and damage could result. The goal is for these alarm types to generate true positive alarms.