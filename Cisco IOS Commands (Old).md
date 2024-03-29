---
tags:
  - Studies
  - Commands
  - Networking
---

## Show Commands

#### Basic Show Commands

- `show running-config` - Displays the current configuration. (No variables)
- `show running-config | section {section-name}` - Filters the running configuration to display only the section specified. (Variable: {section-name})
- `show running-config interface` - Displays the running configuration of a specific interface. (Variable: {interface})
- `show interfaces` - Displays information about interfaces. (No variables)
- `show startup-config` - Displays the contents of the startup configuration file. (No variables)
- `show version` - Displays information about the system hardware and software. (No variables)
- `show version | include IOS` - Displays information about the installed IOS version. (No variables)
- `show users` - Displays information about currently logged-in users. (No variables)
- `show history` - Displays the command history.
- `show interfaces description` - Displays a brief description of interfaces. (No variables)
- `show controllers` - Displays information about hardware controllers on the device. (No variables)
- `show environment` - Displays environmental information such as temperature and voltage. (No variables)
- `show tech-support` - Generates a detailed technical support report for troubleshooting purposes. (No variables)
- `show log` - Displays system log messages. (No variables)
- `show controllers Ethernet-controller {int-id} phy` - Displays physical layer (PHY) information for a specific Ethernet interface. (Variable: {int-id})
- `show controllers Ethernet-controller {fa0/1} | include MDIX` - Shows information related to MDIX negotiation on a specific FastEthernet interface. (Variable: {fa0/1})
- `show flash` - Displays information about the flash memory, which often stores the IOS image and configuration files.
- `show mac-address-table` or `show mac address-table` - Displays the MAC address table, which maps MAC addresses to switch ports.
- `show crypto isakmp sa` - Displays information about active Internet Security Association and Key Management Protocol (ISAKMP) security associations. (No variables)
- `show crypto ipsec sa` - Displays information about active IPsec security associations. (No variables)

#### Security Show Commands

- `show port-security interface {int-id}` - Displays information about port security on a specific interface.
- `show port-security address` - Shows the MAC addresses that are configured for port security.
- `show interface {int-id} status` - Displays the status of a specific interface.
- `show mac address-table dynamic` - Displays the dynamically learned MAC addresses in the MAC address table.
- `show crypto key mypubkey rsa` - Displays the RSA public key for the device. (No variables)

#### IP Show Commands

- `show ip interface brief` - Displays a brief summary of the status and configuration of all interfaces.
- `show ipv6 interface brief` - Displays a brief summary of the status and configuration of all IPv6 interfaces.
- `show ip interface brief | include up` - Displays a summary of interfaces with the "up" status.
- `show ip interface brief | exclude unassigned` - Shows a summary of interfaces excluding those with "unassigned" status.
- `show ipv6 interface brief` - Displays a brief summary of IPv6 interfaces on the router.
- `show ip route` - Displays the routing table. (No variables)
- `show ip route | begin {Gateway}` - Displays the routing table starting from a specific gateway IP address. (Variable: {Gateway})
- `show ipv6 route` - Displays the IPv6 routing table.
- `show ip interface` - Displays detailed information about all interfaces.
- `show interface status` - Displays the status and protocol of all interfaces. (No variables)
- `show ipv6 interface` - Displays detailed information about all IPv6 interfaces.
- `show ip ssh` - Shows the SSH (Secure Shell) configuration status on a router.

#### VLAN Show Commands

- `show vlan brief` - Displays a brief summary of configured VLANs.
- `show vlan id` - Displays detailed information about a specific VLAN. (Variable: {VLAN ID})
- `show interface vlan {vlan-id}` - Shows information about a specific VLAN interface.
- `show interfaces {if-id} switchport` - Displays switchport information for a specific interface.
#### ARP Show Commands

- `show arp` - Displays the ARP (Address Resolution Protocol) table, which maps IP addresses to MAC addresses.
- `show ip arp` - Displays the ARP (Address Resolution Protocol) table, which maps IP addresses to MAC addresses.

#### DHCP Show Commands

