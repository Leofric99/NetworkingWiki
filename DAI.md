---
tags:
  - Studies
  - CyberSecurity
  - Acronym
  - Theory
aliases:
  - Dynamic ARP Inspection
  - Dynamic Address Resolution Protocol Inspection
description: Prevents ARP spoofing and ARP poisoning attacks.
---
Dynamic ARP Inspection (DAI) prevents ARP spoofing and ARP poisoning attacks.

In a typical [[ARP Spoofing Attacks|ARP Spoofing Attack]], a threat actor can send unsolicited [[ARP]] requests to other hosts on the subnet with the MAC Address of the threat actor and the IP address of the default gateway. To prevent ARP spoofing and the resulting ARP poisoning, a switch must ensure that only valid ARP Requests and Replies are relayed.

Dynamic ARP inspection (DAI) requires [[DHCP Attacks#DHCP Attack Mitigation|DHCP Snooping]] to be enabled and helps prevent ARP attacks by:

- Not relaying invalid or gratuitous ARP Requests out to other ports in the same VLAN
- Intercepting all ARP Requests and Replies on untrusted ports
- Verifying each intercepted packet for a valid IP-to-MAC binding
- Dropping and logging ARP Requests coming from invalid sources to prevent ARP poisoning
- Error-disabling the interface if the configured DAI number of ARP packets is exceeded

## Implementation Guidelines

To mitigate the chances of ARP spoofing and ARP poisoning, follow these DAI implementation guidelines:

- Enable [[DHCP Attacks#DHCP Attack Mitigation|DHCP Snooping]] globally.
- Enable DHCP snooping on selected [[VLANs]].
- Enable DAI on selected VLANs.
- Configure trusted interfaces for DHCP snooping and [[ARP]] inspection.

It is generally advisable to configure all access switch ports as untrusted and to configure all uplink ports that are connected to other switches as trusted.

The sample topology in the image identifies trusted and untrusted ports.

![[DAI-20240302155025714.webp#invert|500]]

For the DAI Commands, click [[ARP Commands#DAI Commands|here]].