---
tags:
  - Studies
  - CyberSecurity
  - Acronym
  - Theory
---
Host-based [[IPS]] (HIPS) is software installed on a host to monitor and analyse suspicious activity, offering advantages like monitoring critical system processes specific to the host. One example of a HIPS is Windows Defender.

## Pros and Cons of HIPS

#### Pros
Functioning as a ==blend of antivirus, antimalware, and firewall==, they provide comprehensive protection for the host. 

When paired with a [[NIPS|network-based IPS]], HIPS effectively prevents unauthorised commands, registry updates, system directory changes, installation programs, buffer overflows, and monitors network traffic to thwart [[DoS Attacks|denial-of-service attacks]] or illicit FTP sessions.

#### Cons
A disadvantage of HIPS is that it operates ==only at a local level==. It does not have a complete view of the network, or coordinated events that might be happening across the network. To be effective in a network, HIPS must be installed on every host and have support for every operating system.