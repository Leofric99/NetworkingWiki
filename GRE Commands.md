---
tags:
  - Studies
  - Table
  - Networking
  - Commands
cssclasses:
  - commands
---
## Configuration Commands

These commands **must** be done on ==both sides== of the tunnel.

| Mode                      | Command                                          | Description                                                                                            | Variables `{}` or Options `[]`                                                                                                                                                                                       |
| :------------------------ | :----------------------------------------------- | :----------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `config`                  | `interface tunnel {no}`                          | Initialises the tunnel, and enters tunnel config mode.                                                 | `{no}` The desired tunnel number.                                                                                                                                                                                    |
| `config-if`               | `ip address {addr} {netmask}`                    | Sets an IP address on the tunnel interface.                                                            | `{addr}` is the desired tunnel interface address. `{netmask}` is the subnet mask for the desired tunnel interface address.                                                                                           |
| `config-if`               | `tunnel source {if}`                             | Sets the tunnel source interface.                                                                      | `{if}` is the desired interface the tunnel should exit from.                                                                                                                                                         |
| `config-if`               | `tunnel destination {addr}`                      | Sets the tunnel destination address (and activates the tunnel).                                        | `{addr}` is the IP address that the GRE tunnel should arrive at.                                                                                                                                                     |
| `config-if`               | `tunnel mode gre ip`                             | Configures the tunnel to convey IP packets over GRE.                                                   | N/A                                                                                                                                                                                                                  |
| `config-if`               | `no shutdown`                                    | Enables the tunnel if not already enabled.                                                             | N/A                                                                                                                                                                                                                  |
| `config-if` (or `config`) | `ip route {dest-addr} {dest-netmask} {next-hop}` | Configures a static route to a remote network via the GRE tunnel. Can be repeated for multiple routes. | `{dest-addr}` is the desired destination network for traffic via the GRE tunnel. `{dest-netmask}` is the subnet mask for the destination network. `{next-hop}` is the IP address of the other end of the GRE tunnel. |

## Show Commands

| Command                         | Description                                    | Variables `{}` or Options `[]`       |
| :------------------------------ | :--------------------------------------------- | :----------------------------------- |
| `show running-config`           | Shows the running configuration of the device. | N/A                                  |
| `show ip interface tunnel {no}` | Shows information about a tunnel interface.    | `{no}` is the desired tunnel number. |
