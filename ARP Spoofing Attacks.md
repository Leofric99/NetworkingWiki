---
tags:
  - Studies
  - CyberSecurity
  - Theory
description: An attack which involves sending false ARP packets.
aliases:
  - ARP Poisoning Attacks
---
Any client on a network is allowed to send an unsolicited [[ARP]] Request called a ==gratuitous ARP==. When a host sends a gratuitous ARP, other hosts on the subnet store the MAC address and IPv4 address contained in the gratuitous ARP in their ARP tables.

The problem is that an attacker can send a gratuitous ARP message containing a ==spoofed MAC address== to a switch, and the switch would update its MAC table accordingly. Therefore, any host can ==claim to be the owner of any IP and MAC address== combination they choose with the possibility of creating a [[MITM Attacks|MITM Attack]].

> [!example]-
> To begin with each device has an accurate MAC table with the correct IPv4 and MAC addresses for the other devices on the LAN.
> 
> The threat actor then sends two spoofed gratuitous ARP Replies in an attempt to replace R1 as the default gateway:
> 1. The first one informs all devices on the LAN that the threat actor’s MAC address (CC:CC:CC) maps to R1’s IPv4 address, 10.0.0.1.
> 2. The second one informs all devices on the LAN that the threat actor’s MAC address (CC:CC:CC) maps to PC1’s IPv4 address, 10.0.0.11.
>    
>![[ARP Spoofing Attacks-20240302145828680.webp#invert|590]]
>
>R1 and PC1 will remove their correct entry for each other’s MAC address and replace it with PC2’s MAC address. The threat actor has now poisoned the ARP caches of all devices on the subnet.

Luckily, ARP Spoofing/Poisoning attacks can be mitigated by using [[DAI]] or [[IPSG]].