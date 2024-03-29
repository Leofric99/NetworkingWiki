---
tags:
  - Studies
  - CyberSecurity
---
[[IDS]] and [[IPS]] sensors can operate in inline mode (aka inline interface pair mode) or promiscuous mode (aka passive mode).

## Inline Mode

As shown in the image below, operating in inline mode puts the IPS directly into the traffic flow and ==makes packet-forwarding rates slower== by adding latency. Inline mode allows the sensor to stop attacks before they reach the target.

![[IDS and IPS Modes-20240219134557589.webp#invert]]

The inline IPS device ==can analyse packets by information from layers 3 - 7==. This deeper analysis lets the system identify and stop or block attacks that would pass through a traditional firewall device.

An IDS sensor could also be deployed inline. In this case, the IDS would be configured so that it only sends alerts and does not drop any packets.

## Promiscuous Mode

As shown in the image, packets do not flow through the sensor in promiscuous mode. 

The sensor analyses a *copy* of the monitored traffic, not the actual forwarded packet. The advantage of operating in promiscuous mode is that the sensor ==does not affect the packet flow== with the forwarded traffic. 

![[IDS and IPS Deployment-20240219133738679.webp#invert|450]]

The disadvantage of operating in promiscuous mode is that the sensor ==cannot stop all malicious traffic from reaching its intended target==. For example, it cannot stop [[Atomic Attacks]].

The response actions implemented by promiscuous sensor devices are ==post-event responses== and often require assistance from other networking devices (for example, routers and firewalls) to respond to an attack.