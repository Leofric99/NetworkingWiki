---
tags:
  - Studies
  - Acronym
  - Networking
  - CCNA
  - Theory
aliases:
  - Bridge Protocol Data Units
description: Messages exchanged between network devices to share information about the spanning tree topology and prevent loops.
---
Bridge Protocol Data Units (BPDUs) are essential messages in network bridging protocols, particularly in the context of [[STP]]. 

BPDUs are exchanged between network devices, such as switches, to convey information about the network's topology and help prevent loops in Ethernet-based networks. 

## Structure

Each BPDU contains a [[BID]] that identifies which switch sent the BPDU. The BID is involved in making many of the [[STA]] decisions including root bridge and port roles.

> [!note]-
> For the CCNA you don't need to know this diagram.

![[BPDUs-20240305114623474.webp#invert]]

## Operation

Once the [[STP#Electing the Root Bridge|root bridge has been elected]], only this root bridge will send BPDUs for the entire topology.