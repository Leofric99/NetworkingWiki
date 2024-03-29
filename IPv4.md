---
tags:
  - Studies
  - Acronym
  - Networking
  - CCNA
  - Theory
  - COM412
description: The fourth version of the Internet Protocol serving as the foundation for most internet communication.
aliases:
  - Internet Protocol version 4
---

Internet Protocol version 4 (IPv4) is the fourth version of the Internet Protocol (IP), which identifies devices on a network through an addressing system. It uses ==32-bit addresses==, which limits the number of unique hosts to approximately 4.3 billion.

IPv4 operates at layer three of the [[The OSI Model]]. 

## The IPv4 Packet

IPv4 has an extensive header field, but unlike [[The Ethernet Frame]], it has no trailer.

| Field                | Octet(s) | Bit Position        | Description                                       |
|----------------------|----------|---------------------|---------------------------------------------------|
| Version              | 1        | 0-3                 | IPv4 protocol version (usually 4)                |
| IHL (Header Length)  | 1        | 4-7                 | Length of the header in 32-bit words              |
| DSCP (Differentiated Services Code Point) | 1 | 8-13         | Differentiated services in use for packet         |
| ECN (Explicit Congestion Notification)      | 1 | 14-15        | Indicates congestion in the network               |
| Total Length         | 2-3      | 16-31               | Total length of the packet (header + data)        |
| Identification       | 4-5      | 32-47               | Used for uniquely identifying fragments of a packet|
| Flags                | 6        | 48-50               | Control flags for fragmentation                   |
| Fragment Offset      | 6-7      | 51-63               | Indicates where in the datagram this fragment belongs|
| Time to Live (TTL)   | 8        | 64-71               | Maximum number of hops before packet is discarded |
| Protocol             | 9        | 72-79               | Protocol used in the data portion of the packet   |
| Header Checksum      | 10-11    | 80-95               | Error-checking for the header                     |
| Source IP Address    | 12-15    | 96-127              | Sender's IP address                               |
| Destination IP Address | 16-19  | 128-159             | Receiver's IP address                             |
| Options (if any)     | 20+      | 160+                | Variable-length field, may include options         |
| Padding (if needed)  | Variable | Variable            | Padding to ensure the header is a multiple of 32 bits|

For more information about the IPv4 Header, see [[The IPv4 Header]].

## IPv4 Address Composition

IPv4 addresses follow a standard format of ==four 'octets' at 8 bits each==. Each one of these octets is a number which can range from 0 to 255 such as the following example: `192.168.0.254`. ==Two IPv4 addresses within a range can never be used for hosts== as they are reserved. The first address within any network (`.0` in `/24` networks) is the address of the network as a whole. The last address in the range is known as the broadcast address (`.255` in `/24` networks) which will send an IP packet to all devices within the network.

## Decimal & Binary Conversion

To convert IPv4 addresses into binary, and vice versa visit: [[Decimal & Binary Conversion|The Decimal & Binary Conversion Table]]. For this IPv4 address this address would be as follows:

`11000000 10101000 00000000 11111110`

==Binary is base 2== meaning that each digit increases by a factor of two, but strangely from right to left. 

In the following example, I have converted the binary value of 10010110 into decimal. To calculate the value of each number in the binary value, you must multiply it by a factor. This factor begins on the right of the binary value as 1, and increases by a factor of two as it progresses towards the left.

| Binary Value | Multiplier (doubles each time) | Result |
| :--- | :--- | :--- |
| 0 | x1 | 0 |
| 1 | x2 | 2 |
| 1 | x4 | 4 |
| 0 | x8 | 0 |
| 1 | x16 | 16 |
| 0 | x32 | 0 |
| 0 | x64 | 0 |
| 1 | x128 | 128 |

The end result can be found by adding up all of the values in the result column which in this case results in 150.

## Address Classes

There are five classes of IPv4 addresses. This is a legacy method of classing IPv4 addresses, and is not typically used anymore.

The table below shows the five classes of IPv4 addresses. Note that in the binary column, the numbers are fixed, and the 'X' represents any value.

| Class | CIDR | First Octet (Binary) | First Octet (Decimal) | Address Range |
| :--- | :--- | :--- | :--- | :--- |
| A | /8 | 0XXXXXXX | 0 - 127 | 0.0.0.0 - 127.255.255.255 |
| B | /16 | 10XXXXXX | 128 - 191 | 128.0.0.0 - 191.255.255.255 |
| C | /24 | 110XXXXX | 192 - 223 | 192.0.0.0 - 191.255.255.255 |
| D | N/A | 1110XXXX | 224 - 239 | 224.0.0.0 - 239.255.255.255 |
| E | N/A | 1111XXXX | 240 - 255 | 240.0.0.0 - 255.255.255.255 |
Only ranges A, B, and C can be assigned to devices. This is because classes D, and E, have special purposes.

IP Address addresses and ranges are assigned by [[IANA]].

## CIDR Notation

Slash (AKA CIDR) Notation ==identifies== which section of the IPv4 address is the ==network portion==, and which section is the ==host portion== of the address. It was introduced by the [[IETF]] in 1993 to replace the wasteful [[IPv4#Address Classes]].

The most common for home networks is `/24`. This means that the first 24 binary bits are reserved for the network leaving the remaining octet (8 bits) free to identify the host within that network.

## Subnet Masks

Subnet masks do much the ==same as slash notation==. It identifies the network and host sections of an IPv4 address. The simple way to think of subnet masks are just another way of writing the slash notation.

If you imagine a slash notation of `/24`. This identifies that the first 24 bits are reserved for the Network. We will assign reserved values the binary 1. The rest are free for the host so we will assign them 0. Therefore the subnet mask will be `11111111.11111111.11111111.00000000` or `255.255.255.0`.