---
tags:
  - Studies
  - CyberSecurity
  - Theory
aliases:
  - MAC Address Flooding
  - Media Access Control Flooding
description: A layer two network attack technique which works by feeding fake MAC addresses to a Switch.
---
All ==MAC tables have a fixed size== and consequently, a switch can run out of resources in which to store [[Studies/MAC|MAC Addresses]]. 

MAC address flooding attacks ==take advantage of this limitation== by bombarding the switch with fake source MAC addresses until the switch MAC address table is full.

## How it Works

When a threat actor bombards the switch with fake MAC Addresses the Switch's MAC table will become saturated.

Once this occurs, the Switch will begin to treats ~~any~~ new frames as unknown unicast addresses which it will flood out of all interfaces which the threat actor can pick up using packet sniffers.

The image below shows how a threat actor can easily use the network attack tool `macof` to overflow a MAC address table.

![[MAC Table Attacks-20240302120703883.webp#invert]]

> [!note]-
> The frames being flooded could only be from the same [[LANs|LAN]] or [[VLANs|VLAN]].

1. The threat actor is connected to VLAN 10 and uses `macof` to rapidly generate many random source and destination MAC and IP addresses.
   
2. Over a short period of time, the switch’s MAC table fills up.
   
3. When the MAC table is full, the switch begins to flood all frames that it receives. As long as `macof` continues to run, the MAC table remains full and the switch continues to flood all incoming frames out every port associated with VLAN 10.
   
4. The threat actor then uses packet sniffing software to capture frames from any and all devices connected to VLAN 10.

> [!note] 
> If the threat actor stops `macof` from running or is discovered and stopped, the switch eventually ages out the older MAC address entries from the table and begins to act normally again.

## Attack Mitigation

To mitigate MAC address table overflow attacks, network administrators must implement [[Port Security Commands|port security]]. Port security will only allow a specified number of source MAC addresses to be learned on the port. Port security is further discussed later in this module.