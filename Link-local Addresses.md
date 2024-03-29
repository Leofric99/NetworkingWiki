---
tags:
  - Studies
  - Networking
  - CCNA
  - Theory
description: An IPv6 unicast address that can be automatically configured on any interface that uses IPv6.
---
A Link-local [[IPv6]] address is a unicast IPv6 address which can be ==automatically configured== on any interface which has IPv6 enabled.

Link-local means that these addresses are *only* used for communication on ==one single link== (or subnet). Any routers, or layer three switches, will *not* route packets using these addresses. In this way, they can also be thought of as similar to the [[IPv4 Private Address Ranges]].

One use case for these addresses is the [[NDP]].

## Link-local Address Space

The address space used for Link-local addresses is the `FE80::/10` range. This is equivalent to `FE80::` to `FEBF:FFFF:FFFF:FFFF:FFFF:FFFF:FFFF:FFFF`.

*Note: The standards state that the 54 bits after the `FE80` should always be zero, so you won't see link-local addresses like: `FE9` or `FEA`. Only `FE8`.*

## Link-Local Address Generation

Link-local addresses will always begin with `FE8`, but the host portion of such an address will actually use [[EUI-64]] to generate to attempt to ensure unique addresses are used.