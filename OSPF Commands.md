---
tags:
  - Studies
  - CCNA
  - Commands
  - Networking
  - Table
cssclasses:
  - commands
---
## Basic Configuration Commands

| Mode | Command | Description | Variables `{}` or Options `[]` |
|:-----|:---|:---|:---|
| `config`     | `router ospf {process-id}` | Enables OSPF and enters OSPF config mode. | `{process-id}` An identifier for the OSPF operation on the router |
| `config-router`     | `network {network-address}` | Sets the networks for which OSPF is needed and therefore also identifies the interfaces that will participate. Do not enter networks which are not part of the OSPF network like a link to the ISP. | `{network-address}` The network address of any participating networks. |  
## Other Configuration Commands

| Mode | Command | Description | Variables `{}` or Options `[]` |
| :--- | :--- | :--- | :--- |
| `config-router` | `router-id {router-id}` | Sets a router-id within OSPF | `{router-id}` Any IPv4 formatted ID e.g. `1.1.1.1`. |
| `config-router` | `auto-cost reference-bandwidth {desired-bandwidth}` | Sets a desired reference bandwidth for OSPF calculations so that they match the network environment better. | `{desired-bandwidth}` Desired bandwidth in Mbps. |
| `config-router` | `default-information originate [always]` | Inject a default route (0.0.0.0) into OSPF, which can be useful for routing to unknown destinations. | `[always]` Forces the default route to be advertised even if it's not in the routing table. |
| `config-router` | `passive-interface {interface}` | Sets the interface as passive which will prevent OSPF updates, and hello messages from being sent out from that interface. | `{interface}` Sets the desired interface for the command. |
| `config-router` | `passive-interface default` | Set all interfaces to passive mode (no OSPF hellos sent or received) | N/A |
| `config-if` | `no passive-interface` | Removes OSPF passive status from an interface (if passive interfaces are default, this enables OSPF on the interface). | N/A |
| `config` | `ip ospf priority {priority}` | Sets the router priority. The highest priority will become the DR. | `{priority}` Default is `1`. Can be anything between `1` and `255`. |
| `config-if` | `ip ospf hello-interval {seconds}` | Sets the hello interval to a desired duration. | `{seconds}` Default is `10`, but this can be anything. |
| `config-if` | `ip ospf dead-interval {seconds}` | Sets the dead interval to a desired duration. | `{seconds}` Default is `40`, but this can be anything. |
| `config-if` | `ip ospf cost {desired-cost}` | Sets the cost to a manual value. | `{desired-cost}` Desired cost value. |
| `config-router` | `redistribute {source-protocol} [subnets]` | Redistributes routes from another routing protocol (e.g., EIGRP or RIP) into OSPF. | `{source-protocol}` Either RIP, EIGRP, etc. `[subnets]` Allows the redistribution of subnet routes. Without this, only classful networks are redistributed. |
| `config-router` | `area {area-id} authentication message-digest` | Enables OSPF authentication for an area using MD5. | `{area-id}` The ID of the OSPF area. |
| `config-router` | `area {area-id} authentication message-digest key {key-id} md5 {key}` | Configures MD5 authentication for a specific OSPF area. | `{area-id}` The ID of the OSPF area. `{key-id}` The key ID. `{key}` The Key. |
| `config-router` | `area {area id} virtual-link {router-id}` | Creates a virtual link to connect a router to an OSPF area that is not directly connected to the backbone area (Area 0). | `{area-id}` The ID of the OSPF area. `{router-id}` The router ID of the destination router in the desired area. |
| `config-if` | `ip ospf network {net-type}` | Tells OSPF which network type is connected to the interface. | `{net-type}` The type of network connected. Either `broadcast`, `non-broadcast`, `point-to-multipoint`, or `point-to-point`. |
| `config-router` | `area {area id} range {ip-range} [advertise / not-advertise]` | Summarises routes within an OSPF area | `{area-id}` The OSPF area ID. `{ip-range}` The IP address range. `[advertise / not-advertise]` Specifies whether to advertise or suppress the summary route. |
| `config` | `ip ospf flood-reduction` | Enables OSPF [[LSAs\|LSA]] flood reduction, reducing LSA propagation. | N/A |
| `config-router` | `area {area id} stub [no-summary]` | Configures an OSPF area as a stub area. | `{area-id}` The OSPF area ID. `[no-summary]` Prevents Type 3 LSAs (summary LSAs) from being sent into the stub area. |
| `config-router` | `area {area id} nssa [no-redistribution]` | Configures an OSPF area as a Not-So-Stubby Area (NSSA). | `{area-id}` The OSPF area ID. `no-redistribution` Prevents external route redistribution into the NSSA area. |

## Show Commands


| Command | Description | Variables `{}` or Options `[]` |
| :--- | :--- | :--- |
| `show ip ospf` | Displays general OSPF information, including the router ID, process ID, router's state, and the number of LSAs received and sent. | N/A |
| `show ip ospf interface brief` | Provides a summary of OSPF-enabled interfaces, including their OSPF process status, area ID, IP address, and cost. | N/A |
| `show ip ospf neighbor` | Provides a summary of OSPF-enabled interfaces, including their OSPF process status, area ID, IP address, and cost. | N/A |
| `show ip ospf database` | Lists OSPF neighbour relationships, displaying information such as the neighbour's IP address, state, and interface. | N/A |
| `show ip ospf route` | Displays OSPF routing information, including OSPF routes in the routing table, the type of route (intra-area, inter-area, or external), and metrics. | N/A |
| `show ip ospf virtual-links` | Lists OSPF virtual links and their status when used to connect areas through the backbone area (Area 0). | N/A |
| `show ip ospf border-routers` | Displays information about OSPF Autonomous System Boundary Routers (ASBRs) and their connection to OSPF areas. | N/A |
| `show ip ospf statistics` | Provides OSPF statistics, including the number of SPF calculations, LSA floods, and OSPF packets sent and received. | N/A |
| `show ip ospf summary-address` | Lists summary addresses configured in OSPF, including the route's destination, area, and advertised status. | N/A |
| `show ip ospf interface {interface-id}` | Shows detailed information about a specific OSPF-enabled interface, including its state, timers, and cost. | `interface-id` The ID of the desired interface. |
| `show ip ospf border-routers` | Displays information about OSPF ASBRs and how they are connected to OSPF areas. | N/A |
| `show ip ospf virtual-links` | Lists OSPF virtual links and their status when used to connect non-backbone areas to the backbone area (Area 0). | N/A |
| `show ip ospf sham-links` | Displays information about OSPF Sham Links, which are used in MPLS VPN environments to connect OSPF domains. | N/A |
 
