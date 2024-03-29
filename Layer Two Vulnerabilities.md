---
tags:
  - Studies
  - CyberSecurity
  - Theory
  - COM512
aliases:
  - Layer Two Weaknesses
description: The vulnerabilities associated with Layer two of the OSI Model.
---
Organisations regularly implement solutions to protect layer three and above through [[IPS]] devices, [[VPNs]], and so on, but layer two is arguably more important. This is because if layer two is compromised, all the layers above it are also compromised.

## Layer Two Switch Attacks

Security is only as strong as the weakest link in the system, and Layer 2 is considered to be that weakest link. Today, with [[BYOD]] and more sophisticated attacks, our LANs have become more vulnerable to penetration.

Attack types against the Layer 2 LAN infrastructure are highlighted in the table.

| Attack Type              | Description                                                                                                       |
| :----------------------- | :---------------------------------------------------------------------------------------------------------------- |
| [[MAC Table Attacks]]    | Includes MAC table overflow (also called MAC Address Flooding) Attacks.                                           |
| [[VLAN Attacks]]         | Includes VLAN hopping and VLAN double-tagging attacks. It also includes attacks between devices on a common VLAN. |
| [[DHCP Attacks]]         | Includes [[DHCP]] starvation and DHCP spoofing attacks.                                                           |
| [[ARP Spoofing Attacks]] | Includes ARP spoofing/ARP poisoning attacks.                                                                      |
| Address Spoofing Attacks | Includes MAC Address and IP address spoofing attacks prevented with [[IPSG]].                                     |
| [[STP Attacks]]          | Includes Spanning Tree Protocol manipulation attacks.                                                             |
## Cisco's Solutions

| Topic Title                                            | Topic Objective                                                                                                |
| ------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------- |
| [[Port Security Commands]]                             | Port security prevents many types of attacks including MAC table overflow attacks and DHCP starvation attacks. |
| [[DHCP Attacks#DHCP Attack Mitigation\|DHCP Snooping]] | DHCP Snooping prevents DHCP starvation and DHCP spoofing attacks by rogue DHCP servers.                        |
| [[DAI]]                                                | DAI prevents ARP spoofing and ARP poisoning attacks.                                                           |
| [[IPSG]]                                               | IP Source Guard prevents MAC and IP address spoofing attacks.                                                  |

The image below provides an overview of Cisco solutions that help mitigate Layer 2 attacks.

![[Layer Two Vulnerabilities-20240302115751276.webp#invert]]
