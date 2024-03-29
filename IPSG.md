---
tags:
  - Studies
  - CyberSecurity
  - Acronym
  - Theory
aliases:
  - IP Source Guard
  - Internet Protocol Source Guard
description: Prevents MAC and IP address spoofing attacks.
---
IP Source Guard (IPSG) prevents MAC spoofing attacks, like [[ARP Spoofing Attacks|ARP Poisoning]], and IP spoofing attacks which are harder to prevent. It does this by dynamically maintains [[PVACLs]].

## How it Works

IPSG operates in a similar way to [[DAI]], but it inspects every single packet, not just [[ARP]] ones. Also similarly to DAI, IPSG requires that [[DHCP Attacks#DHCP Attack Mitigation|DHCP Snooping]] be enabled. IPSG is deployed on ~~untrusted~~ Layer 2 access and trunk ports.

Initially, *all* IP traffic on the port is blocked, except for DHCP packets that are captured by the DHCP snooping process. A [[PVACLs|PVACL]] is installed on the port when a client receives a valid IP address from the DHCP server or when a static IP source binding is configured by the admin.

This process ==restricts the client IP== traffic to those source IP addresses that are configured in the binding. Any IP traffic with a source IP address other than that in the IP source binding will be ==filtered out==. This filtering limits the ability of a host to attack the network by claiming the IP address of a neighbour host.

For each untrusted port, there are two possible levels of IP traffic security filtering:

| Level                            | Description                                                                                                                                                                                                                                        |
| -------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Source IP address filter         | IP traffic is filtered based on its ==source IP address==, allowing only traffic with a source IP address matching the IP source binding entry to be permitted. Adjustments are automatic when creating or deleting IP source entries on the port. |
| Source IP and MAC address filter | IP traffic is filtered based on ==both source IP address and MAC address==, permitting only traffic with matching IP source and MAC addresses. Adjustments are automatic to reflect changes in the IP source binding entry on the port.            |

Click [[IPSG Commands|here]] for IPSG Commands.