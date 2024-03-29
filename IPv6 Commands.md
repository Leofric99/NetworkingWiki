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
Remember to enable [[IPv6]] on any device which requires it with the `ipv6 unicast-routing` command.
## Configuration Commands

| Mode        | Command                                     | Description                                                                                          | Variables `{}` or Options `[]`                                                                                                                                                                                                 |
| :---------- | :------------------------------------------ | :--------------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `config`    | `ipv6 unicast-routing`                      | Enable IPv6 unicast routing on the device.                                                           | N/A                                                                                                                                                                                                                            |
| `config`    | `ipv6 route {ipv6} {ipv6/int} {admin-dist}` | Configures a static IPv6 route.                                                                      | `{ipv6}` is the destination network/device IPv6 address, and it's prefix length. `{ipv6/int}` is the next-hop IPv6 address (without prefix length) or the local exit interface. `{admin-dist}` is the administrative distance. |
| `config`    | `ipv6 route ::/0 {ipv6/int} {admin-dist}`   | Configures a static IPv6 default route.                                                              | `{ipv6/int}` is the next-hop IPv6 address (without prefix length) or the local exit interface. `{admin-dist}` is the administrative distance.                                                                                  |
| `config-if` | `ipv6 address {ipv6} [anycast]`             | Sets the IPv6 address on an interface.                                                               | `{ipv6}` is the desired interface IPv6 address, and it's prefix length. `[anycast]` is optional. Only do that if you want the interface to be a part of an [[IPv6 Anycast Addresses\|anycast address group]].                  |
| `config-if` | `ipv6 address {ipv6} link-local`            | Sets the link-local IPv6 address on the interface.                                                   | `{ipv6}` is the desired IPv6 link local address.                                                                                                                                                                               |
| `config-if` | `ipv6 enable`                               | Enables IPv6 on an interface.                                                                        | N/A                                                                                                                                                                                                                            |
| `config-if` | `ipv6 address autoconfig`                   | Configures interface to obtain IPv6 address via [[SLAAC]].                                           | N/A                                                                                                                                                                                                                            |
| `config`    | `ipv6 nd managed-config-flag`               | Enables the Managed Address Configuration flag in IPv6 Neighbour Discovery (ND) for stateful DHCPv6. | N/A                                                                                                                                                                                                                            |

## Show Commands

| Command                     | Description                                                                      | Variables `{}` or Options `[]` |
| :-------------------------- | :------------------------------------------------------------------------------- | :----------------------------- |
| `show ipv6 interface brief` | Displays a brief summary of the status and configuration of all IPv6 interfaces. | N/A                            |
| `show ipv6 route`           | Displays the IPv6 routing table.                                                 | N/A                            |
| `show ipv6 interface`       | Displays detailed information about all IPv6 interfaces.                         | N/A                            |
| `show interface status`     | Displays the status and protocol of all interfaces.                              | N/A                            |