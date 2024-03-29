---
tags:
  - Studies
  - Table
  - Networking
  - Commands
cssclasses:
  - commands
---
[[RIP]] is a distance-vector routing protocol used to exchange routing information between routers within a small to medium-sized network. It is an alternative to [[OSPF]] and [[EIGRP]].

## Configuration Commands

| Mode            | Command                         | Description                                                                                              | Variables `{}` or Options `[]`                                                  |
| :-------------- | :------------------------------ | :------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------ |
| `config`        | `router rip`                    | Enters RIP config mode.                                                                                  | N/A                                                                             |
| `config-router` | `version 2`                     | Enables RIP version 2. Version 1 may not work with [[NAT Commands]].                                     | N/A                                                                             |
| `config-router` | `network {addr}`                | Tells device which interface to enable RIP on (effectively advertising the networks to the RIP network). | `{addr}` is the IP address of the network without subnet mask or wildcard mask. |
| `config-router` | `default-information originate` | Advertises the default route for the router to other routers in the RIP network.                         | N/A                                                                             |
 
## Show Commands

|Command|Description|Variables `{}` or Options `[]`|
|---|---|---|
|`show ip protocols`|Displays global parameters and the current state of routing protocols configured on the router.|N/A|
|`show ip route`|Displays the routing table, showing routes learned through RIP if RIP is configured and operational.|N/A|
|`show ip rip database`|Displays the contents of the RIP database, listing all routes learned through RIP.|N/A|
|`show ip rip interface`|Displays the RIP configuration on each interface, including enabled network addresses and RIP version.|N/A|
|`show ip rip neighbor`|Displays information about neighboring routers with which RIP updates are exchanged.|N/A|
