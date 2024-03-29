---
tags:
  - Studies
  - Networking
  - CCNA
  - Theory
  - COM412
description: A text-based interface used to configure and manage Cisco networking devices.
---

## What is a CLI?

A CLI, or Command Line Interface is what is used to directly interact with a device without a GUI, or Graphical User Interface.

An administrator can connect to the CLI using multiple methods:

- A Console Connection (via a console cable)
- An SSH or Telnet Connection (via the network)

## Cisco IOS CLI Modes

Cisco IOS's CLI has various modes. Each mode can be used for different things and has different capabilities. The modes are as follows:

![[Pasted image 20240207124135.png]]

- **User EXEC (>)**: Basic mode for viewing info (show commands) but limited configuration. Think "read-only".

- **Privileged EXEC (#)**: More powerful mode with full configuration access. Requires a password! Like an administrator account.

- **Configure Terminal**: Enter this sub mode from Privileged EXEC to modify device settings. Imagine it as an editing workspace.

- **Other sub modes**: Within Configure Terminal, specific modes exist for configuring interfaces, routing, lines, etc. Each focuses on a particular area.

