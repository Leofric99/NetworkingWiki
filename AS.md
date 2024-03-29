---
tags:
  - Studies
  - Acronym
  - Networking
aliases:
  - Autonomous System
  - Autonomous Systems
description: A large network or group of networks that has a unified routing policy.
---
An autonomous system (AS) is a large network or group of networks that has a unified routing policy. These autonomous systems are usually large organisations, ISPs, etc.

Imagine an AS as being like a town's post office. Mail goes from post office to post office until it reaches the right town, and that town's post office will then deliver the mail within that town. Similarly, packets cross the Internet by hopping from AS to AS until they reach the AS that contains their destination [[IPv4]] or [[IPv6]] address. Routers within that AS send the packet to the correct address.

Every AS controls a specific set of IP addresses, just as every town's post office is responsible for delivering mail to all the addresses within that town. The range of IP addresses that a given AS has control over is called their "IP address space."

Most ASes connect to several other ASes. If an AS connects to only one other AS and shares the same routing policy, it may instead be considered a subnetwork of the first AS.

Typically, each AS is operated by a single large organisation, such as an Internet service provider (ISP), a large enterprise technology company, a university, or a government agency.