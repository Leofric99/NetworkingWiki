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
For information about PVLANs, click [[PVLANs|here]].

## Configuration Commands

| Mode        | Command                | Description                                                                                                    | Variables `{}` or Options `[]` |
| :---------- | :--------------------- | :------------------------------------------------------------------------------------------------------------- | :----------------------------- |
| `config-if` | `switchport protected` | Configures the port as a protected port in order to make use of the [[PVLANs#PVLAN Edge\|PVLAN Edge feature]]. | N/A                            |

## Show Commands

| Command                            | Description                                                        | Variables `{}` or Options `[]`    |
| :--------------------------------- | :----------------------------------------------------------------- | :-------------------------------- |
| `show interfaces {int} switchport` | View the configuration of [[Trunking]], [[VLANs]], and [[PVLANs]]. | `{int}` is the desired interface. |