---
tags:
  - Studies
  - Networking
  - CCNA
  - Theory
  - Acronym
  - COM414
aliases:
  - Spanning Tree Protocol
  - IEEE 802.1D
description: Used to prevent layer two loops and broadcast storms in redundant layer two networks.
---
The Spanning Tree Protocol (STP) is a network protocol that builds a ==loop-free logical topology== for Ethernet networks. 

> [!info]- QRH
> Click [[QRH-STP.pdf|here]] for the quick reference handbook.

The basic function of STP is to ==prevent switch loops== and the broadcast radiation that results from them whilst enabling redundant switches to be implemented. The image below shows a broadcast storm.

![[STP-20240306093518605.webp#invert]]

It was introduced by the [[IEEE]] in 802.1D. It is not a proprietary protocol and so will be found on any layer two switch.

## STP Operation

Switches with STP enabled will begin to send out 'Hello' [[BPDUs]] to indicate to other switches that they have STP enabled. Then, once switches have established their neighbours, they will [[STP#Electing the Root Bridge|elect the root bridge]]. 

This hierarchy ensures a stable and loop-free network topology by designating a central point for [[STP#The Root Path Cost|calculating the root path]] and avoiding potential loops.

After electing the root bridge, they will elect the [[STP#Electing Ports|elect the root ports]], designated ports, and alternate ([[STP#Timers and Port States|blocking]]) ports using the [[STA]].

## Electing the Root Bridge

By default, all switches will ==assume that they are the root bridge== until they realise they aren't. Therefore they will send [[BPDUs]] until a 'successor' root bridge has been elected.

The root bridge is elected based on the concept of [[BID|Bridge ID]]. The switch with the lowest Bridge ID is elected as the root bridge. Unlike the other switches in the topology, *all* ports on the root bridge will be ==Designated ports== (in a forwarding state).

If multiple switches share the same priority, the one with the lowest [[Studies/MAC|MAC Address]] is selected. 

> [!note]
> By default, Cisco switches have a priority of `32768`, making the MAC Address the deciding factor. Administrators can manually set priorities to influence root bridge selection.

> [!example]-
> In the example below, Switch 1 will be the Root Bridge, as the [[BID]] is the lowest. An Administrator should configure the BID manually if he wishes to manually specify the Root Bridge. 
> 
> ![[STP-20240305111515451.webp#invert|590]]
> 
> It doesn’t matter what the BID is as long as it is lower than the others (if it is to be the Root Bridge).


## Electing Ports

After the Root Bridge has been established, the [[STA]] is used to select the root port using [[STA#Root Path Cost]]. The path on a given switch with the lowest root path cost to the root bridge *will* be the 'Root Port'.

With the Root port calculated, designated and alternate ports must be determined. ==Designated ports== are any port that is not a root port (unless the port in question becomes the alternate port). They ==face away from the root bridge==. The designated ports will be placed in a [[STP#Timers and Port States|forwarding state]].

The ==Alternate port(s)== will be ==calculated automatically== by STA and will be placed in a [[STP#Timers and Port States|blocking state]].

When a switch has ==multiple equal-cost paths== to the root bridge, the switch will determine a port using the following criteria:*

- Lowest sender [[BID]]
- Lowest sender port priority
- Lowest sender port ID

> [!example]-
> 
> In this example, the connection between S2 and S1 is 100Mbps, and therefore the link (as there is only one hop) is 19. 
> 
> ![[STP-20240305113200113.webp#invert|590]]
> 
> Path two has two hops at the same speed, but therefore the Root Path Cost is 38. Root Path Cost of 19 wins. This is now the path to the Root Bridge determined.
> 
> In this case the root port is the port on the switch which has the lowest path cost to forward data to the root bridge, so for S3 it’s F0/1, and for S2 it’s F0/1 also.
> 
> ==Designated ports== on the other hand, ==face away== from the root bridge (they may also be on the root bridge) and are the port with the smallest path cost to the switches away from the root bridge. This will almost always be the other end from a root port. A designated port can be seen here:
> 
> If a port is not a root port or a designated port, then it becomes an alternate (backup) port. Alternate ports are set to a discarding or blocking state to prevent loops as can be seen here:
> 
> ![[STP-20240305113848803.webp#invert|590]]

## Timers and Port States

STP takes time to set up, which is why a switch ==will not begin forwarding packets immediately==. STP convergence requires three timers as follows:

| Timer               | Description                                                                                                                                                                                           |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Hello Timer         | This is the interval between [[BPDUs]]. The default is two seconds, but can be changed to anything from 1 - 10 seconds.                                                                               |
| Forward Delay Timer | The forward delay is the time that is spent in the listening and learning state (when the switch is first plugged in) The default is 15 seconds but that can be modified to between 4 and 30 seconds. |
| Max Age Timer       | The maximum length of time that a switch waits before attempting to change the STP topology. The default is 20 seconds, but can be changed to anything from 6 - 40 seconds.                           |
The diagram below shows what phases switches go through when a new link is connected to the switch (trunk link). 

> [!note]
> The two blocking stages below are the same and could be merged.

![[STP-20240305114341763.webp#invert]]

For the commands, see [[STP Commands]].