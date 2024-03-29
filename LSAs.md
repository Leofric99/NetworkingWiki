---
tags:
  - Studies
  - Acronym
  - Networking
  - CCNA
  - Theory
aliases:
  - Link-State Advertisements
---
LSAs are Link-state Advertisements used in link-state routing protocols. They contain information about a network. They are the data contained within [[LSUs]].

## OSPF's Use of LSAs

In the [[OSPF]] protocol, whenever a new network is added to the OSPF area, LSAs are 'flooded' throughout the network area until all routers have a copy.

The LSAs are then stored by each router in their [[LSDB|LSDBs]]. This forms the basis for the router's topology table.

Each router will then use the SPF algorithm to calculate the best route to the new network. Each LSA has an aging timer which will expire after 30 minutes. LSAs for that network will be flooded again after this expires.