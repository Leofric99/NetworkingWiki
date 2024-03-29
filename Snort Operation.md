---
tags:
  - Studies
  - CyberSecurity
  - Theory
description: Snort is an open source network IPS that performs real-time traffic analysis and generates alerts.
cssclasses:
  - programming
---
Snort is an open source network [[IPS]] that performs real-time traffic analysis and generates alerts when threats are detected on IP networks. To read a boarder overview of Snort, click [[Snort|here]].

Packets arriving on Snort enabled interfaces are inspected as follows:

1. Cisco IOS Software forwards the packets to be inspected to the Snort IPS engine using an internal [[VPG]] interface.
2. Snort IPS inspects the traffic and takes necessary action.
3. Snort drops the packets associated with bad flows (IPS mode). Good flow packets are returned back to the router for further processing.

Packet exchange between the container applications and the IOS data plane is done using VPG interfaces. These routed interfaces are connected through the router back plane. The corresponding interface on the container side will appear as virtual Ethernet ports.

## Snort IPS [[VPG]] Interfaces

Snort IPS requires two VPG interfaces. A Management interface, and a Data interface.

The Management Interface is the interface that is used to source logs to the log collector and for retrieving signature updates from Cisco.com. For this reason, this interface requires a routable IP address.

The Data Interface is the interface that is used to send user traffic between the Snort virtual container service and the router forwarding plane.

In the image example, VPG0 is used for Snort management traffic while VPG1 is used for user traffic to be inspected. User traffic to be inspected is forwarded to the Snort engine using VPG1 as shown. Traffic is then inspected and either rejected (dropped) or forwarded back to the router as shown.

![[Snort Operation-20240222130251820.webp#invert|500]]

## Snort IPS Rule Alarms

In Snort IPS, signatures are configured using “rules”. These rules serve as the signature alarms by comparing incoming traffic to the Snort rules. Traffic ==matching== a rule header ==generates an action==.

A rule header is conceptually similar to an access control list ([[ACLs|ACL]]) statement. It is a one line statement that identifies malicious traffic. The basic rule command syntax is as follows. See the image following the syntax for an example.

```
[_action_] [_protocol_] [_sourceIP_] [_sourceport_] > [_destIP_] [_destport_] ([_Rule options_])
```

![[Snort Operation-20240222124856667.webp#invert]]

## Snort IPS Rule Actions

Snort can be enabled in either [[IDS]] or [[IPS]] mode. In IDS mode, Snort can perform three actions: Alert, Log, and Pass.

- **Alert** will generate an alert using the selected alert method.
- **Log** will log the packet.
- **Pass** will ignore the packet.

In IPS mode, Snort can perform all the actions above *and* three more. Drop, Reject, and Sdrop.

- **Drop** will block and log the packet.
- **Reject** will block the packet, log it, and then send a TCP reset if the protocol is [[TCP]] or an [[ICMP]] port unreachable message if the protocol is [[UDP]].
- **Sdrop** will block the packet but not log it.

## Snort IPS Header Options

A Snort rule header also contains rule options (fields) to ==provide additional information== for the rule. Options are separated by semicolons (;) and the rule option keywords are separated from their arguments using colons (:).

The image displays an example of what the Snort IPS Header would contain:

![[Snort Operation-20240222125625166.webp#invert|400]]

The table below describes the common general rule and the detection rule options in the sample rule header.

|Rule Option|Specific Action|
|---|---|
|`msg:` |This is a simple text string that provides a meaningful message to output when the rule matches.|
|`flow:` |Specifies the direction of network traffic.|
|`content:` |A detection rule option that allows the rule creator to set rules that search for specific content in the packet payload and trigger response based on that data. This option data can contain mixed text and binary data|
|`distance: / offset:` |Detection rule keywords that allow the rule creator to specify where to start searching relative to the beginning of the payload or the beginning of a content match.|
|`within: / depth:` |Detection rule keywords that allow the rule creator to specify how far forward to search relative to the end of a previous content match and, once that content match is found, how far to search for it.|
|`pcre` |A detection rule keyword that allows rules to be written using “perl compatible regular expressions” which allows for more complex matches.|
|`byte_test` |A detection rule keyword that allows a rule to test a number of bytes against a specific value in binary.|
|`metadata:` |Allows a rule creator to embed additional information about the rule.|
|`reference:` |Allows rules to include references to external sources of information.|
|`classtype:` |Identifies the potential effect of what a successful attack would be.|
|`sid / rev` |The signature ID (**sid**) is a unique identifier for each rule making them easy to identify. It should be used with the **rev** (revision) keyword to indicate the current version of the rule.|
