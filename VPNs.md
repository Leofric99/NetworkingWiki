---
tags:
  - Studies
  - Acronym
  - Networking
  - CCNA
  - Theory
  - CyberSecurity
  - COM512
  - COM515
aliases:
  - Virtual Private Networks
  - VPN
description: Encrypts internet traffic and hides device locations, making connections secure and private.
---
A VPN is virtual in that it carries information within a ==private network==, but that information is actually ==transported over a public network==. A VPN is private in that the traffic is encrypted to keep the data confidential while it is transported across the public network.

This image shows a collection of various types of VPNs managed by an enterprise’s main site. The tunnel enables remote sites and users to access the main site’s network resources securely:

![[VPNs-20240318115317152.webp#invert]]

## Benefits of using a VPN

Modern VPNs now support encryption features, such as [[IPSec]] and [[SSL]] to secure network traffic between sites. Major benefits of VPNs are shown in the table.

| **Benefit**       | **Description**                                                                                                                                                                                                                                    |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Cost Savings**  | With the advent of cost-effective, high-bandwidth technologies, organisations can use VPNs to ==reduce their connectivity costs== while simultaneously increasing remote connection bandwidth.                                                     |
| **Security**      | VPNs provide the ==highest level of security== available, by using advanced encryption and authentication protocols that protect data from unauthorised access.                                                                                    |
| **Scalability**   | VPNs allow organisations to use the internet, making it easy to add new users without adding significant infrastructure.                                                                                                                           |
| **Compatibility** | VPNs can be implemented across a wide variety of [[WANs\|WAN]] link options including all the popular broadband technologies. Remote workers can take advantage of these high-speed connections to gain secure access to their corporate networks. |
## VPN Topologies

VPNs are commonly deployed in ~~one~~ of two VPN Topologies. Either [[Site-to-Site VPNs]], or [[Remote Access VPNs]].

## IPSec

[[IPSec]] is an IETF standard (RFC 2401-2412) that defines how a VPN can be secured across IP networks. IPsec protects and authenticates IP packets between source and destination. IPsec can protect traffic from Layer 4 through Layer 7.