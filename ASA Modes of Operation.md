---
tags:
  - Studies
  - CyberSecurity
  - Theory
aliases:
  - Adaptive Security Appliance Modes of Operation
description: Details the two ASA modes which ASA devices can be placed into.
---
There are two firewall interface modes of operation available on [[ASAs|ASA]] devices: [[ASA Modes of Operation#Routed Mode|Routed Mode]], and [[ASA Modes of Operation#Transparent Mode|Transparent Mode]].

## Routed Mode

In routed mode, ==two or more== interfaces separate Layer 3 networks (i.e., domains). In the figure, the ASA is considered to be a router hop in the network and can perform NAT between connected networks. 

![[ASAs-20240314135545608.webp#invert|250]]

Routed mode ==supports multiple interfaces==. Each interface is on a ==different subnet== and requires an IP address on that subnet. The ASA applies policies to flows as they transit the firewall.

## Transparent Mode

An ASA in transparent mode is often referred to as a *“bump in the wire”*, or a *“stealth firewall”* because the [[ASAs|ASA]] functions like a Layer 2 device and is not considered a router hop. 

![[ASAs-20240314135731886.webp#invert|400]]

In the image above, the ASA is only assigned an IP address on the local network for management purposes. 

This mode is useful to simplify a network configuration, or when the existing IP addressing cannot be altered. However, the drawbacks include no support for dynamic routing protocols, [[VPNs]], [[QoS]], or DHCP Relay.
