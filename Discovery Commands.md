---
tags:
  - Studies
  - Table
  - Networking
  - Commands
cssclasses:
  - commands
aliases:
  - CDP Commands
  - LLDP Commands
---
Discovery protocols allow network administrators to 'discover' devices on the network. The industry standard for this is [[LLDP]], Cisco has also developed its own proprietary protocol for this in the form of [[CDP]].

> [!important]
> Both [[LLDP]], and [[CDP]], are enabled by default on all Cisco network devices. This can be a security risk. Consider disabling these protocols by putting `no` in front of some of these commands below.

| Mode        | Command         | Description                                | Variables `{}` or Options `[]` |
| :---------- | :-------------- | :----------------------------------------- | :----------------------------- |
| `config`    | `cdp run`       | Enables CDP on the device.                 | N/A                            |
| `config-if` | `cdp enable`    | Enables CDP on a specific interface.       | N/A                            |
| `config`    | `lldp run`      | Enables LLDP on the device.                | N/A                            |
| `config-if` | `lldp transmit` | Enables LLDP transmitting on an interface. | N/A                            |
| `config-if` | `lldp receive`  | Enables LLDP receiving on an interface.    | N/A                            |

## Show Commands

| Command                      | Description                      | Variables `{}` or Options `[]` |
| :--------------------------- | :------------------------------- | :----------------------------- |
| `show cdp`                   | Allows you to verify CDP status. | N/A                            |
| `show cdp neighbors detail`  | Shows CDP neighbours in detail.  | N/A                            |
| `show lldp neighbors detail` | Shows LLDP neighbours in detail. | N/A                            |