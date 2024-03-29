---
tags:
  - Studies
  - Table
  - Networking
  - Commands
cssclasses:
  - commands
---
These commands detail a thorough initial configuration of a Cisco networking device. There may be some commands in here which are router or switch specific.

## Configuration

You will find a command-and-explanation table right below, and a text box with the same command sequence you can copy and paste on your device's terminal after that.

> [!note]-
> These commands work on both Cisco routers and switches.

| Mode          | Command                                  | Description                                                                              | Variables `{}` or Options `[]`                                                                                                          |
| ------------- | ---------------------------------------- | ---------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| `exec`        | `enable`                                 | Enter privileged EXEC mode.                                                              | N/A                                                                                                                                     |
| `exec`        | `configure terminal`                     | Enter global configuration mode.                                                         | N/A                                                                                                                                     |
| `config`      | `hostname {name}`                        | Sets a name for the device.                                                              | `{name}` is the desired hostname for the device (e.g. `R1`).                                                                            |
| `config`      | `no ip domain-lookup`                    | Disable DNS lookup.                                                                      | N/A                                                                                                                                     |
| `config`      | `enable secret {password}`               | Enables an encrypted password for privileged exec mode.                                  | `{password}` is the desired password.                                                                                                   |
| `config`      | `banner motd {banner}`                   | Creates a welcome message prior to login.                                                | `{banner}` is the desired message to display.                                                                                           |
| `config`      | `banner login {banner}`                  | Creates a welcome message on login.                                                      | `{banner}` is the desired message to display.                                                                                           |
| `config`      | `cdp run`                                | Ensure CDP (Cisco Discovery Protocol) is running (if desired). Could be a security risk. | N/A                                                                                                                                     |
| `config`      | `clock set {time} {date}`                | Sets the time on the device. It is usually better to use NTP.                            | `{time}` is the current time in the format hh:mm:ss. `{date}` is the current date in the format `MMM DD YYYY` (e.g. `JAN 23 2024`).     |
| `config`      | `clock timezone {timezone} [{offset}]`   | Sets the device timezone.                                                                | `{timezone}` is the time zone for the device (e.g. `GMT` or `PST`). `[{offset}]` is for if offset hours need to be applied (e.g. `-5`). |
| `config`      | `line console 0`                         | Enter console line configuration mode.                                                   | N/A                                                                                                                                     |
| `config-line` | `logging synchronous`                    | Enable synchronous logging to avoid interruption.                                        | N/A                                                                                                                                     |
| `config-line` | `history size {lines}`                   | Specify the size of command history.                                                     | `{lines}`: Number of lines for command history                                                                                          |
| `config-line` | `exec-timeout {minutes} {seconds}`       | Set the timeout for EXEC sessions.                                                       | `{minutes}`, `{seconds}`: Timeout duration                                                                                              |
| `config-if`   | `duplex [half / full / auto]`            | Sets the duplex mode on a switchport.                                                    | `[half / full / auto]` is the switch port duplex mode.                                                                                  |
| `config-if`   | `speed [10 / 100 / 1000 / 10000 / auto]` | Sets a specific bandwidth speed for a switchport.                                        | `[10 / 100 / 1000 / 10000 / auto]` is the desired speed in                                                                              |
| `config-if`   | `mdix auto`                              | Enables automatic [[MDIX]] negotiation on an Ethernet interface.                         | N/A                                                                                                                                     |
| `config`      | `service password-encryption`            | Encrypts all plaintext passwords.                                                        | N/A                                                                                                                                     |
| `exec`        | `copy running-config startup-config`     | Save the running configuration to the start-up configuration.                            | N/A                                                                                                                                     |


## Show Commands

| Command               | Description                                        | Variables `{}` or Options `[]` |
| --------------------- | -------------------------------------------------- | ------------------------------ |
| `show running-config` | Shows the device's running configuration.          | N/A                            |
| `show version`        | Shows information about the version of IOS.        | N/A                            |
