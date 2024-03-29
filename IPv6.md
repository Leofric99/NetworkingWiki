---
tags:
  - Studies
  - Acronym
  - Networking
  - Theory
  - CCNA
  - COM412
aliases:
  - Internet Protocol version 6
description: The latest version of the Internet Protocol that provides a larger address space compared to its predecessor, IPv4.
---
IPv6 (Internet Protocol version 6), is the latest version of the Internet Protocol that provides a large address space. Before IPv6, there was IPv4 (and later [[ISP]] which was never publicly released).

An IPv6 address is ==128 bits== in length, and is written as 32 [[Hexadecimal Notation|hexadecimal]] characters divided into eight groups of four using colons such as in the following example:


![[IPv6-20240227133322411.webp#invert|600]]

IPv6 subnets can be very simple when an IPv6 address uses a `/64` prefix length, however it's not always so simple. To find out how to subnet IPv6 networks, click [[IPv6 Subnetting|here]].

For the Cisco IOS IPv6 Commands, click [[IPv6 Commands|here]].
## Why Was IPv6 Needed?

IPv6 was introduced to combat the issue of dwindling availability of [[IPv4]] addresses. When IPv4 was being developed, the creators never thought that the internet would be as big as it is today.

IPv4 was adjusted to be less wasteful with the introduction of [[VLSM]], but this only provided a short-term solution; the long-term solution is IPv6.

## IPv6 Notation Rules

To make IPv6 easier to read and understand, there are a couple of notation rules which you must know about.

1. ==Leading zeros== in each group of four hexadecimal values can be removed.

2. Any consecutive groups of ==four [[Hexadecimal Notation|hexadecimal]] zeros== can be collapsed into a single double colon '::', however this can only be done *once* per address.

## IPv6 Address Types

There are several methods of obtaining an IPv6 address, and different IPv6 address types. For example [[EUI-64]] uses the device's MAC address, then there are [[GUAs]], [[ULAs]], and [[Link-local Addresses]]. It is important to know the basics of these four when taking the CCNA.

There are also other descriptors for IPv6 addresses as follows:

- Unicast Addresses - One to one addresses. One source and one destination.
- Broadcast Addresses - One to all. One source, to all destinations (on the network).
- [[IPv6 Multicast Addresses|Multicast Addresses]]
- [[IPv6 Anycast Addresses|Anycast Addresses]]