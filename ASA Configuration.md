---
tags:
  - Studies
  - CyberSecurity
  - Theory
aliases:
  - Adaptive Security Appliance Commands
description: An explanation of how to implement the ASA Commands.
---
This note guides you through the configuration of an [[ASAs|ASA]] [[Firewalls|Firewall]]. For a pure command list instead, see [[ASA Commands]].

## CLI Differences

[[ASAs]] have their own CLI which is similar to that of Cisco IOS and can, for the most part, be treated as such.

However, the ASA CLI also has different commands. The table contrasts common IOS router and ASA commands.

| IOS Router Command                       | Equivalent ASA Command       |
| ---------------------------------------- | ---------------------------- |
| `enable secret {password}`               | `enable password {password}` |
| `line vty 0 4 password {password} login` | `passwd {password}`          |
| `ip route`                               | `route interface_name`       |
| `show ip interface brief`                | `show interface ip brief`    |
| `show ip route`                          | `show route`                 |
| `show ip nat translations`               | `show xlate`                 |
| `copy running-config startup-config`     | `write [memory]`             |
| `erase startup-config`                   | `write erase`                |
## Initial Setup

Some [[ASAs]] will ship with a basic configuration which is suitable for [[SOHO]] environments so it's important to remove that configuration to begin with using the `configure factory-default` command.

---

The ASA provides an interactive setup ==initialisation wizard== to simplify the initial configuration of the device if desired. The wizard guides the administrator to configure basic settings using interactive prompts.

The wizard is displayed ==when there is no start-up configuration==, or if the start-up configuration is erased and the ASA is rebooted using the `write erase` and `reload` privileged EXEC commands.

###### Initialisation Wizard Example %% fold %%

```
Pre-configure Firewall now through interactive prompts [yes]? <Enter>   
Firewall Mode [Routed]: <Enter>   
Enable password [<use current password>]: cisco   
Allow password recovery [yes]? <Enter>   
Clock (UTC):   
  Year [2021]:    
  Month [Feb]:    
  Day [9]:    
  Time [11:21:11]:    
Management IP address: 192.168.1.1   
Management network mask: 255.255.255.0   
Host name: NETSEC-ASA   
Domain name: netsec.com   
IP address of host running Device Manager: 192.168.1.100   
   
The following configuration will be used:   
Enable password: cisco   
Allow password recovery: yes   
Clock (UTC): 11:21:11 Feb 9 2021   
Firewall Mode: Routed   
Management IP address: 192.168.1.1   
Management network mask: 255.255.255.0   
Host name: NETSEC-ASA   
Domain name: netsec.com   
IP address of host running Device Manager: 192.168.1.100   
   
Use this configuration and save to flash? [yes]<Enter>
```

## Basic Settings

An [[ASAs|ASA]] must be configured with basic management settings. The table displays the commands to accomplish this task.

| ASA Command                                                  | Description                                                                                                                                                                                       |
| ------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `hostname {name}`                                            | Specifies a hostname up to 63 characters.<br><br>A hostname must start and end with a letter or digit, and have as interior characters only letters, digits, or a hyphen.                         |
| `domain-name {name}`                                         | Sets the default domain name.                                                                                                                                                                     |
| `enable password {password}`                                 | Sets the enable password for privileged EXEC mode.<br><br>Sets the password as a case-sensitive string of 3 to 32 alphanumeric and special characters (not including a question mark or a space). |
| `banner motd {message}`                                      | Provides legal notification and configures the system to display a message-of-the-day banner when connecting to the ASA.                                                                          |
| `key config-key password-encryption {new-pass} [{old-pass}]` | Sets the passphrase between 8 and 128 characters long.<br><br>Used to generate the encryption key.                                                                                                |
| `password encryption aes`                                    | Enables password encryption and encrypts all user passwords.                                                                                                                                      |
## Interface Configuration

The IP address of an interface on an [[ASAs|ASA]] can be configured using one of the following options:

