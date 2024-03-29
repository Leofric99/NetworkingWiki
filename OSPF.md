---
tags:
  - "#Studies"
  - Networking
  - CCNA
  - Theory
  - COM515
aliases:
  - Open Shortest Path First
description: A dynamic routing protocol that efficiently exchanges routing information in IP networks.
---
Open Shortest Path First (OSPF) is a ==link-state routing protocol== that was developed as an alternative for [[RIP]] or [[EIGRP]]. It has significant advantages over RIP in that it offers ==faster convergence== and ==scales== to much larger network implementations.

OSPF uses the concept of ==areas==. A network administrator can divide the routing domain into distinct areas that help control routing update traffic.

> [!info]- QRH
> Click [[QRH-OSPF.pdf|here]] for the quick reference handbook.

## How it Works

There are several steps that OSPF will go through as it establishes itself on the network.

---

1. Hello [[LSPs]] are sent and received between neighbouring routers through all interfaces which have OSPF enabled. 
---
2. Routers, will then go through the [[OSPF Establishing Neighbours|OSPF Establishing Neighbour Adjacencies]] process to establish their neighbours on OSPF enabled interfaces. [[OSPF Establishing Neighbours|This]] page actually includes step three here. Once neighbours have been established, each router makes a note of these neighbours in it's [[OSPF#Databases|adjacency (neighbour) table]].
---
3. Routers will then [[OSPF Elections|elect the DR & BDR]].
---
4. The OSPF routers will then synchronise their [[LSDB|LSDBs]] through a process which involves flooding [[LSAs]] throughout the network (not just from and to the [[DR]]).
---
5. Once [[LSAs]] have been flooded, and an OSPF area's [[LSDB|LSDBs]] are up to date, the [[SPF]] algorithm will be run on each router in the area to determine the [[OSPF#Databases|forwarding table]], and therefore, the routing table for each router.
---
6. At this point, the router is ==fully established== as an OSPF router and can efficiently route traffic within the OSPF domain. The routers continues to exchange [[LSPs|OSPF Hello Packets]] with its neighbours to maintain adjacencies and monitor network health.

## Multi-Area OSPF

To make OSPF more ==efficient and scalable==, OSPF supports hierarchical routing using areas. An OSPF area is a group of routers that share the ==same link-state information== in their [[LSDB|LSDBs]]. OSPF can be implemented in one of the following ways:

- **Single-area OSPF.** All routers are in one predetermined area. Best practice is to use 0 unless there are plans to introduce more OSPF areas.
- **Multi-area OSPF.** OSPF is implemented using multiple areas, in a hierarchical fashion. All areas must connect to the backbone area (area 0). Routers interconnecting the areas are referred to as [[ABRs]], but there is little about these on this course.

Advantages of using multi-area OSPF include the following:

| Benefit                               | Description                                                                                                                                                                                |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Smaller routing tables                | Routing tables are smaller due to fewer entries. This is achieved by summarising network addresses between areas (summarisation is not enabled by default).                                |
| Reduced link-state update overhead    | Dividing the network into smaller areas minimises processing and memory requirements for link-state updates.                                                                               |
| Reduced frequency of SPF calculations | Topology changes within an area have a localised impact. [[LSAs\|LSA]] flooding stops at the area boundary, reducing the need to recalculate the [[SPF]] algorithm for the entire network. |

The diagram below shows a network topology with three OSPF areas. R1 and R2 are controlling Multi-area OSPF, whereas the other routers are only dealing with single areas. 

![[OSPF-20240313163110263.webp#invert]]

There is a ‘backbone’ area known as Area 0 by best practice. If there were more OSPF areas here, more routers (or more router interfaces on an enterprise router) would need to be added to area 0 and connected to R1 and R2.



## Databases

There are three different databases kept by routers using OSPF. They are as follows.

| Database Name       | Table Name      | Description                                                                                                                                                                                                                                                 |
| :------------------ | :-------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Adjacency Database  | Neighbour Table | A list of all neighbour routers to which a router has established bi-directional communication. This table is unique for each router, and can be viewed using the `show ip ospf neighbor` command.                                                          |
| [[LSDB]]            | Topology Table  | A list of information about all other routers in the network. This database represents the network LSDB. All routers within an area defined by the Network Admin have identical LSDBs, and can be viewed using the `show ip ospf database` command.         |
| Forwarding Database | Routing Table   | List of routes generated when an algorithm is run on the link-state database. Each router's routing table is unique and contains information on how and where to send packets to other routers. This table can be viewed using the `show ip route` command. |
