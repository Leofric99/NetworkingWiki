---
tags:
  - Studies
  - Acronym
  - Networking
  - CCNA
  - Theory
aliases:
  - Router ID
description: A number assigned to OSPF routers to identify it, and to influence the DR and BDR elections.
---
A Router ID (RID) is the highest logical (loopback) IP address configured on a router, if no logical/loopback IP address is set then the Router uses the highest IP address configured on its active interfaces.

The RID can influence [[OSPF Elections]] if the [[OSPF]] interface priority on all routers in an OSPF area is equal and/or left as default. It can be manually set using the `router-id` command specified in [[OSPF Commands]].