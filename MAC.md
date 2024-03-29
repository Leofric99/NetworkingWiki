---
tags:
  - Studies
  - Acronym
  - Networking
  - CCNA
  - Theory
  - COM412
aliases:
  - MAC Addresses
  - MAC Address
description: A unique hardware address assigned to a network interface controller for identification within a network.
---

MAC (*AKA: Burned-In Address or BIA*) stands for ==Media Access Control==, and is a layer two protocol which handles addressing of devices. Each device with networking capabilities will be ==assigned a MAC address by the manufacturer==.

- Each MAC Address is unique.
- 6 Bytes (or 48 bits) in length.
- The first 3 bytes are known as the OUI (*Organisationally Unique Identifier*).
- The last 3 bytes are unique to the device.
- Written as ==12 Hexadecimal characters==.

The broadcast MAC address in a network is always `FF:FF:FF:FF:FF:FF`.

## Unknown Unicast Frames

When a switch receives a MAC address of an unknown device, it is known as an Unknown Unicast Frame. The switch will follow the following procedure:

- Frame is ==flooded== out of all interfaces (except the entry interface).
- Once the device responds, the ==switch will learn the MAC address==, and add it to it's MAC address table which will include the interface the device is associated with.
- This frame is now known as a Known Unicast Frame.
- The MAC address table is regularly cleared, so if the device doesn't send any frames before the time runs out, the MAC address will be removed from the table.

## Configuration

The following Cisco IOS commands are associated with MAC Addresses.

- `show mac-address-table` or `show mac address-table` - Displays the MAC address table, which maps MAC addresses to switch ports
- `show mac address-table dynamic` - Displays the dynamically learned MAC addresses in the MAC address table.
- `show port-security address` - Shows the MAC addresses that are configured for port security.
- `switchport port-security mac-address` - Sets a specific MAC address for port security.
- `switchport port-security mac-address sticky` - Configures port security to dynamically learn and allow MAC addresses.
- `switchport port-security aging (static | time {time} | type (absolute | inactivity))` - Sets aging parameters for dynamically learned MAC addresses.
- `switchport port-security maximum {no of connections}` - Sets the maximum number of allowed MAC addresses on a port.
- `mac-address {aaaa.bbbb.cccc}` - Specifies a MAC address for port security.
- `show arp` - Displays the ARP (Address Resolution Protocol) table, which maps IP addresses to MAC addresses.
- `show ip arp` - Displays the ARP (Address Resolution Protocol) table, which maps IP addresses to MAC addresses.
- `ip arp inspection validate src-mac | dst-mac | ip | src-mac dst-mac | src-mac ip | dst-mac ip | src-mac dst-mac ip` - Specifies the validation method for ARP inspection.