---
tags:
  - "#Studies"
  - Networking
  - CCNA
  - Theory
description: The first process which OSPF routers go through to become established on the network.
---
Establishing adjacencies is the first process which [[OSPF]] enabled router interfaces will go through to become established in the OSPF area.

OSPF has three states. Down, Init, and Two-way. The table below details what each of these three states mean. These port states are used in the [[OSPF Establishing Neighbours|OSPF Establishing Neighbour Adjacencies]] process.

| State          | Description                                                                                                                                                                                                                                                     |
| -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Down State     | No hello packets received results in the Down State. As soon as the router(s) begin sending hello packets again, the state transitions to the Init State.                                                                                                       |
| Init State     | Hello packets are received from the neighbouring routers. These packets contain the Router ID of the sending router. This will cause the router(s) to transition to a two-way state.                                                                            |
| Two-way State  | In this state, communication between the two routers is bidirectional. On multi-access links, the routers will now elect a ==DR and BDR== and transition to the ExStart state as detailed in [[OSPF Establishing Neighbours\|the neighbour adjacency process]]. |
| ExStart State  | On point-to-point networks, the two routers decide which router will initialte the DBD packet exchange and decide upon the initial DBD packet sequence number.                                                                                                  |
| Exchange State | Routers exchange DBD packets. If additional router information is required then the routers will transition to the loading state, otherwise they will transition to the full state.                                                                             |
| Loading State  | LSRs and LSUs are used to gain additional route information. Routes are processed using the SPF algorithm. The routers will then transition to the Full state.                                                                                                  |
| Full State     | The Link-state database of the router is fully synchronised.                                                                                                                                                                                                    |
