---
tags:
  - Studies
  - Networking
  - CyberSecurity
  - Commands
aliases:
  - Switched Port Analyser Commands
cssclasses:
  - commands
---
The SPAN feature on Cisco switches sends a copy of each frame entering the source port out the destination port and toward the packet analyser or IDS.

For theoretical information about SPAN, see [[SPAN]].

## Configuration Commands

| Mode | Command | Description | Variable(s) |
|:-----|:---|:---|:---|
| `config`     | `monitor session {number} source [interface {interface} / vlan {vlan}]` | Associates a source port or [[VLANs\|VLAN]] with a SPAN session. | `{number}` A session number used to identify a SPAN session. `{interface}` The interface ID. `{vlan}` The VLAN ID. |
| `config`     | `monitor session {number} destination [interface {interface} / vlan {vlan}]` | Associates a destination port or [[VLANs\|VLAN]] with a SPAN session. | `{number}` A session number used to identify a SPAN session. `{interface}` The interface ID. `{vlan}` The VLAN ID. |  
## Show Commands

| Mode | Command | Description | Variable(s) |
|:---|:---|:---|:---|
| Privileged Exec | `show monitor` | Used to verify the SPAN session. The command displays the type of the session, the source ports for each traffic direction, and the destination port. | N/A |  
