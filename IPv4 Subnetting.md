---
tags:
  - Studies
  - Networking
  - CCNA
  - Theory
  - COM412
aliases:
  - Subnets
  - FLSM
  - Fixed Length Subnet Masks
  - Fixed Length Subnet Mask
description: A technique in computer networking that involves dividing an IP network into sub-networks.
---
A subnet, or subnetwork, is ==a smaller network carved out of a larger one==, typically for the purpose of improving network efficiency or security. It allows an organisation to split a single IP network into multiple smaller networks, each with its own range of IP addresses and potentially its own network infrastructure.

> [!info]- QRH
> Click [[QRH-IPv4-Subnetting.pdf|here]] for the quick reference handbook.

Subnets operate at layer three with either [[IPv4]] or [[IPv6]]. There is a supporting layer two architecture which performs a similar function on layer two devices like switches known as [[VLANs]].

Note that the methods detailed here are not usually an ideal solution as it can waste subnets if the number you need does not perfectly align with the number of host bits you borrow for the network portion. If this is the case [[VLSM]] may be a better solution.

## Calculating Possible Hosts

In order to calculate the number of possible host addresses in a network, we must use the following formula where $n$ represents the number of host bits available for use in binary:
$$2^n - 2$$
See [[Decimal & Binary Conversion|The Decimal & Binary Conversion Table]] to find the host bits for a given Subnet Mask. 

The two is subtracted to allow for the un-assignable addresses of the network address, and the broadcast address.

## Calculating Required Host Bits for Number of Hosts

Re-arranging the formula above, we can use the formula below to calculate how many host bits will be required (and therefore subnet mask) of the new subnet. In this formula, $x$ is the required number of hosts, and $n$ is the number of host bits which will be needed.
$$n = log2​(x+2)$$
With this equation, if the result is a decimal, you would *always* round up to the next whole number.
## Calculating Possible Subnets

In order to calculate the number of possible subnets from a parent network, we can use the formula $2^x$ where $x$ is the number of borrowed host bits. (the number of extra bits we will move to the network portion to create the subnets). As above, we can use [[Decimal & Binary Conversion|The Decimal & Binary Conversion Table]] to find the binary from any given decimal address.

In this /24 example, we are 'borrowing' two bits for the subnets which will create 4 possible subnets. Each one becoming a /26 network.

| Metric | Value |
| :--- | :--- |
| Original Network: | `192.168.255.0` |
| Original Subnet Mask: | `11111111.11111111.11111111.00000000` |
| Original Subnet: | `255.255.255.0` |
As each new network bit can either be a one or a zero we can calculate the new network addresses by finding the decimal values for binary `00000000`, `01000000`, `10000000`, and `11000000`.

| Metric | Value |
| :--- | :--- |
| New Networks: | `192.168.255.0 - 63` |
|  | `192.168.255.64 - 127` |
|  | `192.168.255.128 - 191` |
|  | `192.168.255.192 - 255` |
| New Subnet Mask: | `11111111.11111111.11111111.11000000` |
| New Subnet: | `255.255.255.192` |
## Finding How Many Bits to Borrow for New Subnets

There is a simple formula to find out how many network bits need to be borrowed from the host portion of an address to create new subnets. This is derived from the $2^x$ formula in the section above. In this formula below $y$ is the number of required subnets.

$$x = \frac{log(y)}{log(2)}$$

If this formula results in a decimal value being returned **always** round up.
## Identifying the Subnet in which an IP Address Resides

To identify which subnet an IP Address resides in, we can write the IP address out in decimal and binary. For example:

| Given IP Address | Subnet Mask (in Binary) |
|:-----------------|:------------|
|     `192.168.5.57/27` | `11000000.10101000.00000101.00111001`            |  

If we then separate that subnet mask to show the network, and host, bits we get:

| Network Portion | Host Portion |
|:---|:---|
| `11000000.10101000.00000101.001` | `11001` |  
Now, it is simply a case of converting the binary figure for the network address portion into decimal (whilst all host bits are set to 0). So, `00100000` becomes `32`. Therefore this IP address is a part of the `192.168.5.32/27` subnet.