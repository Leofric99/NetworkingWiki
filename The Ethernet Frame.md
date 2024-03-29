---
tags:
  - Studies
  - Networking
  - CCNA
  - Theory
  - COM412
description: A standardised data packet format used for communication in computer networks.
---

Here is a representation of the Ethernet Frame. This Ethernet Frame is broken down into The Ethernet Header, the Packet, and the Ethernet Trailer. The maximum size for any ethernet frame is 1500 bytes which is it's [[MTUs|MTU]].

![[Pasted image 20240206161432.png#invert]]
## The Ethernet Header

There are ==five== different fields in the Ethernet Header. Note the lengths in bytes of each section. This is important to know.
## Preamble 

- 7 bytes long
- 56 bits long
- It allows devices to ==synchronise their clocks==.
## SFD

- 1 byte long
- 8 bits long
- Start Frame Delimiter. 
- ==Indicates the end of the Preamble== and the beginning of the rest of the frame.
## Destination

- 6 bytes long
- 48 bits long
- The destination device [[Studies/MAC|MAC Address]].
## Source

- 6 bytes long
- 48 bits long
- The source device [[Studies/MAC|MAC Address]].
## Type (or length)

- 2 bytes long
- 16 bits long
- ==Identifies== the layer three ==protocol== used in the enclosed packet.
- If length, it details the length of the encapsulated data.

## The Ethernet Trailer

## FCS (The only trailer field)

- 4 bytes long
- Used to ==ensure that there are no errors== in the data.
- Runs a CRC, or Cyclic Redundancy Check, on the frame to do this.