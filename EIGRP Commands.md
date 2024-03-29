---
tags:
  - Studies
  - Table
  - Networking
  - Commands
cssclasses:
  - commands
---
[[EIGRP]] is a Cisco proprietary advanced distance-vector routing protocol designed for efficient and scalable routing within enterprise networks. It is an alternative to [[OSPF]] and [[RIP]].

| Mode            | Command                 | Description                                                                                                                                 | Variables `{}` or Options `[]`                                                                 |
| :-------------- | :---------------------- | :------------------------------------------------------------------------------------------------------------------------------------------ | :--------------------------------------------------------------------------------------------- |
| `config`        | `router eigrp`          | Enters EIGRP config mode.                                                                                                                   | N/A                                                                                            |
| `config-router` | `network {addr} {wild}` | Tells EIGRP which interface to participate in the routing protocol (effectively advertises these networks to the routing protocol network). | `{addr}` is the network address to add. `{wild}` is the wildcard mask for the network address. |
| `config-router` | `eigrp router-id {id}`  | Sets a router ID for the router.                                                                                                            | `{id}` is the desired router ID (e.g. `1.1.1.1`).                                              |

## Show Commands

|Command|Description|Variables `{}` or Options `[]`|
|---|---|---|
|`show ip protocols`|Displays global parameters and the current state of routing protocols configured on the router, including EIGRP.|N/A|
|`show ip route`|Displays the routing table, showing routes learned through EIGRP if EIGRP is configured and operational.|N/A|
|`show ip eigrp neighbors`|Displays information about neighboring routers with which EIGRP updates are exchanged.|N/A|
|`show ip eigrp interfaces`|Displays the status of EIGRP on all interfaces, including their IP addresses, enabled networks, and metrics.|N/A|
|`show ip eigrp topology`|Displays the current EIGRP topology table, listing all known routes, their successors, feasible successors, and metrics.|N/A|
|`show ip eigrp topology all-links`|Displays the current EIGRP topology table, including all possible successor routes, even if they are not currently used.|N/A|
|`show ip eigrp topology {network}`|Displays detailed EIGRP topology information for a specific network or prefix.|`{network}`: Network address or prefix for which topology information is desired|
|`show ip eigrp interfaces {interface}`|Displays detailed information about the status of EIGRP on a specific interface, including its IP address and enabled networks.|`{interface}`: Interface name for which EIGRP information is desired|