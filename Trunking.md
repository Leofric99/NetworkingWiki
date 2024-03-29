---
tags:
  - "#Studies"
  - Networking
  - CCNA
  - Theory
  - COM414
aliases:
  - Trunk Ports
  - VLAN Trunking
description: Bundles multiple VLANs into a single connection.
---
Trunking is a the practice of implementing configurations so that multiple [[VLANs]] can be transported over a single physical connection. It enables efficient segregation and communication of different VLANs within a network infrastructure without wasting Router, or Switch, interfaces.

> [!note]
> Trunking can only be used between Switches and Routers. Not on access ports.

## Trunking Protocols

There are two main trunking protocols:

- [[ISL|ISL (Inter-Switch Link)]]
- IEEE 802.1Q

For the CCNA, you're only required to learn IEEE 802.1Q although you should be aware that ISL exists.

## IEEE 802.1Q

Trunking uses [[VLANs|VLAN]] ==tags to keep track of which frame belongs to which VLAN==. This way, multiple VLANs can occupy the same cable without becoming mixed up. Trunk ports are 'tagged' whereas access ports are 'untagged'.

802.1Q tags traffic to enable layer two devices to identify the VLAN that the frame is destined for. To do this, it inserts a 32bit, or 4byte, field between the *source* and *Type/Length* fields of [[The Ethernet Frame]] as shown in this image as *802.1Q*:

![[IEEE-20240214135303386.webp#invert|600]]

This Ethernet Frame tag consists of two main fields:

- [[TPID]]
- [[TCI]]

The image below displays the 802.1Q tag, and all its fields. The subdivisions of the TCI field are important to have a basic idea about for the CCNA: [[PCP]], [[DEI]], and [[VID]].

![[Trunking-20240214141835329.webp#invert|600]]

## The Native VLAN

Unlike [[ISL]], 802.1Q has a feature called the Native VLAN. This is ==set as VLAN 1 by default== on all ports configured as [[Trunking|Trunk Ports]] however it can (and should) be manually configured.

> [!important]
> Native VLAN traffic will not be tagged. Instead, any untagged traffic a switch receives will be assumed to be traffic for the native VLAN. Therefore it is *very important* that the native VLAN is the same throughout a layer two switched network to avoid a native VLAN mismatch.

For the Trunking commands, see [[VLAN Commands#Trunking Configuration]].