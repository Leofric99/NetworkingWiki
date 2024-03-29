---
tags:
  - Studies
  - CyberSecurity
  - Theory
description: Exploit vulnerabilities in the DHCP protocol to compromise network integrity.
---
[[DHCP]] attacks involve exploiting vulnerabilities in the Dynamic Host Configuration Protocol to compromise network integrity

This is commonly done through techniques such as DHCP spoofing, where unauthorised devices attempt to assume the role of a legitimate DHCP server, leading to potential unauthorised access and traffic interception.

The two main types of DHCP attack are [[DHCP Starvation Attacks]], and [[DHCP Spoofing Attacks]].

## DHCP Attack Mitigation

It is easy to mitigate ==DHCP ~~starvation~~== attacks by using ==port security==. However, mitigating DHCP spoofing attacks requires more protection:

DHCP spoofing attacks can be mitigated using DHCP snooping on trusted ports. DHCP snooping ==builds and maintains== a DHCP snooping binding ==database== that the switch can use to filter DHCP messages from untrusted sources.

Devices under your administrative control, such as switches, routers, and servers, are trusted sources. Any device beyond the firewall or outside your network is an untrusted source. In addition, all access ports are generally treated as untrusted sources. The image below shows an example of trusted and untrusted ports.

![[DHCP Attacks-20240302141735650.webp#invert]]

> [!note]
> In a large network, the DHCP binding table may take time to build after it is enabled. For example, it could take 2 days for DHCP snooping to complete the table if DHCP lease time is 4 days.

When DHCP snooping is enabled on an interface or VLAN, and a switch receives a packet on an untrusted port, the switch ==compares the source packet== information with that held in the DHCP ==snooping binding table==. The switch will deny packets containing specific information:

- Unauthorised DHCP server messages from an untrusted port.
- Unauthorised DHCP client messages not adhering to the snooping binding table or rate limits.
- DHCP relay-agent packets that include option-82 information on an untrusted port.

To counter Gobbler using the same MAC address, DHCP snooping also makes the switch check the [[CHADDR]] field in the DHCP request. 

This ensures that it matches the hardware MAC address in the DHCP snooping binding table and the MAC address in the MAC table. If there is no match, the request is dropped.

Similar mitigation techniques are available for DHCPv6 and IPv6 clients. Because IPv6 devices can also receive their addressing information from the router’s Router Advertisement (RA) message, there are also mitigation solutions to prevent any rogue RA messages.

To see the implementation and configuration of DHCP Snooping, click [[DHCP Commands#Configuring DHCP Snooping|here]].