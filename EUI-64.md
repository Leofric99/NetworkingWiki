---
tags:
  - Studies
  - Acronym
  - Networking
  - CCNA
  - Theory
aliases:
  - Extended Unique Identifier 64
description: A method to automatically create a unique IPv6 interface identifier based on a device's MAC address.
---
EUI stands for Extended Unique Identifier. (Modified) EUI-64 is a method of converting a [[Studies/MAC|MAC Address]] into a 64-bit interface identifier (or the host portion of a /64 [[IPv6|IPv6 Address]]).

## How it Works

The process of how to convert between MAC and IPv6 using EUI-64 is detailed in this image, and explained below.

1. Divide the [[Studies/MAC|MAC Address]] *exactly* in half.
2. Insert `FFFE` into the middle of the MAC address.
3. Invert the 7th binary bit of the address (and convert it back to [[Hexadecimal Notation|hexadecimal]].

![[EUI-64-20240227150849077.webp#invert]]