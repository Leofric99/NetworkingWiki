---
tags:
  - Studies
  - Acronym
  - Networking
  - CCNA
  - Theory
  - COM412
aliases:
  - Address Resolution Protocol
description: Resolves MAC addresses from known IP addresses.
---

ARP Stands or the ==Address Resolution Protocol==, and was designed to resolve [[Studies/MAC]] from known [[IPv4]] or [[IPv6]] addresses. ARP was defined in 1982 in the IETF's RFC826 and can be found in this PDF: [[IETF RFC826.pdf]].

## Packet Types

ARP only uses ==two packet types==:

- ARP Request
- ARP Reply

ARP ==Requests are broadcasts==, and are sent to every device in the subnet whereas ARP ==Replies are targeted unicast== messages from device(s) that received the ARP Request back to the device that sent the ARP Request with the associated [[Studies/MAC|MAC Address]].

For ARP Commands, click [[ARP Commands|here]].