- `show ip dhcp server statistics` - Displays DHCP server statistics. (No variables)
- `show ip dhcp binding` - Displays DHCP (Dynamic Host Configuration Protocol) address bindings. (No variables)
- `show ipv6 dhcp interface {g0/0/1}` - Shows information about the DHCPv6 configuration on a specific interface. (Variable: {g0/0/1})
- `show ipv6 dhcp pool` - Displays information about IPv6 DHCP pools.
- `show ipv6 dhcp binding` - Shows a list of DHCPv6 address bindings.
- `show ip dhcp snooping` - Displays information about DHCP snooping.

#### STP Show Commands

- `show spanning-tree` - Displays information about the Spanning Tree Protocol (STP) status on interfaces.

#### NAT Show Commands

- `show ip nat translations` - Displays the Network Address Translation (NAT) translation table. (No variables)

#### CDP Show Commands

- `show cdp neighbors` - Displays information about directly connected Cisco devices discovered via Cisco Discovery Protocol (CDP). (No variables)
- `show cdp` - Verify CDP status
- `show cdp neighbors detail` - detailed CDP information

#### PAgP and LACP (Etherchannel) Show Commands

- `show interfaces port-channel X` - Display information about the Etherchannel bundle with the specified channel group number (X).
- `show etherchannel summary` - View a summary of all configured Etherchannels and their status.
- `show lacp neighbor` - Display information about LACP neighbours and their status.
- `show etherchannel load-balance` - View the load-balancing algorithm configured for Etherchannels.
- `show etherchannel port-channel` - Display information about all configured port-channel interfaces.
- `show lldp neighbors` - Discover device neighbours using LLDP
- `show lldp neighbors detail` - Detailed neighbour information

#### ACL Show Commands

- `show ip access-list` - Shows the IPv4 access control lists and their entries.
- `show ipv6 access-list` - Displays the IPv6 access control lists and their entries.
- `show access-list {acl-name}` - Provides detailed information about a specific ACL, including the sequence numbers and entries.
- `show access-list {acl-name} statistics` - Shows statistics related to matches and hits for ACL entries.
- `show access-lists | include {keyword}` - Filters ACL display output to include only entries containing the specified keyword.
- `show access-lists | exclude {keyword}` - Filters ACL display output to exclude entries containing the specified keyword.

#### OSPF Show Commands

- `show ip ospf` - Displays general OSPF information, including the router ID, process ID, router's state, and the number of LSAs received and sent.
- `show ip ospf interface brief` - Provides a summary of OSPF-enabled interfaces, including their OSPF process status, area ID, IP address, and cost.
- `show ip ospf neighbor` - Lists OSPF neighbor relationships, displaying information such as the neighbor's IP address, state, and interface.
- `show ip ospf database` - Shows the contents of the OSPF link-state database, including information about LSAs, their types, and sequence numbers.
- `show ip ospf route` - Displays OSPF routing information, including OSPF routes in the routing table, the type of route (intra-area, inter-area, or external), and metrics.
- `show ip ospf virtual-links` - Lists OSPF virtual links and their status when used to connect areas through the backbone area (Area 0).
- `show ip ospf border-routers` - Displays information about OSPF Autonomous System Boundary Routers (ASBRs) and their connection to OSPF areas.
- `show ip ospf statistics` - Provides OSPF statistics, including the number of SPF calculations, LSA floods, and OSPF packets sent and received.
- `show ip ospf summary-address` - Lists summary addresses configured in OSPF, including the route's destination, area, and advertised status.
- `show ip ospf interface {interface-id}` - Shows detailed information about a specific OSPF-enabled interface, including its state, timers, and cost.
- `show ip ospf border-routers` - Displays information about OSPF ASBRs and how they are connected to OSPF areas.
- `show ip ospf virtual-links` - Lists OSPF virtual links and their status when used to connect non-backbone areas to the backbone area (Area 0).
- `show ip ospf sham-links` - Displays information about OSPF Sham Links, which are used in MPLS VPN environments to connect OSPF domains.

## Basic Configuration / To Sort

