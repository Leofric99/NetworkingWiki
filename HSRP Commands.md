---
tags:
  - Studies
  - Table
  - Networking
  - Commands
  - CCNA
cssclasses:
  - commands
---
[[HSRP]] commands configure routers to share a single virtual IP address for high availability.

## Configuration Commands

| Mode        | Command                                            | Description                                                                                                                         | Variables `{}` or Options `[]`                                                                                                                                                            |
| :---------- | :------------------------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `config-if` | `standby version {ver}`                            | Enables HSRP on a router interface.                                                                                                 | `{ver}` The desired version of HSRP.                                                                                                                                                      |
| `config-if` | `standby {group-number} ip {ip}`                   | Sets the IP address for the HSRP virtual router for an HSRP group. This must be set to the same value for all routers in the group. | `{group-number}` is the desired HSRP group the router is to be a part of. `{ip}` is the desired virtual IP address for the virtual router.                                                |
| `config-if` | `standby {group-number} priority {priority-value}` | Sets the priority value for an HSRP or [[VRRP]] group.                                                                              | `{group-number}` is the desired HSRP group the router is to be a part of. `{priority-value}` is the desired HSRP priority for the router (default 100 and higher values are prioritised). |
| `config-if` | `standby {group-number} preempt`                   | Configures HSRP or VRRP to pre-empt and take over as the active router when its priority becomes higher.                            | `{group-number}` is the desired HSRP group the router is to be a part of.                                                                                                                 |
| `config-if` | `standby {group-number} timers {hello} {hold}`     | Configures the standby and hold timers for the HSRP of VRRP group.                                                                  | `{group-number}` is the desired HSRP group the router is to be a part of. `{hello}` is the desired hello timer in seconds. `{hold}` is the desired hold timer in seconds.                 |

## Show Commands

| Command                | Description                                         | Variables `{}` or Options `[]`  |
| :--------------------- | :-------------------------------------------------- | :------------------------------ |
| `show running-config`  | Shows the router running configuration.             | N/A                             |
| `show standby [brief]` | Shows details about the active and standby routers. | `[brief]` condenses the output. |
