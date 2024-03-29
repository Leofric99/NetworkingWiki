---
tags:
  - Studies
  - Acronym
  - Networking
  - CCNA
  - Theory
aliases:
  - Unique Local Addresses
  - Unique Local Address
description: An IPv6 address which cannot be routed over the internet.
---
ULAs are Unique Local Addresses. A form of [[IPv6]] address which cannot be routed over the public internet similar to [[IPv4 Private Address Ranges]].

ULAs, unlike [[GUAs]], don't need to be registered with a [[RIRs|RIR]] to be used and therefore *may* not be unique, but as they aren't routed globally, this doesn't matter.

The address space reserved for these addresses is: `FC00::/7` which is the range: `FC00::` to `FDFF:FFFF:FFFF:FFFF:FFFF:FFFF:FFFF:FFFF`. There is an example below.

![[ULAs-20240227152430337.webp#invert]]

The Global ID should be unique so that addresses don't overlap when companies merge.