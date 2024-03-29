---
tags:
  - Studies
  - Acronym
  - Networking
  - CCNA
  - Theory
  - COM414
aliases:
  - Virtual Local Area Network
  - Virtual LAN
description: A method of logically segmenting a physical network into multiple virtual networks at layer two.
---
A VLAN is a a Virtual [[LANs|Local Area Network]] which operates at layer two (Data-Link Layer) of [[The OSI Model]] to ==logically separate hosts at layer two==. [[IPv4 Subnetting|Subnets]] are the layer three equivalent.

> [!info]- QRH
> Click [[QRH-VLANs.pdf|here]] for the quick reference handbook.

All VLANs need a supporting layer three subnet to support routing between them. Hosts in one VLAN cannot communicate with hosts in another VLAN unless there is a router or layer 3 switch to provide routing services.

Configuring VLAN tagging will divide the [[Broadcast Domains|Broadcast Domain]] of a network into smaller pieces. They are configured on a ==per-interface basis==.
## Why are VLANs Needed?

VLANs are useful for two reasons:

### Security

==VLANs improve security== because when a broadcast frame is sent, the [[Broadcast Domains|Broadcast Domain]] is restricted to a smaller group of devices. In addition to this, [[ACLs]] take affect at a router, so transferring from one VLAN to another VLAN requires passing through a router which has the power to block these messages.

### Performance

They ==improve performance== because there is simply less traffic (in the form of broadcasts) traversing the network.

## Scalable VLANs

When building networks with more than a couple of [[LANs]] then assigning ==one port per VLAN== between the switch and router is ==not usually viable== as routers generally don't have more than a few ports. This is also wasteful whenever more than one VLAN is being used.

[[Trunking]] can be used to solve this problem. Where layer two switches are in use, this is the typical method for configuring VLANs within the network.

## VLAN Ranges

The range of usable VLANs is 1 - 4094. This ==range is split== up into two separate categories:

- Normal VLANs (1 - 1005)
- Extended VLANs (1006 - 4094)

> [!note]- Older Networking Devices
> Some older networking devices may not support the extended VLAN range.