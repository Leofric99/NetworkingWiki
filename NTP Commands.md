---
tags:
  - Studies
  - Table
  - Networking
  - Commands
  - CCNA
cssclasses:
  - commands
---
[[NTP]] commands in Cisco IOS enable the configuration and management of Network Time Protocol settings for accurate time synchronisation across a network.

## Configuration Commands

| Mode     | Command                | Description                                | Variables `{}` or Options `[]`                   |
| :------- | :--------------------- | :----------------------------------------- | :----------------------------------------------- |
| `config` | `ntp server {ip_addr}` | Sets the NTP source server for the device. | `{ip_addr}` is the IP address of the NTP server. |

## Show Commands

| Command                 | Description                                                                                            | Variables `{}` or Options `[]` |
| :---------------------- | :----------------------------------------------------------------------------------------------------- | :----------------------------- |
| `show ntp associations` | Allows you to verify NTP configuration.                                                                | N/A                            |
| `show ntp status`       | More NTP verification, displays stratum information (how far the device is away from the time source). | N/A                            |
