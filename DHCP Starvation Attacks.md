---
tags:
  - Studies
  - CyberSecurity
  - Theory
description: An attack which prevents new clients from connecting to a network.
---
The goal of the [[DHCP]] starvation attack is [[DoS Attacks|DoS]] for connecting clients. DHCP starvation attacks require an attack tool such as Gobbler. 

Gobbler has the ability to look at the entire scope of leasable IP addresses and tries to lease them all. Specifically, it creates DHCP discovery messages with bogus MAC addresses.