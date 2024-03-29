---
tags:
  - Studies
  - CyberSecurity
  - Theory
aliases:
  - Spanning Tree Protocol Attacks
  - Spanning Tree Attacks
description: Attacks which involve manipulating the [[STP]] protocol to disrupt network traffic and potentially launch further exploits.
---
Threat actors can manipulate [[STP]] to conduct an attack by spoofing the root bridge and changing the topology of a network. Attackers can make their hosts appear as root bridges; and therefore, capture all traffic for the immediate switched domain.

> [!tldr]
> Malicious [[BPDUs]] are sent by the attacking host which announce a lower bridge priority in an attempt to be elected as the root bridge.

## How it Works

To conduct an STP manipulation attack, the ==attacking host broadcasts== STP [[BPDUs]] containing configuration and topology changes that will force spanning-tree recalculations, as shown in the image below.

![[STP Attacks-20240323154803264.webp#invert]]

Malicious [[BPDUs]] are sent by the attacking host which announce a lower bridge priority in an attempt to be elected as the root bridge.

> [!note]-
> These issues can occur when someone adds an Ethernet switch to the network without any malicious intent.

If successful, the attacking host ==becomes the root bridge==, as shown in the figure below, and can now capture a variety of frames that would otherwise not be accessible.

![[STP Attacks-20240323155236435.webp#invert]]

## Mitigating STP Attacks

To mitigate STP manipulation attacks, use the Cisco STP stability mechanisms to enhance the overall performance of the switches and to reduce the time that is lost during topology changes.

| Technique      | Description                                                                                                                                                           | Application                                               |
| -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------- |
| PortFast       | Immediately brings an interface that is configured as an access or trunk port to the forwarding state from a blocking state, bypassing listening and learning states. | Apply to all end-user ports.                              |
| BPDU Guard     | Immediately error disables a port that receives a BPDU, typically used on PortFast enabled ports.                                                                     | Apply to all end-user ports.                              |
| [[Root Guard]] | Prevents an inappropriate switch from becoming the root bridge, limiting switch ports for root bridge negotiation.                                                    | Apply to all ports which should not become root ports.    |
| [[Loop Guard]] | Prevents alternate or root ports from becoming designated ports due to a failure leading to a unidirectional link.                                                    | Apply to all ports that are or can become non-designated. |
