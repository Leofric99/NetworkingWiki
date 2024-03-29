---
tags:
  - "#Studies"
  - Networking
  - CCNA
  - Theory
aliases:
  - OSPF Packets
  - OSPF Packet Types
  - Link State Packets
description: Packets which facilitate OSPF neighbour discovery, exchange of topology information, and synchronisation of link-state databases.
---
Link State Packets (LSPs) are the packets used by link-state routing protocols like [[OSPF]]. The table below summarises the five different types of LSPs used by OSPFv2. OSPFv3 is similar too.

| Type | Packet Name                        | Description                                                |
| ---- | ---------------------------------- | ---------------------------------------------------------- |
| 1    | Hello                              | Discovers neighbours and builds adjacencies between them   |
| 2    | Database Description ([[DBD]])     | Checks for database synchronisation between routers        |
| 3    | Link-State Request ([[LSRs]])      | Requests specific link-state records from router to router |
| 4    | Link-State Update ([[LSUs]])       | Sends specifically requested link-state records            |
| 5    | Link-State Acknowledgement (LSAck) | Acknowledges the other packet types                        |
## A Hello Packet

Shown in the image below is an example of an OSPF hello packet which includes the various fields a hello packet has and the functions it performs:

![[LSPs-20240313160627582.webp#invert]]