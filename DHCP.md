---
tags:
  - Studies
  - Acronym
  - Networking
  - CCNA
  - Theory
  - COM414
aliases:
  - Dynamic Host Configuration Protocol
description: A protocol which automatically assigns IP addresses and other network settings to devices on a network.
---
Dynamic Host Configuration Protocol (DHCP), automatically manages IP address assignment and other network settings for devices on a network. This eliminates the need for manual configuration for each device.

## How it Works

When a client device connects to a new network, unless it has been statically configured with an IP address, subnet mask, and default gateway, it will follow a set process for retrieving these details. The process for attaining these details via DHCP is known as DORA:

![[DHCP-20240316164827833.webp|100]]
- DHCP Discover
- DHCP Offer
- DHCP Request
- DHCP Ack

To kick off this process, the new device will send a broadcast packet to the [[LANs|LAN]] in the form of a ==*DHCP Discover*== Message as shown below:

![[DHCP-20240316163152245.webp#invert]]

The DHCP Server will (hopefully) receive this message and reply to the device in question with a ==*DHCP Offer*== message which will contain an 'offer' of an IP address in its' range (and other details):

![[DHCP-20240316163619794.webp#invert]]

The device will then accept the DHCP Offer made by the server with a ==*DHCP Request*== message which tells the server that it would like to lease the offered address:

![[DHCP-20240316163833727.webp#invert]]

On receipt of this request to lease the provided IP address, the DHCP server will respond with an acknowledgement message, a ==*DHCP Ack*==, confirming the start of the lease:

![[DHCP-20240316164219411.webp#invert]]
The last two steps of this: *DHCP Request*, and *DHCP Ack*, are used when a device comes to ==renew it's lease== cutting out the Discover and Offer stages.

## Relays

Some networks may be designed so that the router acts as a DHCP server, however some larger enterprises may choose to configure one ==central DHCP server==, with only a ==relay at each site==/LAN which can also be configured on a router.

If a central DHCP server is located outside the client's [[LANs|LAN]] it ==will not receive== it's DHCP Discover broadcast message. This is where the relay comes in.

On receiving the DHCP Discover message from the client, the relay will simply change the source and destination fields of the packet, and ==forward them on== to the DHCP server.

Once the DHCP Offer message is sent from the server back to the client's DHCP relay, this will forward the Offer message on to the client and so on.

