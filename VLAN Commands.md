---
tags:
  - Studies
  - Table
  - Commands
  - Networking
  - CCNA
aliases:
  - VLAN Commands
  - Trunk Commands
  - Trunking Commands
  - DTP Commands
  - Router-on-a-Stick Commands
  - Voice VLAN Commands
cssclasses:
  - commands
---
This concise list of Cisco IOS commands provides the key commands for configuring and managing [[VLANs]] and [[Trunking]], allowing you to efficiently control network segmentation and data flow.

## [[VLANs|VLAN]] Configuration

| Mode     | Command                        | Description                               | Variables `{}` or Options `[]`                           |
| :------- | :----------------------------- | :---------------------------------------- | -------------------------------------------------------- |
| `config` | `vlan {vlan-number}`           | Enters VLAN configuration mode.           | `{vlan-number}` is the desired VLAN number to configure. |
| `config` | `interface vlan {vlan-number}` | Enters VLAN interface configuration mode. | `{vlan-number}` is the desired VLAN number to configure. |
| `config` | `vlan database`                | Enters VLAN database configuration mode.  | N/A                                                      |
| `config` | `no vlan {vlan-id}`            | Deletes a VLAN by its VLAN ID.            | `{vlan-id}` is the desired VLAN number.                  |

## [[Trunking]] Configuration

| Mode        | Command                                    | Description                                           | Variables `{}` or Options `[]`                                                        |
| :---------- | :----------------------------------------- | :---------------------------------------------------- | ------------------------------------------------------------------------------------- |
| `config-if` | `switchport mode access`                   | Sets the interface to access mode.                    | N/A                                                                                   |
| `config-if` | `switchport access vlan {vlan-id}`         | Assigns an access VLAN to an interface.               | `{vlan-id}` is the desired VLAN number.                                               |
| `config-if` | `no switchport access vlan`                | Removes the access VLAN assignment from an interface. | N/A                                                                                   |
| `config-if` | `switchport trunk encapsulation dot1q`     | Sets the encapsulation for trunking.                  | N/A                                                                                   |
| `config-if` | `switchport mode trunk`                    | Configures the Port-Channel interface as a trunk.     | N/A                                                                                   |
| `config-if` | `switchport trunk allowed vlan {vlan-ids}` | Specifies the allowed VLANs on a trunk port.          | `{vlan-id}` is the desired VLAN numbers to allow. values are comma separated (1,2,3). |
| `config-if` | `switchport trunk native vlan {vlan-id}`   | Sets the native VLAN for the trunk interface.         | `{vlan-id}` is the desired VLAN number.                                               |

> [!tip] Best Practice
> It is best practice to force the switchport mode by using the `switchport mode access` command. This also applies to Trunk ports (`switchport mode trunk`).

## [[DTP]] Commands

| Mode        | Command                             | Description                                                                           | Variables `{}` or Options `[]` |
| :---------- | :---------------------------------- | :------------------------------------------------------------------------------------ | ------------------------------ |
| `config-if` | `switchport mode dynamic auto`      | Interface becomes trunk if neighbouring is trunk or dynamic desirable.                | N/A                            |
| `config-if` | `switchport mode dynamic desirable` | Interface becomes trunk if neighbouring is trunk, dynamic auto, or dynamic desirable. | N/A                            |
| `config-if` | `switchport nonegotiate`            | Stops [[DTP]] negotiation on the interface.                                           | N/A                            |

## Voice VLANs

| Mode        | Command                            | Description                                                                            | Variables `{}` or Options `[]`                 |
| :---------- | :--------------------------------- | :------------------------------------------------------------------------------------- | ---------------------------------------------- |
| `config`    | `interface [int-id]`               | Access interface on which the voice VLAN will be assigned.                             | `[int-id]` is the identifier of the interface. |
| `config-if` | `switchport mode access`           | Sets the interface to access mode.                                                     | N/A                                            |
| `config-if` | `switchport access vlan [vlan-id]` | Assigns an access VLAN to an interface.                                                | `[vlan-id]` is the desired VLAN number.        |
| `config-if` | `mls qos trust cos`                | Sets trusted state of an interface and indicates which packet fields classify traffic. | N/A                                            |
| `config-if` | `switchport voice vlan [vlan-id]`  | Assigns a voice VLAN to that port.                                                     | `[vlan-id]` is the desired VLAN number.        |

## Router-on-a-Stick Configuration

| Mode           | Command                                 | Description                                                                                | Variables `{}` or Options `[]`                                                                                              |
| :------------- | :-------------------------------------- | :----------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| `config`       | `interface {if}.{vlan-id}`              | Create the {vlan-id} subinterface on interface Gigabit Ethernet 0/0                        | `{if}` is the desired interface to configure the subinterfaces on. `{vlan-id}` is the VLAN identifier for the subinterface. |
| `config-subif` | `encapsulation dot1q {vlan-id}`         | Configure subinterface to operate on a specified VLAN                                      | `{vlan-id}` is the VLAN identifier for the subinterface.                                                                    |
| `config-subif` | `encapsulation dot1q {vlan-id} native`  | Must be configured on the subinterface belonging to the native VLAN                        | `{vlan-id}` is the VLAN identifier for the native VLAN.                                                                     |
| `config-subif` | `ip address {ip-address} {subnet-mask}` | Assign an IP address to the subinterface                                                   | `{ip-address}` is the IP address. `{subnet-mask}` is the subnet mask.                                                       |
| `config`       | `interface {if}`                        | Access the Gigabit0/0 interface (i.e., the actual physical interface) to enable it         | `{if}` is the interface you configured the subinterface(s) on.                                                              |
| `config-if`    | `no shutdown`                           | Enable the physical interface. This enables all configured subinterfaces on that interface | N/A                                                                                                                         |

## Show Commands

| Command                               | Description                                                                                                             | Variables `{}` or Options `[]`                                 |
| ------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------- |
| `show vlan`                           | Check whether a port belongs to the expected VLAN                                                                       | N/A                                                            |
| `show mac address-table`              | Check which addresses were learned on a particular port of the switch, and to which VLAN that port is assigned          | N/A                                                            |
| `show interfaces [int-id] switchport` | Helpful in verifying an inactive VLAN is assigned to a port                                                             | `[int-id]` Optional interface ID to specify a particular port. |
| `show interfaces trunk`               | - Check native VLAN id matches on both ends of link  - Check whether a trunk link has been established between switches | N/A                                                            |