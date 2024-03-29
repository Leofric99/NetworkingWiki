---
tags:
  - Studies
  - CyberSecurity
  - Acronym
  - Theory
  - COM512
aliases:
  - Adaptive Security Appliances
description: A network security device which provides firewall, intrusion prevention, VPN (Virtual Private Network), and other security features.
---
Adaptive Security Appliances (ASAs) are network security devices ==developed by Cisco== that provides [[Firewalls]], [[IPS]], [[VPNs|VPN]], and other [[ASA Features]]. 

ASAs are typically used by organisations to protect their networks from unauthorised access, malware, and other cyber threats. Cisco's ASA Firewall models are [[Cisco Firepower Series]].

## ASA Deployment

When deploying ASAs on a network, there are three considerations:

- Where you place them (see [[Layered Network Defences]] and [[ASA Implementation]]).
- What [[ASA Modes of Operation|mode]] you operate them in.

## Security Levels

The ASA ==assigns== security ==levels== to distinguish between inside and outside networks. Security levels define the level of ==trustworthiness of an interface==. The higher the level, the more trusted the interface (from `0` to `100`).

When traffic moves from an interface with a higher security level to an interface with a lower security level, it is considered outbound traffic. Conversely, traffic moving from an interface with a lower security level to an interface with a higher security level is considered inbound traffic. An example design can be seen below.

> [!example]-
> ![[ASAs-20240314140921938.webp#invert|590]]

Security levels help to control many aspects of network traffic as shown in the table below.

| **Aspect**            | **Effect**                                                                                                                                                                                                                                                                                                                                                                                                      |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Network Access        | By default, there is an implicit permit from a higher security interface to a lower security interface (outbound). Hosts on the higher security interface can access hosts on a lower security interface. Multiple interfaces can be assigned the same security level. If communication is enabled for interfaces with the same security level, there is an implicit permit for traffic between the interfaces. |
| Inspection Engines    | Some application inspection engines are dependent on the security level. When interfaces have the same security level, the ASA inspects traffic in either direction.                                                                                                                                                                                                                                            |
| Application Filtering | HTTPS and FTP filtering applies only for outbound connections that are from a higher level to a lower level. If communication is enabled for interfaces with the same security level, traffic can be filtered in either direction.                                                                                                                                                                              |
## Inbound/Outbound Traffic Rules

This list outlines default traffic behaviour in Cisco ASA firewalls, covering outbound and inbound traffic policies as well as exceptions requiring [[ACLs|ACL]] configurations.

1. Outbound traffic is allowed and inspected ==by default==.
2. Returning traffic is permitted due to stateful packet inspection, facilitating internal access to [[DMZ]] resources and internet connectivity without extra commands.
3. By default, inbound traffic from the outside to the DMZ or inside is denied, while return traffic from the inside to outside is allowed.
4. Exceptions demand [[ACLs|ACL]] configuration to permit traffic from lower security level interfaces to higher ones, like outside to inside.

## ASA Commands

For ASA Commands, see [[ASA Commands]], or to lean how to implement the ASA Commands, see [[ASA Configuration]].