- `hostname` - Sets the hostname for the device. (Variable: {name})
- `interface` - Enters interface configuration mode. (Variable: {interface})
- `interface range {f0/1 - 2}` - Specifies a range of interfaces for configuration.
- `interface loopback0` - Enters the loopback interface configuration mode, which is used for creating virtual loopback interfaces.
- `no shutdown` - Enables an interface. (No variables)
- `exit` - Exits the interface configuration mode. (Note: Loopback interfaces are enabled as soon as an IP or IPv6 address is applied.)
- `ping` - Sends ICMP echo requests to a destination IP address. (Variable: {IP address})
- `enable` - Enters privileged EXEC mode. (Variable: {password})
- `configure terminal` - Enters global configuration mode. (No variables)
- `copy running-config startup-config` - Saves the running configuration to the startup configuration. (No variables)
- `clock set` - Sets the system clock. (Variables: hh:mm:ss {month} {day} {year})
- `clock timezone` - Configures the time zone for the device. (Variables: {zone-name} {offset-hours})
- `banner motd` - Configures a message of the day banner. (Variable: {message})
- `banner login` - Configures a login banner message. (Variable: {message})
- `traceroute` - Traces the route to a destination by sending UDP packets with increasing TTL values. (Variable: {IP address})
- `duplex` - Configures the duplex mode for a switch port as half, full, or auto. (Variable: {half/full/auto})
- `speed` - Sets the speed for a switch port as 10, 100, or auto. (Variable: {10/100/auto})
- `mdix auto` - Enables automatic MDIX (Media Dependent Interface Crossover) negotiation on an Ethernet interface.
- `no ip domain-lookup` - Disables the DNS hostname-to-IP address lookup feature, preventing the device from attempting DNS resolution for unrecognized commands. (No variables)
- `crypto key generate rsa general-keys` - Initiates the generation of an RSA key pair for various cryptographic purposes, such as SSH (Secure Shell) or SSL/TLS encryption. (Variables: {modulus size})
- `disable` - Exits privileged EXEC mode. (No variables)
- `line console 0` - Enters console line configuration mode. (No variables)
- `line vty 0 15` - Enters VTY (Virtual Terminal Line) configuration mode. (No variables)
- `reload` - Reloads the device, optionally saving the configuration first. (No variables)
## Network Administration Commands

- `logging` - Configures logging parameters. (Variables: {host} {facility} {severity level})
- `delete flash:vlan.dat` - Deletes the VLAN database file stored in flash memory.
- `clear counters` - Clears interface counters. (No variables)
- `boot system` - Specifies the storage device and the path to the IOS file that the router or switch should boot from. (Variables: {storage device}:/{path to file}/{filename})
- `logging sync` - Enables synchronous logging for the console line. (No variables)
- `erase startup-config` - Erases the startup configuration. (No variables)
- `debug` - Enables debugging for various protocols and processes. (Variables: {protocol/process})
- `copy running-config tftp` - Copies the running configuration to a TFTP server. (Variables: {TFTP server IP} {destination file name})
- `logging trap` - Sets the severity level for syslog messages to be sent to a logging server. (Variable: {severity level})
- `terminal history size` - Sets the number of lines in the command history buffer.
- `write memory` - Saves the running configuration to the startup configuration file. (No variables)

#### Configuring SSH

-  `ip domain-name {FQDN}` - Sets the domain name for SSH access.
- `crypto key generate rsa general-keys modulus {modulus-value}` - Generates a crypto key for the SSH encryption using a given modulus value. Usually `1024` or `2048`.
- `username {username} secret {password}` - Create a local user account if you haven't already.
- `line vty {vty-lines}` - Sets which VTY lines to configure.
- `transport input ssh` - Sets SSH as the access method.
- `ip ssh version 2` - Sets SSH version 2 for improved security.
- `login local` - Tells it to use the local user account(s) as the login method.

## Security Commands

- `service password-encryption` - Encrypts passwords stored in the device's configuration. (No variables)
- `enable secret` - Sets an encrypted password for privileged EXEC mode. (Variable: {password})
- `login local` - When in either VTY line config mode, or Console config mode, this sets the login credentials needed for access to the lines/console to the local user account(s) which can be created using the command below.
- `username {username} secret {password}` - Create a local user account.
- `switchport port-security` - Enables port security on a switch port.
- `switchport port-security mac-address` - Sets a specific MAC address for port security.
- `switchport port-security mac-address sticky` - Configures port security to dynamically learn and allow MAC addresses.
- `switchport port-security aging (static | time {time} | type (absolute | inactivity))` - Sets aging parameters for dynamically learned MAC addresses.
- `switchport port-security violation (protect/restrict/shutdown)` - Configures the violation action for port security.
- `switchport port-security maximum {no of connections}` - Sets the maximum number of allowed MAC addresses on a port.
- `mac-address {aaaa.bbbb.cccc}` - Specifies a MAC address for port security.

