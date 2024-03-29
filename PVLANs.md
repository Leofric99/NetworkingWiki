---
tags:
  - Studies
  - CyberSecurity
  - Acronym
  - Theory
  - Networking
aliases:
  - Private VLANs
description: Provides Layer 2 isolation between ports within the same broadcast domain.
---
[[VLANs]] are [[broadcast domains]]. However, in some situations, it may useful to break this rule and allow only the minimum required layer two connectivity within the VLAN.

## Port Types

Private VLANs (PVLAN) provide Layer 2 isolation between ports within the same broadcast domain. There are three types of PVLAN ports:

| Port Type   | Description                                                                                                                                                                                                                               |
| ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Promiscuous | A promiscuous port ==can talk to everyone==. It can communicate with all interfaces, including the isolated and community ports within a PVLAN.                                                                                           |
| Isolated    | An isolated port can ==only talk to promiscuous ports==. It has complete Layer 2 separation from other ports within the same PVLAN but not from promiscuous ports. PVLANs block traffic to isolated ports, except from promiscuous ports. |
| Community   | Community ports can ==talk to other community and promiscuous ports==. These interfaces are separated at Layer 2 from all other interfaces in other communities or isolated ports within their PVLAN.                                     |

It is important to remember that PVLANs can be susceptible to [[PVLAN Proxy Attacks]] due to the nature of PVLANs.

## PVLAN Example

The example in the image shows which ports can interconnect. The security provided by a PVLAN can be bypassed by using the router as a proxy.

![[PVLANs-20240302133502580.webp#invert]]

For example, in the image, PC-A and PC-B are isolated from each other. However, PC-A can initiate an attack against PC-B by sending packets that have the source IP address and MAC address of PC-A, the destination IP address of PC-B, but the destination MAC address of R1. 

S1 will forward the frame to R1 because F0/5 is configured as a promiscuous port. R1 rebuilds the frame with PC-B's MAC address and forwards it to S1. S1 then forwards the frame to PC-B.

*Note: PVLANs are used mainly in service provider co-location sites. Another typical application can be found in hotels where each room would be connected on its own isolated port.*

## PVLAN Edge

The use of the PVLAN Edge feature ensures that there is ==no exchange of unicast, broadcast, or multicast traffic== between PVLAN edge ports on the switch, as shown in the image. The PLVAN Edge feature is also called Protected Ports.

![[PVLANs-20240302134737106.webp#invert|300]]

The PVLAN Edge feature has the following characteristics:

| Feature                            | Description                                                                                                                                                                                                                                                                                                                                                                                                                  |
| ---------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Protected Port                     | A protected port ==does not forward any traffic==, including unicast, multicast, or broadcast, ==to any other port that is also a protected port==. Data traffic cannot be forwarded between protected ports at Layer 2; only control traffic is forwarded as these packets are processed by the CPU and forwarded in software. All data traffic passing between protected ports must be forwarded through a Layer 3 device. |
| Forwarding with Non-protected Port | Forwarding behavior between a protected port and a non-protected port proceeds as usual.                                                                                                                                                                                                                                                                                                                                     |
| Default Behavior                   | The default is to have no protected ports defined.                                                                                                                                                                                                                                                                                                                                                                           |

---

For PVLAN commands, click [[PVLAN Commands|here]].