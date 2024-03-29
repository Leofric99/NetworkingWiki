---
tags:
  - Studies
  - Table
  - Networking
  - Commands
cssclasses:
  - commands
---
The basic IPv4 commands for Cisco IOS routers and layer three switches.

## Configuration

| Mode        | Command                                    | Description                                                                 | Variables `{}` or Options `[]`                                                                                                                                                                      |
| :---------- | :----------------------------------------- | :-------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `config`    | `ip route {network} {mask} {next-hop}`     | Configures a static IPv4 route.                                             | `{network}` is the destination network IPv4 address. `{mask}` is the subnet mask for the destination network in dotted decimal format. `{next-hop}` is the next-hop IPv4 address or exit interface. |
| `config`    | `ip route 0.0.0.0 0.0.0.0 {next-hop}`      | Configures a default static route.                                          | `{next-hop}` is the next-hop IPv4 address or exit interface.                                                                                                                                        |
| `config`    | `ip route 0.0.0.0 0.0.0.0 {next-hop} {ad}` | Configures a floating default static route.                                 | `{next-hop}` is the next-hop IPv4 address or exit interface. `{ad}` is the administrative distance.                                                                                                 |
| `config-if` | `ip address {ip} {mask}`                   | Sets the IPv4 address on an interface.                                      | `{ip}` is the desired interface IPv4 address in dotted decimal format. `{mask}` is the subnet mask for the interface in dotted decimal format.                                                      |
| `config-if` | `ip default-gateway`                       | Sets the default gateway address for an interface.                          | N/A                                                                                                                                                                                                 |
| `config-if` | `ip address dhcp`                          | Enables DHCP on the interface to obtain an IPv4 address dynamically.        | N/A                                                                                                                                                                                                 |
| `config-if` | `no switchport`                            | Enables layer three routing capabilities on a multi-layer switch interface. | N/A                                                                                                                                                                                                 |
## Show Commands

| Command                   | Description                                                                              | Variables `{}` or Options `[]` |
| :------------------------ | :--------------------------------------------------------------------------------------- | :----------------------------- |
| `show running-config`     | Shows the running configuration of the device.                                           | N/A                            |
| `show ip route`           | Displays the IPv4 routing table.                                                         | N/A                            |
| `show ip interface brief` | Displays a brief summary of the status and configuration of all IPv4 interfaces.         | N/A                            |
| `show interface`          | Displays detailed information about all interfaces, including IPv4 addresses and status. | N/A                            |