#### Configuring Role Based CLI Access

**Creating a View**

- `aaa new-model` - Enable AAA before setting up role based views. Run in global configuration mode.
- `enable view` - Enters a the root view. Run in privileged exec mode
- `parser view {view-name}` - Creates a new view in the root view. View name is arbitrary. Run in global configuration mode.
- `secret {password}` - Set a password on the view.
- `commands {parser-mode} {include | include-exclusive | exclude} all | interface {interface-name} | {command}` - Add or remove commands, interfaces, etc permissions to the view you've just created. Parser-mode is what mode the commands are entered in eg. `exec`.

**Creating a Superview**

- `aaa new-model` - Enable AAA before setting up role based views.
- `enable view` - Enters a the root view.
- `parser view {view-name} superview` - Creates a new superview in the root view. View name is arbitrary.
- `secret {password}` - Set a password on the view.
- `view {view-name}` - Adds views (and their associated permissions) to a superview.

#### Configuring SSH

-  `ip domain-name {FQDN}` - Sets the domain name for SSH access.
- `crypto key generate rsa general-keys modulus {modulus-value}` - Generates a crypto key for the SSH encryption using a given modulus value. Usually `1024` or `2048`.
- `username {username} secret {password}` - Create a local user account if you haven't already.
- `line vty {vty-lines}` - Sets which VTY lines to configure.
- `transport input ssh` - Sets SSH as the access method.
- `ip ssh version 2` - Sets SSH version 2 for improved security.
- `login local` - Tells it to use the local user account(s) as the login method.

## IP and Static Route Commands

- `ip address {address} {subnet mask}` - Assigns an IP address and subnet mask to an interface. (Variables: {address} {subnet mask})
- `ip default-gateway {ip-address}` - Sets the default gateway for the device.
- `ip default-gateway {ip-address}` - Sets the default gateway for the device.
- `ip route {dest-network} {dest-subnet-mask} {next-hop-ip}` - Configures static IP routes.
- `ip route 0.0.0.0 0.0.0.0 {next-hop-ip}` - Configures a default static IP route.
- `ip route {dest-network} {dest-subnet-mask} {next-hop-ip} {administrative-dist}` - Configures a floating static route. The administrative distance is an arbitrary number which represents a priority (lower is better). This way, backup static routes can be created.
- `ip route 0.0.0.0 0.0.0.0 {next-hop-ip} {administrative-dist}` - Configures a floating default static IP route (see above).
- `clear ip route` - Clears specific IP routes from the routing table. (Variables: {destination network} {subnet mask})
- `ipv6 unicast-routing` - Enables IPv6 unicast routing on a router.
- `ipv6 route {ipv6-prefix/prefix-length} (ipv6 address/exit if) (admin-dist)` - Configures a static IPv6 route. (Variables: {ipv6-prefix/prefix-length} {ipv6 address/exit if (without prefix-length)} {admin-dist})
- `ipv6 route ::/0 (ipv6 address/exit interface) (admin-dist)` - Configures a static IPv6 default route. (Variables: {ipv6 address/exit interface} {admin-dist})
- `ipv6 route {209.165.200.238} {255.255.255.255} (next hop address/exit interface)` - Configures a static host route for IPv4. (Variables: {209.165.200.238} {255.255.255.255} {next hop address/exit interface})
- `ipv6 route {2001:db8:acad:2::99/128} (exit interface/ipv6 address/exit interface ipv6 address)` - Configures a static host route for IPv6. (Variables: {2001:db8:acad:2::99/128} {exit interface/ipv6 address/exit interface ipv6 address})
- `ipv6 address {IPv6-address}/{slash-notation-net-length}` - sets the IPv6 address on an interface.
- `ipv6 address {IPv6-link-local-address} link-local` - Sets the IPv6 link local address on an interface.
- `ipv6 enable` - Enables IPv6 on an interface.
- `ipv6 address autoconfig` - Configures an interface to obtain its IPv6 address using Stateless Address Autoconfiguration (SLAAC).
- `ipv6 nd managed-config-flag` - Enables the Managed Address Configuration flag in IPv6 Neighbour Discovery (ND) for stateful DHCPv6.

