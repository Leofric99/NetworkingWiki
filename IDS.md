---
tags:
  - Studies
  - CyberSecurity
  - Acronym
  - Theory
  - COM512
aliases:
  - Intrusion Detection System
  - Intrusion Detection Systems
---
Intrusion Detection Systems (IDS) were implemented to passively monitor the traffic on a network by copying the traffic stream and analysing the copied traffic rather than the actual forwarded packets.

## IDS Operation

Working offline, the IDS compares the captured traffic stream with known malicious signatures, similar to software that checks for viruses. Working offline means several things:

- The IDS works ==passively==.
- The IDS device is physically positioned in the network so that traffic must be mirrored in order to reach it.
- Network traffic does not pass through the IDS unless it is mirrored.
- Very ==little latency== is added to network traffic flow.

Although the traffic is monitored, logged, and perhaps reported, no action is taken on packets by the IDS. This offline IDS implementation is referred to as [[IDS and IPS Modes#Promiscuous Mode|Promiscuous Mode]].

The image below shows how an IDS copies the packet stream for analysis:

![[IDS-20240219121809415.webp#invert|400]]

The advantage of operating with a copy of the traffic is that the IDS ==does not negatively affect the packet flow== of the forwarded traffic. The disadvantage of operating on a copy of the traffic is that the IDS cannot stop malicious single-packet attacks from reaching the target. An IDS often requires assistance from other networking devices, such as routers and firewalls, to respond to an attack.

A better solution is to use a device that can immediately detect and stop an attack. An [[IPS|Intrusion Prevention System]] performs this function.

## IDS Implementation

When deciding where to implement IDS, you don't necessarily need to separate it from the traffic flow. You can implement it into the traffic flow. For information on this, see [[IDS and IPS Modes]].

## Pros & Cons of Using an IPS

#### Pros
There are numerous benefits to using an IDS. Most notably that an IDS, unlike an [[IPS]], will not introduce any latency or jitter to network traffic, nor will it even if there is a sensor overload or failure.

#### Cons
There are a few drawbacks to an IDS. The main drawback being that malicious packets cannot be stopped even if they are detected to be malicious. Also, IDS's require finetuning in order to get the best results, and they are more vulnerable to network security evasion techniques.