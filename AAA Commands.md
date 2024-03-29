---
tags:
  - Studies
  - Table
  - Commands
  - CyberSecurity
cssclasses:
  - commands
---
AAA (Authentication, Authorisation, Accounting) forms the cornerstone of cybersecurity, ensuring only the right people access the right things, and tracking their activity for accountability. For the theory, see [[AAA]].

## Detailing the TACACS+ Server to the Networking Device

| Mode | Command | Description | Variables `{}` or Options `[]` |
| :--- | :--- | :--- | :--- |
| `config` | `aaa new-model` | Enables AAA on the device. | N/A |
| `config` | `tacacs server {name}` | Enters TACACS server config mode. | `{name}` The desired TACACS server name. |
| `config-server-tacacs` | `address {type} {ip-address}` | Sets the IP address of the TACACS server. | `{type}` The IP version (`ipv4` or `ipv6`). `{ip-address}` the IP address of the server.` |
| `config-server-tacacs` | `single-connection` | Improves performance by maintaining one single [[TCP]] connection. | N/A |
| `config-server-tacacs` | `key {key}` | Configures a password to encrypt the data transfer between the TACACS server and AAA-enabled router. | `{key}` Any desired password. |

## Detailing the RADIUS Server to the Networking Device

| Mode                   | Command                                                           | Description                                                                                          | Variables `{}` or Options `[]`                                                                                                                                                                                                                                                  |
| :--------------------- | :---------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `config`               | `aaa new-model`                                                   | Enables AAA on the device.                                                                           | N/A                                                                                                                                                                                                                                                                             |
| `config`               | `radius server {name}`                                            | Enters RADIUS server config mode.                                                                    | `{name}` The desired name for the RADIUS server.                                                                                                                                                                                                                                |
| `config-radius-server` | `address {type} {ip-address} auth-port {port1} acct-port {port2}` | Sets the IP address and port numbers of the RADIUS server.                                           | `{type}` The IP version (`ipv4` or `ipv6`). `{ip-address}` the IP address of the server. `{port1}` The authentication [[AAA Commands#Port Numbers\|port number]]. `{port2}` The accounting [[AAA Commands#Port Numbers\|port number]]. `{port2}` doesn't work in packet tracer. |
| `config-radius-server` | `key {key}`                                                       | Configures a password to encrypt the data transfer between the RADIUS server and AAA-enabled router. | `{key}` Any desired password.                                                                                                                                                                                                                                                   |

## Authentication

| Mode          | Command                                                       | Description                                                                                                   | Variables `{}` or Options `[]`                                                                                                                                                                                                                                                                                    |
| :------------ | :------------------------------------------------------------ | :------------------------------------------------------------------------------------------------------------ | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `config`      | `aaa new-model`                                               | Enables AAA on the device.                                                                                    | N/A                                                                                                                                                                                                                                                                                                               |
| `config`      | `username {username} algorithm-type {type} secret {password}` | Creates a local user for authentication.                                                                      | `{username}` The desired username.`{type}` Algorithm type. One example is `scrypt`. `{password}` The desired password.                                                                                                                                                                                            |
| `config`      | `aaa authentication login [default / {list-name}] {method}`   | Configures VTY line AAA login.                                                                                | `[default]` Sets configuration to all VTY lines. `[{list-name}]` Replaces `[default]` so that the authentication config can be applied to different VTY lines separately. `{method}` Sets the AAA [[AAA Commands#Methods\|Method]] for authentication. Multiple can be specified one after the other with spaces. |
| `config-line` | `login authentication {list-name}`                            | Configures AAA login configuration (as above) to certain VTY lines.                                           | `{list-name}` is the list of whatever AAA method you have selected above is. You will need to set this up first.                                                                                                                                                                                                  |
| `config`      | `aaa local authentication attempts max-fail {number}`         | Sets a maximum number of incorrect login attempts before the connection is dropped and the account is locked. | `{number}` The desired maximum number of incorrect login attempts.                                                                                                                                                                                                                                                |

## Authorisation Commands

| Mode | Command | Description | Variables `{}` or Options `[]` |
| :--- | :--- | :--- | :--- |
| `config` | `aaa authorization [network / exec / commands {level}] [default / {list}] {method}` | Configures Authorisation on the device. | `[network]` Allows access to network services such as PPP and SLIP. `[exec]` Allows access to user exec sessions (not privileged).`{level}` The desired privilege level (1 - 15). `[default]` Sets configuration to all VTY lines. `[{list-name}]` Replaces `[default]` so that the authentication config can be applied to different VTY lines separately. `{method}` Sets the AAA [[AAA Commands#Methods\|Method]] for authentication. Multiple can be specified one after the other with spaces. |
## Accounting Commands

| Mode | Command | Description | Variables `{}` or Options `[]` |
| :--- | :--- | :--- | :--- |
| `config` | `aaa accounting [network / exec / connection] [default / {list-name}] [start-stop / stop-only / none]` | Configures Accounting on the device. | `[network]` Runs accounting on network services such as PPP and SLIP. `[exec]` Runs accounting on user exec sessions (not privileged). `[default]` Sets accounting on all VTY lines. `[{list-name}]` Replaces `[default]` so that the accounting config can be applied to different VTY lines separately. `[start-stop]` Sends a "start" accounting notice at the beginning of a process and a "stop" accounting notice at the end of a process. `stop-only` Sends a "stop" accounting record for all cases including authentication failures. `none` Disables accounting services on a line or interface. |

## Show Commands

| Command | Description | Variables `{}` or Options `[]` |
| :--- | :--- | :--- |
| `show aaa local user lockout` | Displays a list of all locked-out users. | N/A |
| `show aaa sessions` | Shows the unique ID of sessions. | N/A |


## Methods

| Method Type Keywords | Description                                                                                                                                  |
| -------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| `enable`             | Uses the enable password for authentication.                                                                                                 |
| `local`              | Uses the local username database for authentication.                                                                                         |
| `local-case`         | Uses case-sensitive local username authentication.                                                                                           |
| `none`               | Uses no authentication.                                                                                                                      |
| `group radius`       | Uses the list of all RADIUS servers for authentication.                                                                                      |
| `group tacacs+`      | Uses the list of all TACACS+ servers for authentication.                                                                                     |
| `group {group-name}` | Uses a subset of RADIUS or TACACS+ servers for authentication as defined by the AAA group server radius or AAA group server tacacs+ command. |
## Port Numbers

| Allocation | Port Number |
|:-----------|:------------|
| Cisco Authentication           | 1645            |
| [[IANA]] Authentication           | 1812            |
| Cisco Accounting           | 1646            |
| [[IANA]] Accounting           | 1813            |  