## SSH Commands

- `ip domain-name {FQDN}` - Sets the domain name for SSH access.
- `crypto key generate rsa general-keys modulus {modulus-value}` - Generates a crypto key for the SSH encryption using a given modulus value. Usually `1024` or `2048`.
- `username {username} secret {password}` - Create a local user account if you haven't already.
- `line vty {vty-lines}` - Sets which VTY lines to configure.
- `transport input ssh` - Sets SSH as the access method.
- `ip ssh version 2` - Sets SSH version 2 for improved security.
- `login local` - Tells it to use the local user account(s) as the login method.

## ARP Commands

- `clear arp` - Clears the ARP cache on the device.
- `ip arp inspection vlan {vlan, vlan}` - Enables ARP inspection on specific VLANs.
- `ip arp inspection validate src-mac | dst-mac | ip | src-mac dst-mac | src-mac ip | dst-mac ip | src-mac dst-mac ip` - Specifies the validation method for ARP inspection.

## VLAN Commands

- `vlan {vlan-number}` - Enters VLAN configuration mode.
- `interface vlan {vlan-number}` - Enters VLAN interface configuration mode.
- `vlan database` - Enters VLAN database configuration mode. (No variables)
- `dot1q` - Configures a sub-interface for 802.1Q VLAN tagging. (Variable: {VLAN ID})
- `switchport mode access` - Sets the interface to access mode.
- `switchport access vlan {vlan-id}` - Assigns an access VLAN to an interface. (Variable: {vlan-id})
- `no switchport access vlan` - Removes the access VLAN assignment from an interface.
- `no vlan {vlan-id}` - Deletes a VLAN by its VLAN ID. (Variable: {vlan-id})
- `switchport trunk encapsulation dot1q` - Sets the encapsulation for trunking.
- `switchport mode trunk` - Configures the Port-Channel interface as a trunk port.
- `switchport trunk allowed vlan {1,2,20}` - Specifies the allowed VLANs on a trunk port. (Variable: {1,2,20})
- `switchport trunk native vlan {x}`

## Discovery Commands

- `clear cdp table` - Clears the CDP table. (No variables)
- `clear ip dhcp binding` - Clears DHCP address bindings. (Variables: {IP address})
- `no cdp run` - Disables the Cisco Discovery Protocol (CDP) on the switch.
- `no cdp enable` - Disables CDP on a specific interface.
- `no lldp run` - Disables the Link Layer Discovery Protocol (LLDP) on the switch.
- `no lldp transmit` - Disables LLDP transmission on a specific interface.
- `no lldp receive` - Disables LLDP reception on a specific interface.

## DHCP Commands

- `ip dhcp pool` - Configures a DHCP address pool. (Variable: {pool name})
- `ip dhcp excluded-address` - Excludes specific IP addresses from DHCP allocation within a pool. (Variables: {start IP} {end IP})
- `clear ip dhcp server statistics` - Clears DHCP server statistics. (No variables)
- `ipv6 dhcp relay destination {ipv6 address} {exit-interface-type-number}` - Configures the IPv6 DHCP relay agent to forward DHCPv6 requests to a DHCP server. (Variables: {ipv6 address} {exit-interface-type-number})
- `network {network} {mask}` - Specifies the network and subnet mask for the DHCP pool. (Variables: {network} {mask})
- `default-router {address}` - Sets the default gateway for DHCP clients. (Variable: {address})
- `lease {days/hrs/mins}` or `infinite` - Defines the lease duration for DHCP addresses. (Variables: {days/hrs/mins} or infinite)
- `netbios-name-server {address} {address}` - Configures NetBIOS name servers for DHCP clients. (Variables: {address} {address})
- `show ip dhcp binding` - Displays a list of DHCP address bindings.
- `show ip dhcp server statistics` - Shows DHCP server statistics.
- `interface {type/number}` - Specifies the interface on which to enable DHCP server or client functionality. (Variable: {type/number})
- `ip address dhcp` - Configures an interface to obtain its IP address dynamically from a DHCP server.
- `ipv6 dhcp pool {name}` - Creates an IPv6 DHCP pool with the specified name. (Variable: {name})
- `address prefix {address/64} lifetime {valid-lifetime/infinite} preferred {preferred-lifetime/infinite}` - Configures IPv6 address assignment parameters within a DHCPv6 pool. (Variables: {address/64} {valid-lifetime/infinite} {preferred-lifetime/infinite})
- `dns-server {address}` - Sets the DNS server for DHCPv6 clients. (Variable: {address})
- `domain-name {name}` - Specifies the domain name for DHCPv6 clients. (Variable: {name})
- `ip dhcp snooping` - Enables DHCP snooping on the switch.
- `ip dhcp snooping limit rate {packets per second}` - Sets the rate limit for DHCP snooping.
- `ip dhcp snooping vlan {vlan, vlan}` - Enables DHCP snooping on specific VLANs.

