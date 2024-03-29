---
tags:
  - Studies
  - Table
  - Networking
  - Commands
cssclasses:
  - commands
aliases:
  - Syslog Commands
---
These commands show you how to configure Logging on Cisco IOS devices.

## Syslog Configuration

| Mode     | Command                                | Description                                                              | Variables `{}` or Options `[]`                             |
| :------- | :------------------------------------- | :----------------------------------------------------------------------- | :--------------------------------------------------------- |
| `config` | `logging host {ip}`                    | Sets a remote server for syslog messages.                                | `{ip}` is the remote IP address of the Syslog server.      |
| `config` | `logging trap {level}`                 | Sets which severity of log messages should be sent to the Syslog server. | `{level}` is the desired severity level (0-7) for logging. |
| `config` | `service timestamps log datetime msec` | Sets log messages to be sent with timestamps.                            | N/A                                                        |

## Show Commands

| Command                   | Description                                                                                               | Variables `{}` or Options `[]` |
| :------------------------ | :-------------------------------------------------------------------------------------------------------- | :----------------------------- |
| `show running-config`     | Shows the running configuration.                                                                          | N/A                            |
| `show logging`            | Displays the logging settings, including the configured Syslog server and the severity level for logging. | N/A                            |
| `show logging host`       | Displays the configured remote Syslog server(s) to which log messages are being sent.                     | N/A                            |
| `show logging trap`       | Displays the configured severity level for logging messages sent to the Syslog server.                    | N/A                            |
| `show ip interface brief` | Checks the status of all interfaces, ensuring connectivity to the configured remote Syslog server.        | N/A                            |