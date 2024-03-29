---
tags:
  - "#Studies"
  - Networking
  - CCNA
  - Theory
  - COM414
aliases:
  - Link Aggregation
  - Port Aggregation
  - Link Aggregation Group
  - LAG
  - Port Channel
description: A port link aggregation technology.
---
EtherChannel is a port link aggregation [[LAg]] technology or port-channel architecture used primarily on Cisco switches.

## Why are [[LAg]] technologies needed?

Imagine that there are many hosts connected to a switch. That switch is connected to another switch by one cable. This cable alone ==isn't capable of handling the bandwidth== of all these hosts at once.

A network administrator could ==add more connections== between the switches as shown in the diagram below, but due to [[STP]], all but one of these connections will be shut down because if they weren't then loops within these four cables could form.

![[EtherChannel-20240316144027485.webp#invert]]

The solution is to bind all of these cables into ==one single virtual link==. If both switches agree that these four cables are one high-capacity cable, and acts accordingly, then [[STP]] will not deactivate any of the interfaces. This is what happens when all cables are [[LAg|aggregated]] into one EtherChannel (or alternatives) as shown below:

![[EtherChannel-20240316144436550.webp#invert]]

*Note: Traffic being sent over any aggregated link will only be sent once like a physical link. EtherChannel load balances between the physical cables.*

## EtherChannel Flows

EtherChannel manages load balancing by working with the concept of 'Flows'. 

Think of a flow like a [[TCP]] connection. Any given communication sequence from and to specific devices within the network will be load balanced on the same physical cable over the Link Aggregation Group.

If frames within the communication sequence are load balanced onto different ports, this could cause the frames to arrive out of order which could introduce issues for [[UDP]] based protocols.

![[EtherChannel-20240316154225180.webp#invert]]

It is possible to change what the switches will use as the parameter for determining which physical cable to use for certain devices across the LAG. The options are:

- Source and/or Destination [[Studies/MAC|MAC Address]].
- Source and/or Destination IP Address.

## Creating an EtherChannel

The commands used to configure EtherChannels are [[EtherChannel Commands|here]], but before using them, it is important to remember that all member interfaces of a port channel group *must* have matching configurations or they won't aggregate. This includes:

- Duplex mode
- Transfer speed
- Switchport mode (Access/[[Trunking|Trunk]])
- Permitted & Native [[VLANs]]

## Layer Three EtherChannels

Although EtherChannels prevent [[STP]] from blocking aggregated links, it can still cause problems in layer two networks with EtherChannels. Take the diagram below. If a network had layer two switches and EtherChannels configured like this, STP could still (rightly) block a port to prevent layer two loops.

*Note: This diagram shows layer three switches. They should be layer two ones.*

![[EtherChannel-20240316154707630.webp#invert|200]]

This is where using layer three switches can help. As they are routed, STP will not play a part in the [[EtherChannel Commands#Layer Three EtherChannel Configuration|layer three EtherChannel configuration]].