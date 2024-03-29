---
tags:
  - Studies
  - Table
  - Networking
  - Commands
  - CyberSecurity
cssclasses:
  - commands
---
This page details how to configure users and passwords in Cisco IOS.

## Configuration Commands

| Mode          | Command                                  | Description                                                                                                    | Variables `{}` or Options `[]`                                                                              |
| :------------ | :--------------------------------------- | :------------------------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------- |
| `config`      | `enable secret {password}`               | Protects Privileged Exec mode with a password which is encrypted for security when it is stored on the device. | `{password}` is the desired password.                                                                       |
| `config`      | `line console 0`                         | Enters line config mode.                                                                                       | N/A                                                                                                         |
| `config-line` | `password {password}`                    | Creates a password for User Exec mode for console connections.                                                 | `{password}` is the desired password.                                                                       |
| `config-line` | `login`                                  | Finalises the User Exec mode password for console connections by enabling logins.                              | N/A                                                                                                         |
| `config`      | `username {username} secret {password}`  | Create a local user.                                                                                           | `{username}` The username for the local user account. `{password}` The password for the local user account. |
| `config`      | `security passwords min-length {length}` | Sets a minimum password length policy for local users (on the device).                                         | `{length}` is the minimum number of characters for a password.                                              |
| `config`      | `service password-encryption`            | Encrypts all plaintext passwords currently stored on the device.                                               | N/A                                                                                                         |

## Show Commands

| Command                   | Description                                                                                             | Variables `{}` or Options `[]` |
| ------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------ |
| `show running-config`     | Displays the current running configuration, including configured passwords and encryption settings.     | N/A                            |
| `show users`              | Displays information about currently logged-in users.                                                   | N/A                            |
| `show enable secret`      | Displays the encrypted enable secret password configured to protect privileged EXEC mode.               | N/A                            |
| `show line console 0`     | Displays configuration details of console line 0, including any configured password and login settings. | N/A                            |
| `show security passwords` | Displays the minimum password length policy configured on the device.                                   | N/A                            |