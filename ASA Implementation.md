---
tags:
  - Studies
  - CyberSecurity
  - Theory
aliases:
  - Adaptive Security Appliance Implementation
description: A guide to implementing ASAs within a network.
---
For details on where to place [[ASAs]] within a network, refer to [[Firewalls|Firewall]] implementations as part of a [[Layered Network Defences|Layered Network Defence]].

## General Implementation Rules

The ASA is a ==dedicated firewall appliance==. By default, it treats a defined inside interface as the trusted network and any defined outside interfaces as untrusted networks.

Each interface has an ==associated security level==. These security levels enable the ASA to implement security policies.

> [!note]-
> Security levels are sometimes called trust levels.

![[ASAs-20240314135302802.webp#invert]]

Network resources that are ==needed by outside users==, such as a web or FTP server, can be located in a [[DMZ]]. The firewall allows ~~limited~~ access to the DMZ while protecting the inside network from outside users as shown in the image above.

> [!example]- Example Implementations
> ## Implementation in Small Branch Offices
> 
> In a small branch, a common deployment would include an inside network with security level `100` and an outside network with security level `0`, as shown in the image below.
> 
> ![[ASA Implementation-20240314142447156.webp#invert|590]]
> 
> ## Implementation in a Small Business
> 
> In the small business, as shown below, an [[ASAs|ASA]] (such as an ASA 5506-X) can be deployed with two different protected network segments. 
> 
> One segment is the ==inside network==, which connects workstations and IP phones. The other segment is the [[DMZ]], which connects a company web server. The outside interface is used to connect to the internet.
> 
> ![[ASA Implementation-20240314142617831.webp#invert|590]]
> 
> ## Implementation in an Enterprise
> 
> In an enterprise deployment, as shown below, the an [[ASAs|ASA]] can be used by telecommuters and home users to connect to a centralised location using a [[VPNs|VPN]].
> 
> ![[ASA Implementation-20240314142821855.webp#invert|590]]