---
tags:
  - Studies
  - Table
  - Networking
  - Commands
cssclasses:
  - commands
---
[[STP]] is a network protocol that builds a loop-free logical topology for Ethernet networks.

## Manually Setting the Root Bridge

| Mode     | Command                                            | Description                                                                                                                                                                      | Variables `{}` or Options `[]`                            |
| :------- | :------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------- |
| `config` | `spanning-tree vlan {vlan-id} root primary`        | Ensures this switch has the lowest priority value for the [[VLAN Commands\|VLAN]].                                                                                               | `{vlan-id}` ID of the VLAN where the priority is set.     |
| `config` | `spanning-tree vlan {vlan-id} root secondary`      | Use if the configuration of an alternative bridge is desired. Sets the switch priority value to ensure it becomes the root bridge if the primary root bridge fails for the VLAN. | `{vlan-id}` ID of the VLAN for the secondary root bridge. |
| `config` | `spanning-tree vlan {vlan-id} priority {priority}` | Manually configure the bridge's priority value for the VLAN.                                                                                                                     | `{vlan-id}` ID of the VLAN where the priority is set.     |

## Configuring PortFast and [[BPDUs|BPDU]] Guard

| Mode        | Command                           | Description                                                                     | Variables `{}` or Options `[]`                                              |
| ----------- | --------------------------------- | ------------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| `config`    | `interface {int-id}`              | Access the interface.                                                           | `{int-id}`: Identifier of the interface to be accessed.                     |
| `config`    | `interface range {interfaces}`    | Access a range of contiguous interfaces if necessary.                           | `{interfaces}` are the interfaces to configure in this format: `G0/1 - 15`. |
| `config-if` | `switchport mode access`          | As a good practice, hard-type this command so the switchport is in access mode. | N/A                                                                         |
| `config-if` | `spanning-tree portfast`          | Enables PortFast on the access port(s).                                         | N/A                                                                         |
| `config-if` | `spanning-tree bpduguard enable`  | Enables BPDU Guard on the access port(s).                                       | N/A                                                                         |
| `config`    | `spanning-tree portfast default`  | Configures PortFast to be the default for all switch interfaces.                | N/A                                                                         |
| `config`    | `spanning-tree bpduguard default` | Configures BPDU Guard to be the default for all switch interfaces.              | N/A                                                                         |

## Configuring [[Root Guard]] and [[Loop Guard]]

| Mode        | Command                           | Description                                                                                               | Variables `{}` or Options `[]`                          |
| ----------- | --------------------------------- | --------------------------------------------------------------------------------------------------------- | ------------------------------------------------------- |
| `config`    | `interface {int-id}`              | Access the interface.                                                                                     | `{int-id}`: Identifier of the interface to be accessed. |
| `config-if` | `spanning-tree guard root`        | Enables root guard on an interface.                                                                       | N/A                                                     |
| `config-if` | `spanning-tree guard loop`        | Enables loop guard on an interface.                                                                       | N/A                                                     |
| `config`    | `spanning-tree loopguard default` | Enables loop guard (all ports) by default on the device. Note that you cannot enable root guard globally. | N/A                                                     |

## Configuring Rapid PVST+

| Mode        | Command                                                       | Description                                                                                   | Variables `{}` or Options `[]`                                                       |
| ----------- | ------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| `config`    | `spanning-tree mode rapid-pvst`                               | Configure Rapid PVST+ as the STP mode on the switch.                                          | N/A                                                                                  |
| `config-if` | `spanning-tree link-type point-to-point`                      | Specify that a link is point-to-point.                                                        | N/A                                                                                  |
| `exec`      | `clear spanning-tree detected-protocols [interface {int-id}]` | Forces renegotiation with neighbouring switches on all interfaces or the specified interface. | `[interface {int-id}]`: (Optional) Interface ID for which the protocols are cleared. |

## Show Commands

| Command                                 | Description                                            | Variables `{}` or Options `[]`                                              |
| :-------------------------------------- | :----------------------------------------------------- | :-------------------------------------------------------------------------- |
| `show spanning-tree`                    | Shows STP information.                                 | N/A                                                                         |
| `show running-config`                   | Shows the device configuration.                        | N/A                                                                         |
| `show running-config interface {if}`    | Shows the configuration of a particular interface.     | `{if}` is the desired interface.                                            |
| `show spanning-tree`                    | Display STP information.                               | N/A                                                                         |
| `show spanning-tree active`             | Display STP information for active interfaces only.    | N/A                                                                         |
| `show spanning-tree brief`              | Display at-a-glance information for all STP instances. | N/A                                                                         |
| `show spanning-tree detail`             | Display detailed information for all STP instances.    | N/A                                                                         |
| `show spanning-tree interface {int-id}` | Display STP information for the specified interface.   | `{int-id}`: Identifier of the interface for which STP information is shown. |
| `show spanning-tree vlan {vlan-id}`     | Display STP information for the specified VLAN.        | `{vlan-id}`: ID of the VLAN for which STP information is shown.             |
| `show spanning-tree summary`            | Display a summary of STP port states.                  | N/A                                                                         |
