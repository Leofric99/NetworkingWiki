---
tags:
  - Studies
  - CyberSecurity
  - Theory
aliases:
  - Private VLAN Proxy Attacks
description:
---
A [[PVLANs|PVLAN]] Proxy attack involves exploiting vulnerabilities in the configuration of PVLANs to ==gain unauthorised access or intercept traffic== within a network. 

## How it Works

During a PVLAN Proxy attack, an attacker gains access to a [[PVLANs#Port Types|promiscuous port]] or somehow manipulates the network to behave as if they have Promiscuous port privileges.

![[PVLAN Proxy Attacks-20240302134131278.webp#invert]]

Once the ==attacker gains access to the Promiscuous port== or mimics its behaviour, they can effectively eavesdrop on the communication between Isolated and Community ports within the PVLAN. This compromises the intended isolation and security provided by the PVLAN architecture.

## Mitigating PVLAN Attacks

To mitigate this type of attack, configure an ACL that will deny traffic with a source and destination IP address that belongs to the same subnet, as shown in in the configuration below.

```
R1(config)# ip access-list extended PVLAN
R1(config-ext-nacl)# deny ip 172.16.0.0 0.0.0.255 172.16.0.0 0.0.0.255  
R1(config-ext-nacl)# permit ip any any
R1(config-ext-nacl)# interface g0/0
R1(config-if)# ip access-group PVLAN in
```