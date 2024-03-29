---
tags:
  - Studies
  - Table
  - Networking
  - Commands
  - CyberSecurity
  - CCNA
cssclasses:
  - commands
---
Cisco IOS ARP commands manage and view the [[ARP|Address Resolution Protocol]] cache, enabling routers to translate IP addresses to MAC addresses on local networks.

## Configuration Commands

| Mode     | Command                                   | Description                                         | Variables `{}` or Options `[]`                                                                                                                                |
| :------- | :---------------------------------------- | :-------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `exec`   | `clear arp [{ip_addr} / all]`             | Clears ARP cache on the device.                     | `{ip_addr}` Defines the IP address of the device who's ARP data needs clearing. `all` Use this to clear all ARP data.                                         |
| `config` | `ip arp inspection vlan {vlan}`           | Enables ARP inspection on specific [[VLANs]].       | `{vlan}` The VLAN name or number.                                                                                                                             |
| `config` | `ip arp inspection validate {validation}` | Specifies the validation method for ARP inspection. | `{validation}` Set validation methods. Can be any of the following: `src-mac / dst-mac / ip / src-mac dst-mac / src-mac ip / dst-mac ip / src-mac dst-mac ip` |
#### [[DAI]] Commands

DHCP snooping is enabled because DAI requires the DHCP snooping binding table to operate.

| Mode        | Command                                               | Description                                                                                                                             | Variables `{}` or Options `[]`                                                                                                                                                                                                                                                                                                           |
| :---------- | :---------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `config`    | `ip dhcp snooping`                                    | Enables [[DHCP Attacks#DHCP Attack Mitigation\|DHCP Snooping]] on the Device.                                                           | N/A                                                                                                                                                                                                                                                                                                                                      |
| `config`    | `ip dhcp snooping vlan {vlans}`                       | Enables DHCP Snooping on select VLAN(s).                                                                                                | `{vlans}` are the VLAN(s) that you want to include in DHCP snooping.                                                                                                                                                                                                                                                                     |
| `config`    | `ip arp inspection vlan {vlans}`                      | Enables ARP Inspection on select VLAN(s).                                                                                               | `{vlans}` are the VLAN(s) that you want to include in [[DAI]].                                                                                                                                                                                                                                                                           |
| `config-if` | `ip dhcp snooping trust`                              | Sets particular interface(s) as DHCP Snooping Trusted Ports.                                                                            | N/A                                                                                                                                                                                                                                                                                                                                      |
| `config-if` | `ip arp inspection trust`                             | Sets particular interface(s) as a [[DAI]] trusted port.                                                                                 | N/A                                                                                                                                                                                                                                                                                                                                      |
| `config`    | `ip arp inspection validate [ip] [src-mac] [dst-mac]` | Configures DAI to check for both destination or source MAC and IP addresses. All three options can be used at the same time if desired. | `[ip]` checks the ARP packet body for invalid and unexpected IP addresses including addresses 0.0.0.0, 255.255.255.255, and all IP multicast addresses. `[src-mac]` checks the source MAC address in the Ethernet header against the sender MAC address in the ARP packet body. `dst-mac` as above, but for the destination MAC address. |

## Show Commands



| Command                                | Description                                                                                                   | Variables `{}` or Options `[]`                                                                              |
| :------------------------------------- | :------------------------------------------------------------------------------------------------------------ | :---------------------------------------------------------------------------------------------------------- |
| `show arp`                             | Displays the ARP table, which maps IP addresses to MAC addresses.                                             | N/A                                                                                                         |
| `show ip arp`                          | Displays the ARP table, which maps IP addresses to MAC addresses.                                             | N/A                                                                                                         |
| `show ip arp-cache [dynamic / static]` | Filters the ARP cache to only show certain entries.                                                           | `[dynamic]` Only show dynamically learned ARP entries. `[static]` Only show statically learned ARP entries. |
| `show ip arp-age`                      | Sorts the ARP cache by the elapsed time since entries were last updated, identifying potential stale entries. | N/A                                                                                                         |
| `show ip arp-summary`                  | Provides a concise overview of the ARP cache, summarising the number of entries and type distribution.        | N/A                                                                                                         |

