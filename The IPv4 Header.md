---
tags:
  - Studies
  - Networking
  - CCNA
  - Theory
  - COM412
description: Contains essential information such as source and destination IP addresses, protocol version, time-to-live, and control flags.
---

The header of an IPv4 packet has many fields. See [[IPv4]] for a detailed table of all of these fields. The image below details an overview of these header fields. In this note, these fields will be detailed in depth.

![[IPv4-20240210132630442.webp#invert]]

## Version

The version field is ==four bits long==. It is used to identify the ==IP version== that is in use. The only two IP versions in use are: [[IPv4]] and [[IPv6]]. [[IPv4]] is denoted by decimal `4` or binary `0100` whereas [[IPv6]] is denoted by decimal `6`, binary `0110`.

## Internet Header Length (IHL)

The IHL field is also ==four bits long==. It specifies the ==total length of the header== only. This is required for the [[IPv4]] header as the options field near the end of the header is variable in length. Without this, the device would not know where to terminate reading the header.

It will specify the length of the header in ==4 byte increments==. Therefore if the length of the header is 20 bytes, this field will indicate that by using a decimal `5` or binary `0101` which also happens to be the minimum value within this field (without an options field at all). The maximum value is `15` which would equal 60 bytes.

## Differentiated Services Code Point (DSCP)

The DSCP field is ==six bits long== and is used for [[QoS|Quality of Service]] and is used for determining the ==priority== of the packet as it travels over the network.

## Explicit Congestion Notification (ECN)

The ECN field is ==two bits long==. It provides end to end ==notification of network congestion== *without* dropping packets unlike traditional methods which detect congestion through dropped packets. This field is optional, and will only be present if both ends support it.

## Total Length

The Total Length field is ==sixteen bits long==. It indicates the ==entire length of the packet== including the packet header, and the layer four segment within. Unlike the IHL field, it identifies the length ==in one byte increments== rather than four byte increments. The minimum value of this field is `20` bytes the maximum value for this field is `65535` bytes.

## Identification

The Identification field is ==sixteen bits long==. If a packet is fragmented, this field  ==identifies which packet the fragment belongs to==. All fragments of the same packet will have their own header with the same value in this field. Fragments are created if the packet to be sent exceeds the [[MTUs|MTU]]. These fragments are then re-assembled by the receiving host.

## Flags

The Flag field is ==three bits long== and is used to ==control and identify fragments==. The three bits are set out as follows:

- **Bit 0** is reserved and is always zero.
- **Bit 1** is the DF Bit. This is used to identify a packet which should not be fragmented.
- **Bit 2** is the MF Bit. This is set to 1 if there are more fragments to follow, or 0 if this is the last *or only* bit.

## Fragment Offset

The Fragment Offset field is ==thirteen bits long== and is used to ==indicate the position of the fragment== within the wider unfragmented packet which would allow the fragment to be put back into the correct order if they arrive out of sequence.

## Time to Live (TTL)

The Time to Live (TTL) field is ==eight bits long==. This field is used to ==prevent packets infinitely looping== around networks. The recommended default value is `64`.

A Router or Multi-layer Switch will drop any packet with a TTL of `0`. Originally the TTL field was designed to indicate the packet's lifetime in seconds, but in practice, this ==indicates the remaining hop count==. Each time a router receives the packet, it will reduce the TTL value by 1.

## Protocol

The Protocol field is ==eight bits long==, and it ==identifies the protocol in use== in by the encapsulated layer four [[PDUs|PDU]]. This will most likely either be [[TCP]] or [[UDP]], but it can be other values. For the CCNA, the ones you need to learn are in the table below.

| Protocol | Field Value |
|:---------|:------------|
| [[TCP]]  | `6`         |
| [[UDP]]  | `17`        |
| [[ICMP]] | `1`         |
| [[OSPF]] | `89`        |  
To find a list of other values in this field, there is a Wikipedia page here: [List of IP protocol numbers - Wikipedia](https://en.wikipedia.org/wiki/List_of_IP_protocol_numbers)
## Header Checksum

The Header Checksum field is ==sixteen bits long==, and will ==reveal any errors== in the [[IPv4]] header. This field is assigned a value on creation based on a calculation. On arrival, the router or host processes this calculation again, and compares the result to the one stated in this field. If there are errors in the packet, the result will not be the same and the packet will be dropped.

This ==will not identify errors in the other layers==. Only IPv4. Errors in the other layers are handled in a different way. [[TCP]] and [[UDP]] in particular have their own checksums.

## Source IP Address & Destination IP Address

The Source IP Address field, and the Destination IP Address field, are ==both 32 bits long==. The source IP Address is the [[IPv4]] address of the sender, and the Destination IP Address is the [[IPv4]] address of the intended recipient.

## Options

The Options field is **optional** and can be ==between zero, and 320, bits long==. This field is rarely used, however, if [[The IPv4 Header#Internet Header Length (IHL)]] field has a value larger than `5` it is in use and options are present. No options are required to be memorised for the CCNA.

