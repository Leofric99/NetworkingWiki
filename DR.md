---
tags:
  - Studies
  - Acronym
  - Networking
  - CCNA
  - Theory
aliases:
  - Designated Router
description: "\rOptimises OSPF network efficiency by reducing the number of adjacencies needed in multi-access networks."
---
The OSPF Designated Router (DR) optimises [[OSPF]] network efficiency by reducing the number of adjacencies needed in multi-access networks.

## Problems Facing Multi-Access Networks

Multi-access networks can create two challenges for OSPF regarding the flooding of [[LSAs]] as follows:

- Creation of multiple adjacencies Ethernet networks could potentially interconnect many OSPF routers over a common link. Creating adjacencies with every router would lead to an excessive number of [[LSAs]] being exchanged between routers on the same network.
- Extensive flooding of [[LSAs]] Link-state routers flood their LSAs any time OSPF is initialised or when there is a change in the topology. This ==flooding can become excessive==.

![[DR-20240313160220698.webp#invert]]

This is why a DR is normally required for OSPF networks. 

It reduces the amount of packets which would otherwise need to be flooded from every router to every other router.

## The DR's Role

The Designated Router performs the following functions which prevent the potential issues above from becoming insurmountable:

- Generates [[LSAs]] for the network. No LSAs are exchanged between two [[DROTHER|DROTHERs]] Only from or to DROTHERs and from or two the DR.
  
- Minimises flooding of [[OSPF]] routing information by acting as a focal point for updates.
  
- Ensures synchronisation of the Link State Database ([[LSDB]]) among OSPF routers.
  
- Facilitates communication between OSPF areas by summarising routes and reducing traffic.