---
tags:
  - Studies
  - Table
  - Networking
  - Commands
cssclasses:
  - commands
---
## Configuration Commands


| Mode          | Command                                                        | Description                                                                | Variables `{}` or Options `[]`                                                                              |
| :------------ | :------------------------------------------------------------- | :------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------- |
| `config`      | `ip domain-name {FQDN}`                                        | Sets the domain name for SSH access.                                       | `{FQDN}` The fully qualified domain name to be used for SSH access.                                         |
| `config`      | `crypto key generate rsa general-keys modulus {modulus-value}` | Generates a crypto key for the SSH encryption using a given modulus value. | `{modulus-value}` The desired modulus value for the RSA key generation, typically `1024` or `2048`.         |
| `config`      | `username {username} secret {password}`                        | Create a local user account if you haven't already.                        | `{username}` The username for the local user account. `{password}` The password for the local user account. |
| `config`      | `line vty {vty-lines}`                                         | Sets which VTY lines to configure.                                         | `{vty-lines}` The range of VTY lines to configure, e.g., `0 15` for all VTY lines.                          |
| `config-line` | `transport input ssh`                                          | Sets SSH as the access method.                                             | N/A                                                                                                         |
| `config-line` | `ip ssh version 2`                                             | Sets SSH version 2 for improved security.                                  | N/A                                                                                                         |
| `config-line` | `login local`                                                  | Tells it to use the local user account(s) as the login method.             | N/A                                                                                                         |
| `config`      | `ip ssh time-out {time}`                                       | Change timeout setting.                                                    | `{time}` is the desired timeout value (in seconds)                                                          |
| `config`      | `ip ssh authentication-retries {retries}`                      | Change number of allowed authentication attempts.                          | `{retries}` is the desired number of retries.                                                               |

## Show Commands

| Command                         | Description                                    | Variables `{}` or Options `[]`       |
| :------------------------------ | :--------------------------------------------- | :----------------------------------- |
| `show running-config`           | Shows the running configuration of the device. | N/A                                  |
| `show ip interface tunnel {no}` | Shows information about a tunnel interface.    | `{no}` is the desired tunnel number. |
| `show ip ssh`                   | Shows SSH configuration information.           | N/A                                  |