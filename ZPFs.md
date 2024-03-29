---
tags:
  - Studies
  - Acronym
  - CyberSecurity
  - Theory
  - COM512
aliases:
  - Zone-based Policy Firewalls
description: Allows interfaces to be assigned to zones to determine screening rules.
---
Zone-based policy firewalls (ZPFs) are a step beyond classic firewalls. While classic firewalls base security configuration on router interfaces, a Zone-based Policy Firewall allows interfaces to be assigned to zones.

Security ==policies== on these firewalls are ==defined based on each zone==, and the security relationships between each zone. Multiple interfaces can be made members of a zone and zone policies will be applied to those interfaces by their nature, not by the IP networks that are communicating through said interface(s). 

These two types of [[Firewalls|firewall]] are reflected within the Cisco IOS configuration of compatible routers.

> [!example]-
> 
> In the image, there are three zones. Private, [[DMZ]], and Public.
> 
> When using ZPFs, interfaces assigned to a certain zone are permitted to communicate without interference, and any new interfaces added to a zone can also communicate without being checked. However, ==traffic between zones is scrutinised==.
> 
> ![[ZPFs-20240216134214580.webp#invert|590]]

## Why use ZPFs?

The primary motivations for network security professionals to migrate to the ==ZPF model== are ==structure and ease of use==. The structured approach is useful for documentation and communication. The ease of use makes network security implementations more accessible to a larger community of security professionals.

| Benefit | Explanation |
| :--- | :--- |
| Not Dependant on [[ACLs]] | N/A |
| Policies are easy to read and troubleshoot. | Thanks to the [[C3PL]], this provides scalability because one policy affects any given traffic, instead of needing multiple ACLs and inspection actions for different types of traffic. |
| Interfaces can be grouped into zones. | Both virtual and physical. |
| Policies are applied to unidirectional traffic between zones | N/A |
| The router security posture is to block unless explicitly allowed. | N/A |

When deciding whether to implement a classic [[Firewalls|firewall]] or a ZPF, it is important to note that ==both configuration models can be enabled concurrently on a router==. However, the models cannot be combined on a single interface. For example, an interface cannot be simultaneously configured as a security zone member and for IP inspection. 

For information about designing a ZPF from scratch, see [[ZPF Design]]. For more information about how ZPFs work, see [[ZPF Operation]]. To learn how to configure a ZPF in Cisco IOS, see [[ZPF Commands]].