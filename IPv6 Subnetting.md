---
tags:
  - "#Studies"
  - Networking
  - CCNA
  - Theory
aliases:
  - Internet Protocol version 6 Subnetting
description: IPv6 subnetting splits a large network into smaller segments using a prefix length.
---
IPv6 addresses are formed of three parts. Firstly, a *global routing prefix* as shown in the image below in blue. The second section is the *subnet identifier*, and is indicated in purple the diagram below. The final section is indicated in orange below, and is the *interface identifier* which is essentially the host portion of the address.

![[IPv6-20240227133603831.webp#invert]]

Indicated in white (or black if in light mode) is the ~~full~~ network portion of the address. This include the *global routing prefix* and the *subnet identifier*.

> [!note]-
> The address in the example above can be collapsed using the [[IPv6#IPv6 Notation Rules|notation rules]] below.

## Finding the IPv6 Prefix

Most IPv6 addresses will use a /64 prefix length as in the example in the previous section, however some will use other lengths. Here's how to find the sections of an address.

Take a /93 prefix length for example. As it says in [[Hexadecimal Notation]], each hexadecimal value pairing comes to 8 bits. Using this, we can continue to add the bits up until we reach the last network prefix.

![[IPv6-20240227135508648.webp#invert]]

In this example, the 93rd bit comes as the first bit in the hexadecimal `B`. Using this [[Hexadecimal Notation#Hex Lookup Table|lookup table]], we can see that hexadecimal `0B` is equal to decimal `11` (written in the example as `0d11`). 

This can be written as `1011` in binary (`0b1011` in the example above) Only the first bit of this binary value is part of the network prefix. Therefore we must set the remaining three to `0` resulting in binary `1000` (`0b1000` in the example).

This converts to decimal `8` (`0d8` in the example) which happens to convert to hexadecimal `08` too (`0x8` in the example). Therefore, as shown in the image, the network prefix is: `2001:DB8:8B00:1:FB89:178::/93`.