---
tags:
  - Studies
  - Acronym
  - Networking
aliases:
  - VLAN ID
  - VLAN Identifier
description: A VLAN Identifier field used within ethernet frames when trunking.
---
VID (VLAN Identifier) is a ==12-bit field== within the IEEE's 802.1Q [[VLANs|VLAN]] tag's [[TCI]] that uniquely identifies a VLAN when using [[Trunking]], allowing network devices to understand and appropriately process [[The Ethernet Frame|Ethernet Frames]] in VLAN-enabled networks.

Being 12 bits in length, it is capable of storing an ID for up to ==4095 VLANs==. Bear in mind that VLANs 0, and 4095, are reserved and can't be used so the actual possible range of VLANs is 1 - 4094 as detailed here: [[VLANs#VLAN Ranges]].

