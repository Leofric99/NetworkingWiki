---
tags:
  - Studies
  - Acronym
  - Networking
  - CCNA
  - Theory
aliases:
  - Shortest Path First
description: AKA the ‘Dijkstra’ algorithm. Calculates the shortest path to each OSPF node.
---
The Shortest Path First (SPF) algorithm, AKA the 'Dijkstra' algorithm, creates an SPF tree by placing each router at the root of the tree and calculating the shortest path to each node. 

![[SPF-20240313124503337.webp#invert|100]]

The SPF tree is then used to calculate the best routes. OSPF then places the best routes into the forwarding database which is used in turn to create the Routing Table.

