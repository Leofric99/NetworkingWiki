---
tags:
  - Studies
  - Acronym
  - Networking
  - CCNA
  - Theory
  - COM412
aliases:
  - Variable Length Subnet Masks
  - Variable Length Subnet Mask
description: A method of subnetting using subnet masks of variable lengths.
---
Variable Length Subnet Masks are used to allocate IP addresses efficiently. [[IPv4 Subnetting|Fixed Length Subnet Masks]], VLSM allows for the creation of ==subnets with varying sizes==, enabling more ==flexible and precise allocation== of IP addresses within a network without wasting the address space.

The basic steps for subnetting using VLSM are as follows:

1. Assign the subnet requiring the most hosts *first*.
2. Assign the subnet requiring the second most hosts *second*.
3. Continue in this way until all subnets have been assigned.

You *must* follow this order or you *will* encounter problems with either the subnetting itself, or assigning these address spaces to the networking devices.

With this method in mind, all you need to do is to follow this method from [[IPv4 Subnetting]] if a requirement is for number of hosts in each [[LANs|LAN]]:


![[IPv4 Subnetting#Calculating Required Host Bits for Number of Hosts]]