## EtherChannel Commands

- `channel-group X mode active` - Configure a physical interface to be part of an EtherChannel bundle using LACP. Replace X with the desired channel group number.
- `channel-group X mode passive` - Configure a physical interface to be part of an EtherChannel bundle using LACP in passive mode.
- `no channel-group X mode active/passive` - Remove an interface from an EtherChannel bundle.
- `interface Port-ChannelX` - Enter the configuration mode for the logical Port-Channel interface.
- `description` - Add a description to the Port-Channel interface for documentation purposes.

## HSRP Commands

- `standby {group-number} priority {priority-value}` - Sets the priority value for an HSRP or VRRP group. (Variables: {group-number} {priority-value})
- `standby {group-number} preempt` - Configures HSRP or VRRP to pre-empt and take over as the active router when its priority becomes higher.

## STP Commands

- `spanning-tree portfast` - Configures PortFast on a switch port.
- `spanning-tree bpduguard enable` - Enables BPDU Guard on a PortFast-enabled port.

## ACL Configuration

- `access-list` - Creates an access control list. (Variables: {number} {permit/deny} {source/destination})
- `show access-lists` - Displays the configured access control lists (ACLs) and their respective entries, including permit and deny statements.
- `ip access-list extended {acl-name}` - Enters extended ACL configuration mode for IPv4 ACLs, allowing you to configure more complex ACLs with source and destination address filtering, port numbers, and more.
- `ipv6 access-list {acl-name}` - Enters extended ACL configuration mode for IPv6 ACLs, similar to the IPv4 extended ACL configuration mode.
- `deny {protocol} {source} {source-wildcard} {destination} {destination-wildcard} [established]` - Configures an entry in an extended ACL to deny traffic based on various criteria such as source and destination IP addresses, protocol, and optional "established" keyword for established connections.
- `permit {protocol} {source} {source-wildcard} {destination} {destination-wildcard} [established]` - Configures an entry in an extended ACL to permit traffic based on various criteria, similar to the "deny" command.
- `remark {comment}` - Adds a comment or remark to an ACL entry for documentation purposes.
- `ip access-list standard {acl-name}` - Enters standard ACL configuration mode for IPv4 ACLs, typically used for simpler filtering based on source IP addresses.
- `ip access-group` - Applies an access control list (ACL) to an interface for filtering traffic. (Variables: {ACL name} {in/out})
- `ipv6 access-list {acl-name}` - Enters standard ACL configuration mode for IPv6 ACLs, similar to the IPv4 standard ACL configuration mode.
- `permit {source} [log]` - Configures a standard ACL entry to permit traffic from a specific source IP address or subnet, with an optional "log" keyword to log matched packets.
- `deny {source} [log]` - Configures a standard ACL entry to deny traffic from a specific source IP address or subnet, with an optional "log" keyword to log matched packets.
- `access-list {acl-number} permit/deny {protocol} {source} {source-wildcard} {destination} {destination-wildcard} [established]` - Configures an ACL entry by specifying an ACL number and protocol, along with source and destination criteria.
- `access-class {acl-number} in | out` - Applies an ACL to filter incoming or outgoing Telnet or SSH sessions on a VTY line (virtual terminal line) of a router or switch. For example:
- `access-class {acl-number} in | out (vty-line-number)` - Applies an ACL to filter incoming or outgoing Telnet or SSH sessions on a specific VTY line. You specify the line number along with the ACL number. For example:
- `access-class {acl-number} in (interface-type) {interface-number}` - Applies an ACL to filter incoming traffic on a specific interface. This command is typically used on a router's physical interface to control incoming traffic based on the ACL. For example:
- `access-class {acl-number} out (interface-type) {interface-number}` - Applies an ACL to filter outgoing traffic on a specific interface. This command is used to control outgoing traffic based on the ACL. For example:
- `access-class {acl-number} in | out (interface-type) {interface-number} (ip)` - Applies an ACL to filter incoming or outgoing IP traffic on a specific interface. This command is used to apply an ACL to an interface to filter IP traffic.

