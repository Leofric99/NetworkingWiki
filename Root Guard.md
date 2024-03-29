---
tags:
  - Studies
  - CyberSecurity
  - Theory
description: Provides a way to enforce the placement of root bridges in the network by limiting which switch can become the root bridge.
---
There are some switches in a network that should never, under any circumstances, become the STP root bridge. Root Guard provides a way to enforce the placement of root bridges in the network by limiting which switch can become the root bridge.

> [!tldr]
> If a root-guard-enabled port receives [[BPDUs]] that are superior to those that the current root bridge is sending, that port is moved to a root-inconsistent state. This is effectively equal to an STP listening state, and no data traffic is forwarded across that port thus preventing an unauthorised switch from becoming the root bridge.

Root Guard is often used in conjunction with [[Loop Guard]].
## How it Works

Root guard is best deployed on ports that connect to switches that should not be the root bridge. 

If a root-guard-enabled port receives [[BPDUs]] that are superior to those that the current root bridge is sending, that port is moved to a root-inconsistent state. This is effectively equal to an STP listening state, and no data traffic is forwarded across that port. Recovery occurs as soon as the offending device ceases to send superior BPDUs.

> [!note]
> Root guard may seem unnecessary because an administrator can manually set the bridge priority of a switch to zero. 
> 
> However, this does not guarantee that this switch will be elected as the root bridge. Another switch may still become the root if it also has a priority of zero and a lower MAC address.

In the image, D1 is the root bridge. If D1 fails, only D2 switch should become the root bridge. To ensure that S1 never becomes a root bridge, the F0/1 interfaces of D1 and D2 should be enabled for Root guard.

![[Root Guard-20240323160251952.webp#invert|590]]

To view Root Guard ports that have received superior BPDUs and are in a root-inconsistent state, use the `show spanning-tree inconsistentports` command.

Use the` spanning-tree guard root` interface configuration command to configure root guard on an interface. All the other commands can be found here: [[STP Commands#Configuring Root Guard and Loop Guard]].