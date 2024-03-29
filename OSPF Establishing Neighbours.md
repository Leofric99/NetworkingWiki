---
tags:
  - "#Studies"
  - Networking
  - CCNA
  - Theory
aliases:
  - OSPF Establishing Neighbour Adjacencies
description:
---
To determine if there is an OSPF neighbour on the link, the router sends a hello packet that contains it’s router ID out of all OSPF enabled interfaces. The hello packet is sent to the reserved ‘all OSPF routers IPv4 multicast address’ of 224.0.0.5. Only OSPFv2 routers will process these packets.

The OSPF router ID is used by the OSPF process to uniquely identify each router in the OSPF area. A router ID is a 32-bit number formated like the IPv4 address of the the router.

When a neighbouring OSPF enabled router receives a hello packet with a router ID that is not within it’s neighbour list, the receiving router attempts to establish an adjacency with the initiating router.

The process for establishing router adjacency on a multi-access network is as follows. This table follows the [[OSPF Port States]]:

| Order | State              | Description                                                                                                                                                                                                                                                                                                                                                                             |
| ----- | ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1     | Down to Init State | When OSPFv2 is enabled on the interface, R1 transitions from down to inits state and starts sending OSPFv2 hellos out of the interface in an attempt to discover neighbours                                                                                                                                                                                                             |
| 2     | Init State         | When R2 receives a hello from the previously unknown router R1, it adds R1’s router ID to the neighbour list and responds with a hello packet containing it’s own Router ID.                                                                                                                                                                                                            |
| 3     | Two-way State      | R1 receives R2’s hello and notices that the message contains the R1 router ID in the list of R2’s neighbours, R1 adds R2’s router ID to the neighbour list and transitions to the two-way state.<br><br>If R1 and R2 are connected with a point-to-point link they transition to ExStart.<br><br>If R1 and R2 are connected with a common Ethernet network, the DR/BDR election occurs. |
| 4     | Elect the DR & BDR | The DR and BDR election occurs, where the router with the highest router ID or highest priority is elected as the DR, and second highest is the BDR.                                                                                                                                                                                                                                    |
