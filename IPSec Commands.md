---
tags:
  - Studies
  - Table
  - Networking
  - Commands
  - CyberSecurity
cssclasses:
  - commands
aliases:
  - VPN Commands
---
## Configuration Commands

> [!important]
> These commands **must** be replicated (with variables adjusted where appropriate) on *both* sides of the IPSec VPN.

| Mode                | Command                                                                                                          | Description                                                                                                                                                | Variables `{}` or Options `[]`                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| :------------------ | :--------------------------------------------------------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `config`            | `license boot module c1900 technology-package securityk9`                                                        | Enables the securityk9 package at boot.                                                                                                                    | N/A                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Privileged Exec     | `copy running-config startup-config`                                                                             | Saves the running-config to startup-config.                                                                                                                | N/A                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Privilege Exec      | `reload`                                                                                                         | Reloads the router which enables the securityk9 package.                                                                                                   | N/A                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `config`            | `access-list {number/name} permit ip [any / host / {from-addr} {from-wild}] [any / host /& {to-addr} {to-wild}]` | Creates an [[ACLs\|ACL]] to identify traffic that *should* travel via the [[VPNs\|VPN]] as 'interesting' which will trigger the IPSec VPN once configured. | `{number/name}` the desired ACL number or name. `[any]` identifies packets from anywhere. `[host]` identifies packets from a particular host. `{from-addr}` specifies the host IP address (if `[host]` was used) or the origin network address of packets bound for the VPN. `{from-wild}` the wildcard mask for the last variable. `{to-addr}` the same as `{from-addr}` but for the destination. `{to-wild}` the same as `{from-wild}` but for the destination. |
| `config`            | `crypto isakmp policy {no}`                                                                                      | Creates a crypto [[ISAKMP]] policy (other options are available) for the IPSec VPN.                                                                        | `{no}` is the desired policy number.                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `config-isakmp`     | `encryption [3des / aes / des] {key-length}`                                                                     | Specifies the encryption type, and key length for the policy.                                                                                              | `[3des]` specifies [[3DES]] encryption is to be used. `[aes]` specifies [[AES]] encryption is to be used. `[des]` specifies [[DES]] encryption is to be used. `{key-length}` is the desired [[PSKs#Key Types\|PSK]] length.                                                                                                                                                                                                                                       |
| `config-isakmp`     | `authentication pre-share`                                                                                       | Sets the method of authentication to [[PSKs]].                                                                                                             | N/A                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `config-isakmp`     | `group {no}`                                                                                                     | Sets the [[DH]] group for the policy.                                                                                                                      | `{no}` is the [[DH#Diffie-Hellman Groups\|Diffie-Hellman group number]].                                                                                                                                                                                                                                                                                                                                                                                          |
| `config`            | `crypto isakmp key {key} address {addr}`                                                                         | Specifies the PSK, and the device which will be using that particular PSK.                                                                                 | `{key}` is the [[PSKs\|PSK]] which will be used for VPN traffic from the specified IP address. `{addr}` is the desired remote device IP address which will be using this key.                                                                                                                                                                                                                                                                                     |
| `config`            | `crypto ipsec transform-set {name} {encryption-algorithm} {integrity-algorithm}`                                 | Creates the transform set with desired attributes.                                                                                                         | `{name}` is the name of the transform set. `{encryption-algorithm}` is the encryption algorithm to be used e.g. `esp-aes`. `{integrity-algorithm}` is the [[Hashing]] algorithm to use e.g. `esp-sha-hmac`. Use `?` to see options.                                                                                                                                                                                                                               |
| `config`            | `crypto map {name} {no} {protocols}`                                                                             | Creates a new crypto map and enters crypto map configuration mode.                                                                                         | `{name}` is the desired crypto map name. `{no}` is the desired crypto map number. `{protocols}` all the policies you want to use with this crypto map e.g. `ipsec-isakmp` which would apply to both [[IPSec]] and [[ISAKMP]]. Use `?` to view options.                                                                                                                                                                                                            |
| `config crypto-map` | `description {description}`                                                                                      | Sets a description for the crypto map.                                                                                                                     | `{description}` is the desired crypto map description.                                                                                                                                                                                                                                                                                                                                                                                                            |
| `config crypto-map` | `set peer {addr}`                                                                                                | Sets a peer address for the crypto map.                                                                                                                    | `{addr}` is the IP address of the desired peer.                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `config crypto-map` | `set transform-set {name}`                                                                                       | Sets the transform set (which will be configured later on).                                                                                                | `{name}` is the name of the transform set that was configured above.                                                                                                                                                                                                                                                                                                                                                                                              |
| `config crypto-map` | `match address {no/name}`                                                                                        | Sets the ACL to check against.                                                                                                                             | `{no/name}` is the ACL number or name created earlier.                                                                                                                                                                                                                                                                                                                                                                                                            |
| `config`            | `interface {interface}`                                                                                          | Enters interface config mode.                                                                                                                              | `{interface}` is the interface name for the desired entry/exit interface for the VPN.                                                                                                                                                                                                                                                                                                                                                                             |
| `config-if`         | `crypto map {name}`                                                                                              | Applies the crypto map to the VPN entry/exit interface.                                                                                                    | `{name}` is the name of the crypto map created just before this.                                                                                                                                                                                                                                                                                                                                                                                                  |
> [!example]-  Example Configuration
> 
> ```# Install the module
license boot module c1900 technology-package securityk9
exit
copy running-config startup-config
reload
>
> # Creating the ACL to identify which traffic to encrypt
> ip access-list extended VPN_TO_NEWB
permit ip 192.168.10.0 0.0.0.255 192.168.5.0 0.0.0.255
permit ip 192.168.20.0 0.0.0.255 192.168.5.0 0.0.0.255
permit ip 192.168.10.0 0.0.0.255 194.34.5.0 0.0.0.255
permit ip 192.168.20.0 0.0.0.255 194.34.5.0 0.0.0.255
deny ip any any
exit
>
># Creating the ISAKMP policy
crypto isakmp policy 10
encryption aes 256
authentication pre-share
group 5 # Only 5 supported in packet tracer.
exit
>
>Setting PSK and transform set options
crypto isakmp key sha address 20.0.0.1
crypto ipsec transform-set SECURE_TRANSFORM esp-aes esp-sha-hmac
crypto map SECURE_SOTON_NEWB 10 ipsec-isakmp
description Links to Newbury Router. IPSec and ISAKMP in use.
set peer 20.0.0.1
set transform-set SECURE_TRANSFORM
match address VPN_TO_NEWB
exit
>
>Applying the IPSec VPN to the external interface of the router.
int s0/0/0
crypto map SECURE_SOTON_NEWB
exit


## Show Commands

| Command                | Description                                                   | Variables `{}` or Options `[]` |
| :--------------------- | :------------------------------------------------------------ | :----------------------------- |
| `show version`         | Allows you to verify that the securityk9 module is installed. | N/A                            |
| `show crypto ipsec sa` | Shows the [[IPSec]] [[SA]].                                   | N/A                            |

