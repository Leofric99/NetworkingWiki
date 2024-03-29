---
tags:
  - Studies
  - CyberSecurity
  - Theory
aliases:
  - Adaptive Security Appliance Features
description: Features available to ASA appliances.
---
  
This note page outlines the diverse range of features inherent in Cisco [[ASAs]], covering aspects such as [[Firewalls|Firewall]] functionality, [[IPS]], [[VPNs|VPN]], and advanced threat protection mechanisms. 

It serves as a reference document for understanding the capabilities of ASAs in securing network environments.

## Virtualisation Support

Cisco also supports the virtualisation of computing infrastructure by taking advantage of the increased power availability of modern x86 servers. Cisco's [[ASAv]] does just this to bring the power of ASA appliances to the virtual domain.

As in the image below, a single ASA can be partitioned into multiple virtual devices. Each of these virtual devices is ==called a security context==.



![[ASAs-20240314130610917.webp#invert]]

Each context is an ==independent device==, with its own security policy, interfaces, and administrators. Multiple contexts are similar to having multiple standalone devices, and most features are supported in this virtualised form (not including VPN and dynamic routing protocols).

## [[HA]] with Failover

As shown in the image below, two identical ASAs can be paired into an *active* */* *standby* failover configuration to provide device redundancy.

![[ASAs-20240314131316456.webp#invert]]

> [!note]
> Both platforms must be identical in software, licensing, memory, and interfaces, including the [[SSM]]. In the example, ASA-1 is the primary/active forwarding device and traffic leaving PC-1 takes the preferred path using ASA-1. ASA-1 and ASA-2 monitor each other using the LAN failover link. If ASA-1 fails, then ASA-2 would immediately assume the primary role and become active.*

## Identity [[Firewalls|Firewall]]

The ASA provides optional ==access control== based on an association of IP addresses to Windows Active Directory login information.

In the image below, when a client attempts to access the server resources, it must first be authenticated using the Microsoft Active Directory Identity-based firewall services. These services enhance the existing access control and security policy mechanisms by allowing users, or groups, to be specified in place of source IP addresses.

![[ASAs-20240314132222209.webp#invert]]

*Note: Identity-based security policies can be interleaved without restriction between traditional IP address-based rules.*

## Threat Control and Containment Services

*All* ASA models support ~~basic~~ [[IPS]] features.

However, advanced IPS features can only be provided by integrating special hardware modules with the ASA architecture. IPS capability is available using the [[AIP]] modules.

Antimalware capabilities can be deployed by integrating the [[CSC]] module. The Cisco [[AIP-SSM]] and Cisco [[AIP-SSC]] deliver protection against tens of thousands of known exploits.

![[ASAs-20240314133014646.webp]]

*Note: They also protect against millions of other unknown exploit variants using specialised [[IPS]] detection engines and thousands of signatures. Cisco Services for IPS provides signature updates through a global intelligence team that is working 24 hours a day to help ensure protection against the latest threats.*