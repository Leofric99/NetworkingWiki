---
tags:
  - Studies
  - Table
  - Commands
  - CyberSecurity
cssclasses:
  - commands
---
There is some overlap here with [[AAA Commands]].

Configuring 802.1X requires a few basic steps:

1. Enable AAA using the `aaa new-model` command.  
2. Designate the RADIUS server and configure its address and ports.  
3. Create an 802.1X port-based authentication method list using the `aaa authentication dot1x` command.  
4. Globally enable 802.1X port-based authentication using the `dot1x system-auth-control` command.  
5. Enable port-based authentication on the interface using the `authentication port-control auto` command.  
6. Enable 802.1X authentication on the interface using the `dot1x pae` command. 

## Configuration Commands

| Mode                     | Command                                                        | Description                                                                                          | Variables `{}` or Options `[]`                                                                                                                                                                                                                                                  |
| :----------------------- | :------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `config`                 | `aaa new-model`                                                | Enables AAA on the device.                                                                           | N/A                                                                                                                                                                                                                                                                             |
| `config`                 | `radius server {server}`                                       | Sets the [[AAA Commands#RADIUS Server Configuration\|RADIUS]] server in use.                         | `{server}` is the RADIUS server name or IP address.                                                                                                                                                                                                                             |
| `config-{server}-server` | `address {type} {address} auth-port {port1} acct-port {port2}` | Sets the IP address and port numbers to be used for the RADIUS server.                               | `{type}` The IP version (`ipv4` or `ipv6`). `{ip-address}` the IP address of the server. `{port1}` The authentication [[AAA Commands#Port Numbers\|port number]]. `{port2}` The accounting [[AAA Commands#Port Numbers\|port number]]. `{port2}` doesn't work in packet tracer. |
| `config-{server}-server` | `key {key}`                                                    | Configures a password to encrypt the data transfer between the RADIUS server and AAA-enabled router. | `{key}` Any desired password.                                                                                                                                                                                                                                                   |
| `config`                 | `aaa authentication dot1x default group {group}`               | Creates an 802.1X port-based authentication method list.                                             | `{group}` is the [[AAA Commands#Methods\|method]].                                                                                                                                                                                                                              |
| `config`                 | `dot1x system-auth-control`                                    | Globally enables 802.1X port-based authentication.                                                   | N/A                                                                                                                                                                                                                                                                             |
| `config-if`              | `authentication port-control auto`                             | Enables port-based authentication on the interface.                                                  | N/A                                                                                                                                                                                                                                                                             |
| `config-if`              | `dot1x pae {[supplicant / authenticator / both]}`              | Enables 802.1X authentication on the interface.                                                      | `{[supplicant]}` means that the interface will not respond to messages meant for an authenticator. `{[authenticator]}` means that the interface will not respond for messages meant for a supplicant. `{[both]}` means that the interface acts as both roles at once.           |

## Show Commands

| Command               | Description                               | Variables `{}` or Options `[]` |
| :-------------------- | :---------------------------------------- | :----------------------------- |
| `show running-config` | Shows the device's running configuration. | N/A                            |