---
tags:
  - Studies
  - CyberSecurity
  - Theory
description: Prevents alternate or root ports from becoming designated ports due to a failure leading to a unidirectional link.
---
Traffic on bidirectional switch links flows in both directions. If for some reason one-direction traffic flow fails, this creates a unidirectional link which can result in a Layer 2 loop. 

> [!tldr]
> If [[BPDUs]] are not received on a non-designated Loop Guard-enabled port, the port transitions to a loop-inconsistent blocking state, instead of the listening / learning / forwarding state thus preventing it from becoming a designated port and causing a loop.

Loop Guard is often used in conjunction with [[Root Guard]].
## How it Works

[[STP]] relies on continuous reception or transmission of [[BPDUs]] based on the port role. The designated port transmits BPDUs, and the non-designated port receives BPDUs. 

A Layer 2 loop is usually created when an STP port in a redundant topology stops receiving BPDUs and erroneously transitions to the forwarding state.

As shown here, Loop Guard is enabled on all non-Root Guard ports using the `spanning-tree guard loop` interface configuration command.

![[Loop Guard-20240323161055584.webp#invert]]

The commands for loop guard can be found here: [[STP Commands#Configuring Root Guard and Loop Guard]].