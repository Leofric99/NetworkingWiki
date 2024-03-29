---
tags:
  - Studies
  - Table
  - Commands
  - CyberSecurity
  - Networking
cssclasses:
  - commands
---
There is some crossover here with [[AAA Commands]]. These commands are specifically for configuring the RADIUS server whilst the AAA Commands are for configuring an entire AAA Suite.

## Configuration Commands

| Mode                   | Command                                                           | Description                                                                                          | Variables `{}` or Options `[]`                                                                                                                                                                                                                                                  |
| :--------------------- | :---------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `config`               | `aaa new-model`                                                   | Enables AAA on the device.                                                                           | N/A                                                                                                                                                                                                                                                                             |
| `config`               | `radius server {name}`                                            | Enters RADIUS server config mode.                                                                    | `{name}` The desired name for the RADIUS server.                                                                                                                                                                                                                                |
| `config-radius-server` | `address {type} {ip-address} auth-port {port1} acct-port {port2}` | Sets the IP address and port numbers of the RADIUS server.                                           | `{type}` The IP version (`ipv4` or `ipv6`). `{ip-address}` the IP address of the server. `{port1}` The authentication [[AAA Commands#Port Numbers\|port number]]. `{port2}` The accounting [[AAA Commands#Port Numbers\|port number]]. `{port2}` doesn't work in packet tracer. |
| `config-radius-server` | `key {key}`                                                       | Configures a password to encrypt the data transfer between the RADIUS server and AAA-enabled router. | `{key}` Any desired password.                                                                                                                                                                                                                                                   |
## Show Commands

| Command               | Description                                    | Variables `{}` or Options `[]` |
| :-------------------- | :--------------------------------------------- | :----------------------------- |
| `show running-config` | Shows the running configuration of the device. | N/A                            |