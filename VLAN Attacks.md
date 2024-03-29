---
tags:
  - Studies
  - CyberSecurity
  - Theory
aliases:
  - Virtual LAN Attacks
  - Virtual Local Area Network Attacks
description: An attack which enables traffic from one VLAN to be seen by another VLAN without the aid of a router.
---
[[VLANs]] are used to create separate broadcast domains on switches. Endpoints that are located in one VLAN are unable to communicate with endpoints that are on another VLAN unless permitted to do so by a router or Layer 3 switch.

A VLAN hopping attack enables traffic from one VLAN to be seen by another VLAN ==without a router==. 

## How it Works

In a basic VLAN hopping attack, the threat actor configures a ==host to act like a switch== to take advantage of the ==automatic trunking== port feature enabled by default on most switch ports.

The threat actor configures the host to spoof [[Trunking#IEEE 802.1Q|802.1Q]] signalling and [[DTP]] signalling to trunk with the connecting switch. If successful, the switch ==establishes a trunk link== with the host, as shown in the image. 

![[VLAN Attacks-20240302131600676.webp#invert]]

Now the threat actor can access all the VLANs on the switch. The threat actor can send and receive traffic on any VLAN, effectively hopping between VLANs. This can lead on to other forms of attack such as [[VLAN Double-Tagging Attacks]].

## Mitigating VLAN Attacks

The following steps can be taken to mitigate [[VLANs|VLAN]] attacks. See [[VLAN Commands#Trunking Configuration]] for the commands.

1. Disable [[DTP]] (auto trunking) negotiations on non-trunking ports by using the `switchport mode access` interface configuration command.
   
2. Disable unused ports and put them in an unused VLAN. In the example it is VLAN 1000.
   
3. Manually enable the trunk link on a trunking port by using the `switchport mode trunk` command.
   
4. Disable [[DTP]] (auto trunking) negotiations on trunking ports by using the `switchport nonegotiate` command.
   
5. Set the native VLAN to a VLAN other than VLAN 1 by using the `switchport trunk native vlan {vlan_number}` command.