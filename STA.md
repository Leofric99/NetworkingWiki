---
tags:
  - Studies
  - Acronym
  - Networking
  - CCNA
  - Theory
aliases:
  - Spanning Tree Algorithm
description: An algorithm for distributed computation of a topology by selecting a single root bridge.
---
[[STP]] is based on an algorithm invented by *Radia Perlman* while working for Digital Equipment Corporation and published in the 1985 paper “An Algorithm for Distributed Computation of a topology by selecting a single root bridge where all other switches determine a single least-cost path".

The algorithm is based around one switch being the ‘[[STP#Electing the Root Bridge|root bridge]]’ in the network. Switches can decide this amongst themselves (using their IDs or MAC addresses). This route bridge acts as the reference point for the entire network as far as STP is concerned.

## Root Path Cost

The Root Path Cost is used to [[STP#Electing Ports|elect the port types]] within the STP topology and is determined by the ==sum of all the individual port costs== along the path from the switch to the root bridge. 

It is the overall cost of the best path from a particular switch to the root bridge that is defined as the ==root path cost==.

The default port costs are ==defined by the speed== at which the port operates. Port costs are configurable, but cannot exceed the physical capabilities of the port.

Port costs can be seen in this table:

| Link Speed | STP Cost: IEEE 802.1D-1998 | RSTP Cost: IEEE 802.1W-2004 |
| ---------- | -------------------------- | --------------------------- |
| 10Gbps     | 2                          | 2,000                       |
| 1Gbps      | 4                          | 20,000                      |
| 100Mbps    | 19                         | 200,000                     |
| 10Mbps     | 100                        | 2,000,000                   |

If two switches are running the same version of STP then they should work together correctly in terms of the Root Path Cost. If they are not, then it will require significant reconfiguration.

*Note that each [[VLANs|VLAN]] has a different spanning tree configuration.*

When a switch has ==multiple equal-cost paths== to the root bridge, the switch will determine a port using the following criteria:

- Lowest sender [[BID]]
- Lowest sender port priority
- Lowest sender port ID