- Manually - Commonly used to assign an IP address and mask to the interface.
- [[DHCP]] - Used when an interface is connecting to an upstream device providing DHCP services. The interface can be a DHCP client and discover its IP address and DHCP-related information from the upstream device.
- [[PPPoE]] - Used when an interface is connecting to an upstream [[DSL]] device providing point-to-point connectivity over Ethernet services. The interface can be a PPPoE client and discover its IP address from an upstream PPPoE DSL device.

The table lists the commands to configure an IP address on an interface.

| ASA Command                     | Description                                                                                |
| ------------------------------- | ------------------------------------------------------------------------------------------ |
| `ip address {ip-add} {netmask}` | Assigns an IP address to the interface.                                                    |
| `ip address dhcp`               | The interface will request an IP address configuration from the upstream device.           |
| `ip address dhcp setroute`      | Used to have the interface request and install a default route to the upstream device.     |
| `ip address pppoe`              | Interface configuration mode command that requests an IP address from the upstream device. |
| `ip address pppoe setroute`     | Same command but it also requests and installs a default route to the upstream device.     |
Each interface must have a [[ASAs#Security Levels|security level]]. Refer to [[ASA Implementation]] for details about where to place the ASA within the network.

The table below details the security level commands for the interfaces.

| ASA Command              | Description                                                                                                                                                                                                                                                                                          |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `nameif {if_name}`       | Names the interface using a text string of up to 48 characters.<br><br>The name is not case-sensitive.<br><br>You can change the name by re-entering this command with a new value.<br><br>Do not enter the no form, because that command causes all commands that refer to that name to be deleted. |
| `security-level {value}` | Sets the security level, where number is an integer between 0 (lowest) and 100 (highest).                                                                                                                                                                                                            |
| `no shutdown`            | Activate the interface.                                                                                                                                                                                                                                                                              |
## Remote Access Configuration

Telnet or SSH is required to manage the [[ASAs|ASA]] remotely, using the CLI. To enable the Telnet service, use the commands listed in the table.

**Telnet:**

| ASA Command                                             | Description                                                                                                                                               |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `[passwd / password] {password}`                        | Sets the login password up to 80 characters in length for Telnet.                                                                                         |
| `telnet [{ipv4_add} {mask} / {ipv6_add&pre}] {if_name}` | Identifies which inside host or network can Telnet to the ASA interface.<br><br>Use the `clear configure telnet` command to remove the Telnet connection. |
| `telnet timeout {minutes}`                              | By default, Telnet sessions left idle for five minutes are closed by the ASA. The command alters the default exec timeout of five minutes.                |
| `aaa authentication telnet console LOCAL`               | Configures Telnet to refer to the local database for authentication.<br><br>The LOCAL keyword is case sensitive and is a predefined server tag.           |
| `clear configure telnet`                                | Removes the Telnet connection from the configuration.                                                                                                     |
**SSH:**

| ASA Command                                                         | Description                                                                                                                                                                                                                                                                                                     |
| ------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `username {name} password {password}`                               | Creates a local database entry.                                                                                                                                                                                                                                                                                 |
| `aaa authentication ssh console LOCAL`                              | Configures SSH to refer to the local database for authentication.<br><br>The `LOCAL` keyword is case sensitive and is a predefined server tag.                                                                                                                                                                  |
| `crypto key generate rsa modulus {modulus-size}`                    | Generates the RSA key required for SSH encryption.<br><br>The `modulus_size` (in bits) can be 512, 768, 1024, 2048, 3072, or 4096.<br><br>A value of at least 2048 is recommended.                                                                                                                              |
| `ssh [{ip_address} {mask} / {ipv6_address} {prefix-len}] {if-name}` | Identifies which inside host or network can SSH to the ASA interface.<br><br>Multiple commands can be in the configuration.<br><br>If the `if-name` is not specified, SSH is enabled on all interfaces except the outside interface.<br><br>Use the `clear configure ssh` command to remove the SSH connection. |
| `ssh version {number}`                                              | Optional. By default, the ASA allows both SSH Version 1 (less secure) and Version 2 (more secure).<br><br>Enter this command in order to restrict the connections to a specific version.                                                                                                                        |
| `ssh timeout {minutes}`                                             | Alters the default exec timeout of five minutes.                                                                                                                                                                                                                                                                |
| `clear configure ssh`                                               | Removes the SSH connection from the configuration.                                                                                                                                                                                                                                                              |
## NTP Services Configuration

Network Time Protocol (NTP) services can be enabled on an [[ASAs|ASA]] to obtain the date and time from an NTP server. To enable NTP, use the global configuration mode commands listed in the table.

| ASA Command                                 | Description                                                                                                      |
| ------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| `ntp authenticate`                          | Enables authentication with an NTP server.                                                                       |
| `ntp trusted-key {key_id}`                  | Specifies an authentication key ID to be a trusted key, which is required for authentication with an NTP server. |
| `ntp authentication-key {key_id} md5 {key}` | Sets a key to authenticate with an NTP server.                                                                   |
| `ntp server {ip_address} [key  {key_id}]`   | Identifies an NTP server.                                                                                        |
## DHCP Configuration

| ASA Command                                               | Description                                                                                                                                                                                                                                                                             |
| --------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `dhcpd address {IP_address1} [- {IP_address2}] {if_name}` | Creates a DHCP address pool in which _IP_address1_ is the start of the pool and _IP_address2_ is the end of the pool, separated by a hyphen.<br><br>The address pool must be on the same subnet as the ASA interface.                                                                   |
| `dhcpd dns {dns1} {dns2}`                                 | (Optional) Specifies the IP address(es) of the DNS server(s).                                                                                                                                                                                                                           |
| `dhcpd lease {lease_length}`                              | - (Optional) Changes the lease length granted to the client which is the amount of time in seconds that the client can use its allocated IP address before the lease expires.<br>- The _lease_length_ defaults to 3600 seconds (1 hour) but can be a value from 0 to 1,048,575 seconds. |
| `dhcpd domain {domain_name}`                              | (Optional) Specifies the domain name assigned to the client.                                                                                                                                                                                                                            |
| `dhcpd enable {if_name}`                                  | Enables the DHCP server service (daemon) on the interface (typically the inside interface) of the ASA.                                                                                                                                                                                  |
## Object Configuration

Objects are ==reusable components== for use in configurations. Objects can be defined and used in Cisco ASA configurations in the place of inline IP addresses, services, names, and so on. 

Objects make it ==easy to maintain configurations== because an object can be modified in one place and the change will be reflected in all other places that are referencing it.

There are ==two types== of objects that can be configured:

- **Network object** - A network object can contain a host, a network IP address, a range of IP addresses, or a fully qualified domain name (FQDN). A network object is configured using the **object network** command.
- **Service object** - Contains a protocol and optional source and/or destination port. A service object is configured using the **object service** command.

#### Network Object

To create a network object, use the `object network {object-name}` global configuration mode command. The prompt changes to network object configuration mode.

Commands available in network object configuration mode are shown in the table below.

Use the `no` form of any of these commands to remove a network object value. To erase all network objects, use the `clear config object network` command. This command clears **all** network objects.

| **ASA Command**                                                  | **Description**                                                                                                                                                                                      |
| ---------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `attribute {attribute-agent} {attribute-type} {attribute-value}` | Defined and used to filter traffic associated with one or more virtual machines.                                                                                                                     |
| `description`                                                    | Enter a description of the object up to 200 characters in length.                                                                                                                                    |
| `fqdn`                                                           | A fully-qualified domain name such as the name of a host, such as www.example.com. Specify v4 to limit the address to IPv4, and v6 for IPv6. If you do not specify an address type, IPv4 is assumed. |
| `host {ip-address}`                                              | The IPv4 or IPv6 address of a single host.                                                                                                                                                           |
| `range {start_add} {end_add}`                                    | A range of addresses. You can specify IPv4 or IPv6 ranges. Do not include masks or prefixes.                                                                                                         |
| `subnet [{ipv4_add} {ipv4_mask} / {ipv6_add_and_prefix}]`        | Assigns a network subnet to the named object.                                                                                                                                                        |

#### Service Object

The table below provides an overview of ==common service options== available. Optional keywords are used to identify source port or destination port, or both. Operators such as `eq` (equal), `neq `(not equal), `lt` (less than), `gt` (greater than), and `range`, support configuring a port for a given protocol. If no operator is specified, the default operator is `eq`.

| **ASA Command**                                                    | **Description**                                               |
| ------------------------------------------------------------------ | ------------------------------------------------------------- |
| `service {protocol}`                                               | Specifies an IP protocol name or number.                      |
| `service tcp [source {operator port} destination {operator port}]` | Specifies that the service object is for the TCP protocol.    |
| `service udp [source {operator port} destination {operator port}]` | Specifies that the service object is for the UDP protocol.    |
| `service icmp [{icmp-type} [{icmp_code}]]`                         | Specifies that the service object is for the ICMP protocol.   |
| `service icmp6 [{icmp-type} [{icmp_code}]]`                        | Specifies that the service object is for the ICMPv6 protocol. |
At this point, [[ASA ACLs]] could be configured if required.

## NAT Configuration

[[NAT]] on [[ASAs]] can be deployed using one of the methods:

---

**Inside NAT** - The typical NAT deployment method is when a host from a higher-security interface has traffic destined for a lower-security interface and the ASA translates the internal host address into a global address. The ASA then restores the original inside IP address for return traffic.

**Outside NAT** - This method is used when traffic from a lower-security interface that is destined for a host on the higher-security interface must be translated. This method may be useful to make an enterprise host located on the outside of the internal network appear as one from a known internal IP address.

**Bidirectional NAT** - Indicates that both inside NAT and outside NAT are used together.

---

The image below illustrates how inside NAT and outside NAT flow.

![[ASA Configuration-20240319154535951.webp#invert]]

Specifically, the Cisco ASA supports the following common types of NAT:

| Type         | Description                                                                                                                                                  |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Dynamic PAT  | This is a many-to-one translation. Also known as NAT with overload. Typically involves an inside pool of private addresses overloading an outside interface. |
| Static NAT   | This is a one-to-one translation. Usually involves an outside address mapping to an internal server.                                                         |
| Policy NAT   | Policy-based NAT operates based on a set of rules. These rules specify which addresses and/or ports will be translated based on certain criteria.            |
| Identity NAT | Real address statically translated to itself, bypassing NAT. Often used to exempt specific addresses from a larger group undergoing translation.             |
These types of NAT are referred to as *network object NAT* because the configuration requires network objects to be configured.

#### Dynamic NAT

To configure network object dynamic NAT, two network objects are required:

- An object identifying the pool of public IP addresses into which internal addresses are translated.
- An object identifying the internal addresses to be translated. These are identified using the range or subnet network object commands.

The two objects are then bound together using the following network object command syntax:

```
ASA(config)# object network name
ASA(config-network-object)# nat ({real_if_name},{mapped_if_name})] dynamic mapped_object [interface [ipv6]] [dns]
```

The `real_if_name` is the pre-NAT interface. The `mapped_if_name` is the post-NAT interface. Notice that there is no space after the comma in the command syntax.

To allow inside hosts to ping outside hosts, you can use a policy map to permit ICMP messages to return through the external interface.

> [!example]-
>  
> ```ASA(config)# object network PUBLIC
> ASA(config-network-object)# range 209.165.200.240 209.165.200.248
> ASA(config-network-object)# exit
> ASA(config)# 
> ASA(config)# object network DYNAMIC-NAT
> ASA(config-network-object)# subnet 192.168.1.0 255.255.255.224
> ASA(config-network-object)# nat (INSIDE,OUTSIDE) dynamic PUBLIC
> ASA(config-network-object)# exit
> ASA(config)#

#### NAT (PAT)

Port Address Translation (PAT) is a variant of NAT. Cisco ASA devices can be configured for Dynamic PAT. Dynamic PAT is used any time multiple internal hosts need to share a single public IP address.

Only one network object is required when overloading the outside interface. To enable inside hosts to overload the outside address (using Dynamic PAT), use the `nat [(real_if_name,mapped_if_name)] dynamic interface network object` configuration command.

> [!example]-
> ```
> ASA(config)# object network INSIDE-NET   
> ASA(config-network-object)# subnet 192.168.1.0 255.255.255.224   
> ASA(config-network-object)# nat (INSIDE,OUTSIDE) dynamic interface   
> ASA(config-network-object)# end   
> ASA#

#### Static NAT

Static NAT is configured when an inside address is mapped to an outside address. For instance, static NAT can be used when a server must be accessible from the outside.

To configure static NAT, use the `nat [(real_if_name,mapped_if_name)] static mapped_ip` network object configuration command.

> [!note]-
> An ACL is required for a dynamic translation to be successful.

> [!example]-
> ```
ASA(config)# object network DMZ-SERVER   
ASA(config-network-object)# host 192.168.2.3   
ASA(config-network-object)# nat (DMZ,OUTSIDE) static 209.165.200.227   
ASA(config-network-object)# exit   
ASA(config)#     
ASA(config)# access-list OUTSIDE-DMZ extended permit ip any host 192.168.2.3   
ASA(config)# access-group OUTSIDE-DMZ in interface OUTSIDE   
ASA(config)#     
ASA(config)# policy-map global_policy   
ASA(config-pmap)# class inspection_default   
ASA(config-pmap-c)# access-list ICMPACL extended permit icmp any any   
ASA(config)# access-group ICMPACL in interface DMZ   
ASA(config)#```

## AAA Configuration

Cisco ASA can be configured to authenticate using a local user database or an external server for authentication or both.

To enable authentication of users connecting via console port, SSH, HTTPS, or Telnet, or to authenticate users attempting to access privileged EXEC mode, use the following command syntax:

`ASA(config)# aaa authentication [serial / enable / telnet / ssh / http] console  [LOCAL / {server-group} LOCAL]`

Use the `username {name} password {password} privilege {priv-level}` command to create local user accounts. To erase a user from the local database, use the `clear config username [name]` command. To view all user accounts, use the `show running-config username` command.

#### TACACS & RADIUS

To configure a TACACS+ or RADIUS server, use the following steps:

- Create a TACACS+ or RADIUS AAA server group via the `aaa-server {server-tag} protocol [tacacs+ / radius]` configuration command. This will enter the AAA-server-group sub-configuration mode.
  
- Configure a AAA server as part of a AAA server group, via the `aaa-server {server-tag} [{if}] host [{server-ip} / {hostname}] {key}` command. This will enter the host-specific AAA sub-configuration mode.
  
- Configure any remaining, host-specific parameters.

To erase AAA configurations, use the following commands:

- `clear config aaa-server` — remove all AAA server configurations.
- `clear config aaa` — remove all AAA-based console authentication configurations.

To view AAA configurations, use the following commands:

- `show running-config aaa-server` — view all configured AAA servers and host-specific parameters.
- `show running-config aaa` — view all AAA-based console authentication configurations.

> [!example]-
> ```
ASA(config)# username Admin password class privilege 15
ASA(config)# show run username
! username Admin password ***** pbkdf2 privilege 15
ASA(config)# aaa-server TACACS-SVR protocol tacacs+
ASA(config-aaa-server-group)# aaa-server TACACS-SVR (DMZ) host 192.168.2.3
ASA(config-aaa-server-host)# exit
ASA(config)# show run aaa-server
! aaa-server TACACS-SVR protocol tacacs+
! aaa-server TACACS-SVR (DMZ) host 192.168.2.3
ASA(config)# 
ASA(config)# aaa authentication serial console TACACS-SVR LOCAL
ASA(config)# aaa authentication ssh console TACACS-SVR LOCAL
ASA(config)# show run aaa
aaa authentication serial console TACACS-SVR LOCAL
aaa authentication ssh console TACACS-SVR LOCAL
ASA(config)# ```