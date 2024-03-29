---
tags:
  - Studies
  - CyberSecurity
aliases:
  - Zone-based Policy Firewall Design
---
There are *four* different steps you should consider when beginning the design of a [[Layered Network Defences|layered network defence]] using [[ZPFs|zone-based policy firewalls]].

## Designing the Zones

Zones establish the security borders of a network. A zone defines a boundary where traffic is scrutinised by policies as it crosses to another region of the network like national borders.

For example, a public network would be one zone and an internal network would be another zone.

## Establishing Policies Between Zones

For each pair of *source to destination* zones (such as from the inside network to the outside internet) the network administrator will need to define what sessions clients in the source zones can establish with servers in destination zones. 

For traffic that is *not* based on the concept of sessions, the administrator must define unidirectional traffic flows from source to destination and vice versa. Policies are *unidirectional* and are defined based on source and destination zones, which are known as zone pairs.

## Designing the Physical Infrastructure

After the zones have been identified, and the traffic requirements between them documented, the administrator must design the physical infrastructure. 

The administrator must take into account security and availability requirements when designing the physical infrastructure. This includes dictating the number of devices between most-secure and least-secure zones and determining redundant devices.

## Identifying Subnets & Merging Traffic Requirements

For each firewall device in the design, the administrator must identify zone subsets that are connected to its interfaces and merge the traffic requirements for those zones. 

For example, multiple zones might be indirectly attached to a single interface of a firewall. This would result in a device-specific interzone policy. Although an important consideration, implementing zone subsets is beyond the scope of this curriculum.

> [!example]-
> 
> Some example ZPF topology implementations can be seen in the images below:
> 
> [[ZPF Design-20240216141747139.webp|LAN-to-Internet ZPF]]
> 
> [[ZPF Design-20240216142031154.webp|Firewall with Public Servers]]
> 
> [[ZPF Design-20240216142110867.webp|Redundant Firewalls]]