## NAT Commands

- `clear ip nat translations` - Clears the NAT translation table. (No variables)

#### Configuring Static NAT (Single Public IP to Single Private IP):

- `ip nat inside` - Specifies that the interface is an inside (private) interface for NAT (run on any internal interface(s) conf mode).
- `ip nat outside` - Specifies that the interface is an outside (public) interface for NAT (run in external interface conf mode).
- `ip nat inside source static {inside-local-address} {inside-global-address}` - sets the static mapping (where inside-local-address is the private IP address, and inside-global-address is the public IP address available to use).

#### Configuring PAT (Single Public IP Port Address Translation):

- `ip nat inside` - Specifies that the interface is an inside (private) interface for NAT (run on any internal interface(s) conf mode).
- `ip nat outside` - Specifies that the interface is an outside (public) interface for NAT (run in external interface conf mode).
- `access-list {acl-number} permit {private-network-ip} {private-network-wildcard} {destination-network-ip} {destination-network-wildcard}` - Defines an access list to specify which traffic should be translated by NAT. Can use `any` instead of destination network & wildcard.
- `ip nat inside source list {access-list} interface {external-interface} overload` - Configures NAT overload (PAT) using an access list and an interface to translate multiple internal IPs to a single external IP ({access-list} is an arbitrary number for the access list number you will use in step d. {interface} is the outside interface.) Any outbound interface can be used (it will still go the right way).

#### Configuring Dynamic NAT (Pool of Public Addresses):

- `ip nat inside` - Specifies that the interface is an inside (private) interface for NAT (run on any internal interface(s) conf mode).
- `ip nat outside` - Specifies that the interface is an outside (public) interface for NAT (run in external interface conf mode).
- `ip nat pool {pool-name} {start-ip} {end-ip} netmask {subnet-mask}` - Defines a pool of public IP addresses that can be used for dynamic NAT or PAT.
- `access-list {acl-number} permit ip {private-network-ip} {private-network-wildcard} {destination-network-ip} {destination-network-wildcard}` - Defines an access list to specify which traffic should be translated by NAT. Can use ‘any’ instead of destination network & wildcard.
- `ip nat inside source list {access-list} pool {pool-name} overload` - Configures NAT overload (PAT) using an access list and a pool of public IP addresses. You would then need to create static routes for the pool addresses.
- `ip nat inside source static tcp {local-ip} {local-port} {global-ip} {global-port}` - Configures a static NAT translation for a specific TCP port.
- `ip nat inside source static udp {local-ip} {local-port} {global-ip} {global-port}` - Configures a static NAT translation for a specific UDP port.

