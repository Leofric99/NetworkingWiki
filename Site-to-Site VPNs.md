---
tags:
  - "#Studies"
  - Networking
  - CCNA
  - Theory
aliases:
  - Site-to-Site Virtual Private Networks
description: "[[VPNs]] which create secure tunnels for remote office sites to connect to other site networks privately and securely."
---
Site-to-site VPNs are used to connect networks across another untrusted network such as the internet. 

In a site-to-site VPN, end hosts send and receive normal unencrypted TCP/IP traffic through a VPN-terminating device. The VPN-terminating device is typically called a VPN gateway.

![[Site-to-Site VPNs-20240318125644990.webp#invert]]

The VPN ==gateway encapsulates and encrypts== outbound traffic. It then sends the traffic through a VPN tunnel over the internet to a VPN gateway at the target site. 

Upon receipt, the receiving VPN gateway strips the headers, decrypts the content, and relays the packet toward the target host inside its private network.

Site-to-site VPNs are typically created and secured using [[IPSec]].