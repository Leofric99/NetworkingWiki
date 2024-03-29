---
tags:
  - Studies
  - Table
  - Networking
  - Commands
  - Template
cssclasses:
  - commands
aliases:
  - PAgP Commands
  - LACP Commands
  - Port Aggregation Protocol Commands
  - Link Aggregation Control Protocol Commands
---
Port Aggregation commands configure and manage the bundling of physical ports, enabling redundancy and load balancing.

Forming [[EtherChannel|EtherChannels]] is a form of Port Aggregation. There are two protocols which can be used to form EtherChannels. These are [[PAgP]] and [[LACP]].

## Configuration Commands

| Mode        | Command                           | Description                                                                                                                      | Variables `{}` or Options `[]`                                                                                                                                                                                                                             |
| :---------- | :-------------------------------- | :------------------------------------------------------------------------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `config`    | `interface range {int-range}`     | Enters interface config mode for a range of interfaces.                                                                          | `{int-range}` is a range of interfaces e.g. `F0/1 - 24`.                                                                                                                                                                                                   |
| `config-if` | `channel-group {num} mode {mode}` | Sets the mode for the virtual EtherChannel. The mode will determine if an EtherChannel will form, and what protocol it will use. | `{num}` is the desired channel-group number. This *must* match for ports intended for the link on the same switch, but can be different on the switch at the other end. `{mode}` is the desired [[EtherChannel Commands#LACP and Cisco PAgP Modes\|mode]]. |
| `config`    | `interface port-channel {num}`    | Enters interface config mode for the entire EtherChannel link you just created as if it were a single link.                      | `{num}` is the port-channel number you configured in the previous command.                                                                                                                                                                                 |
| `config-if` | `description {desc}`              | Sets a description on the EtherChannel.                                                                                          | `{desc}` is the desired description.                                                                                                                                                                                                                       |

> [!note]
> this configuration done, you *might* also want to configure it as a [[Trunking|trunk]] using the latter part of the [[VLAN Commands]] configuration.

## Layer Three EtherChannel Configuration

See [[EtherChannel#Layer Three EtherChannels]] for an explanation.

| Mode        | Command                           | Description                                                                                                                      | Variables `{}` or Options `[]`                                                                                                                                                                                                                             |
| :---------- | :-------------------------------- | :------------------------------------------------------------------------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `config`    | `interface range {int-range}`     | Enters interface config mode for a range of interfaces.                                                                          | `{int-range}` is a range of interfaces e.g. `F0/1 - 24`.                                                                                                                                                                                                   |
| `config`    | `no switchport`                   | Enables routing on the layer three switch.                                                                                       | N/A                                                                                                                                                                                                                                                        |
| `config-if` | `channel-group {num} mode {mode}` | Sets the mode for the virtual EtherChannel. The mode will determine if an EtherChannel will form, and what protocol it will use. | `{num}` is the desired channel-group number. This *must* match for ports intended for the link on the same switch, but can be different on the switch at the other end. `{mode}` is the desired [[EtherChannel Commands#LACP and Cisco PAgP Modes\|mode]]. |
| `config`    | `interface port-channel {num}`    | Enters interface config mode for the entire EtherChannel link you just created as if it were a single link.                      | `{num}` is the port-channel number you configured in the previous command.                                                                                                                                                                                 |
| `config-if` | `ip address {addr} {subnet}`      | Sets an IP address for the entire aggregated port channel.                                                                       | `{addr}` is the desired IP address. `{subnet}` is the desired subnet mask.                                                                                                                                                                                 |

## Show Commands

| Command                              | Description                                                                              | Variables `{}` or Options `[]`                            |
| :----------------------------------- | :--------------------------------------------------------------------------------------- | :-------------------------------------------------------- |
| `show etherchannel load-balance`     | Shows the configuration of the load balancing configured for [[LAg]].                    | N/A                                                       |
| `show interfaces port-channel {num}` | Shows information about the EtherChannel bundle with the specified channel group number. | `{num}` the port-channel number you want to see info for. |
| `show etherchannel summary`          | Shows a summary of all configured EtherChannels and their status.                        | N/A                                                       |
| `show lacp neighbor`                 | Displays information about LACP neighbours and their status.                             | N/A                                                       |
| `show etherchannel port-channel`     | Shows information about all configured port-channel interfaces.                          | N/A                                                       |
| `show lldp neighbors`                | Discover device neighbours using LLDP.                                                   | N/A                                                       |
| `show lldp neighbors detail`         | As above, but more detailed.                                                             | N/A                                                       |

## [[LACP]] and Cisco [[PAgP]] Modes

Both ends of an EtherChannel must be configured correctly for an [[EtherChannel]] to form. Firstly, they must be set correctly for the desired protocol as per the table below.

Secondly they must be configured to the correct mode(s) on both ends for an EtherChannel to be formed as per the section below the table.

| LACP      | Cisco PAgP  |
| --------- | ----------- |
| `passive` | `auto`      |
| `active`  | `desirable` |
| `on`      | `on`        |

No EtherChannel Formation: `auto` & `auto` or `passive` & `passive`.
EtherChannel Formation: `desireable` & `auto` or `active` & `passive`.
EtherChannel Formation: `desirable` & `desirable` or `active` & `active`.