1. `show ip nat translations` - Displays the active NAT translations on the router.
2. `clear ip nat translation ` - Clears all NAT translations.
3. `nat64 enable` - This command enables NAT64 translation on the router.
4. `nat64 prefix stateful` - Configures NAT64 to use stateful translation, which means the router maintains a translation table for IPv6-to-IPv4 and IPv4-to-IPv6 address mappings.
5. `nat64 v6v4 static` - Defines static NAT64 translations for specific IPv6 and IPv4 addresses.
6. `nat64 prefix translation {ipv6-prefix} {ipv4-prefix}` - Configures the IPv6-to-IPv4 prefix translation, allowing IPv6 clients to access IPv4 resources.
7. `ipv6 access-list` - You might use IPv6 access lists to control which IPv6 traffic gets translated by NAT64.
8. `show nat64 translations` - Displays the NAT64 translation table, showing the mappings between IPv6 and IPv4 addresses.
9. `ntp server x.x.x.x` - Sets the clock server for the network
10. `show ntp associations` - Verify NTP conf.
11. `show ntp status` - More NTP verification, displays stratum information (how far the device is away from the time source.

## RIP Commands

- `router rip` - Enter router RIP config mode
- `version 2` - version 1 may not work with NAT
- `network {network address without subnet mask or wildcard mask}` - Repeat this for any directly connected networks (including LANs).

## EIGRP Commands:

- `router eigrp` `{as number}` - Enter EIGRP config mode. AS Number is an identifier for EIGRP domains (Must be the same value for any EIGRP router in the WAN network topology).
- `network {network address} {wildcard mask}` - Repeat this for any directly connected networks (including LANs).
- `eigrp router-id {router id}` - The router ID can be anything in IP address form eg. 1.1.1.1 or 2.2.2.2 or 1.0.0.0 or 1.0.0.1.

## OSPF Commands

#### Basic OSPF Setup

- `router ospf {process-id}` - This is OSPF config mode. The Process ID is simply an identifier for the OSPF operation on the router.
- `network {network-address} {network-wildcard-mask} area {area-id}` - Sets the networks for which OSPF is needed and therefore also identifies the interfaces that will participate. Do not enter networks which are not part of the OSPF network like a link to the ISP. Must be run inside the OSPF config mode.

#### Other OSPF Commands

- `router-id {router-id}` - The router ID can be anything in IP address form eg. 1.1.1.1 or 2.2.2.2 or 1.0.0.0 or 1.0.0.1. Must be run inside the OSPF config mode.
- `auto-cost reference-bandwidth {desired-bandwidth}` - Must be run in OSPF config mode. Sets a desired reference bandwidth for OSPF calculations in order for calculations to be a better match for network environment. Bandwidth is in Mbps.
- `default-information originate [always]` - Must be used in OSPF config mode. Inject a default route (0.0.0.0) into OSPF, which can be useful for routing to unknown destinations. The optional `always` keyword forces the default route to be advertised even if it's not in the routing table.
- `passive-interface {interface}` - Sets the interface as passive which will prevent OSPF updates, and hello messages from being set out from that interface. Must be run inside the OSPF config mode.
- `passive-interface default` - Set all interfaces to passive mode (no OSPF hellos sent or received), and then selectively enable OSPF on specific interfaces using the `no passive-interface` command.
- `ip ospf priority {priority}` - Must be run in interface config mode. Sets the router priority. The default is 1, but can be set anywhere from 1-255. The highest priority in the area will become DR.
- `ip ospf hello-interval {seconds}` - Must be set in interface config mode. Sets the hello interval to a desired duration. The default is 10 seconds.
- `ip ospf dead-interval {seconds}` - Must be set in interface config mode. Sets the dead interval to a desired duration. The default is 40 seconds.
- `ip ospf cost {desired-cost-value}` - Must be set in interface config mode. Sets the cost to a manual value eg. 10, or 100.
- `redistribute {source-protocol} {subnets}` - Redistribute routes from another routing protocol (e.g., EIGRP or RIP) into OSPF.
- `area {area id} authentication message-digest` - Enable OSPF authentication using MD5 authentication for a specific OSPF area.
- `area {area id} authentication message-digest key {key-id} md5 {key}` - Configure MD5 authentication for a specific OSPF area, specifying the authentication key and key ID.
- `area {area id} virtual-link {router-id}` - Create a virtual link to connect a router to an OSPF area that is not directly connected to the backbone area (Area 0).
- `ip ospf network point-to-point` - Configure an interface as a point-to-point OSPF network type.
- `ip ospf hello-interval {seconds}` - Set the frequency (in seconds) at which OSPF hello packets are sent on an interface.
- `ip ospf dead-interval {seconds}` - Configure the dead interval (in seconds) for OSPF hello packets on an interface.
- `ip ospf priority {value}` - Set the priority value for the router in the DR (Designated Router) election process.
- `ip ospf cost {value}` - Manually set the OSPF cost for an interface, influencing the route preference.
- `area {area id} range {ip-range} [advertise | not-advertise]` - Summarize routes within an OSPF area, specifying whether to advertise or suppress the summary route.
- `ip ospf flood-reduction` - Enable OSPF LSA (Link-State Advertisement) flood reduction, reducing LSA propagation.
- `area {area id} stub [no-summary]` - Configure an OSPF area as a stub area. The `no-summary` option prevents Type 3 LSAs (summary LSAs) from being sent into the stub area.
- `area {area id} nssa [no-redistribution]` - Configure an OSPF area as a Not-So-Stubby Area (NSSA). The `no-redistribution` option prevents external route redistribution into the NSSA area.
