---
tags:
  - Studies
  - CyberSecurity
  - Acronym
  - Theory
aliases:
  - Authentication Header
description: An [[IPSec]] protocol used to provide integrity, authentication, and anti-replay protection for IP datagrams.
---
Authentication Header (AH) is an [[IPsec#The Framework Layers|IPSec Framework]] protocol used to provide integrity, authentication, and anti-replay protection for IP datagrams. 

Think of it as similar to [[MD5]] or [[SHA]]. These two protocols actually do the hashing for AH. The difference with AH in its entirety is that it operates at layer three protecting the entire packet (even IP headers which it rebuilds) from being tampered with in transit.

## How it Works

AH achieves authenticity by applying a keyed one-way [[Hashing|Hash Function]] to the packet to create a hash or message digest. The hash is combined with the text and is transmitted in plaintext, as shown in in the image.

1. The IP header and data payload are hashed using the shared secret key.

2. The hash builds a new AH header, which is inserted into the original packet, as shown in the image below.
   
![[AH-20240318142309301.webp#invert|400]]

3. The new packet is transmitted to the IPsec peer router.

4. The peer router hashes the IP header and data payload using the shared secret key, extracts the transmitted hash from the AH header, and compares the two hashes, as shown in the figure below.

![[AH-20240318142421797.webp#invert|400]]

The hashes ==must match exactly==. If one bit is changed in the transmitted packet, the hash output on the received packet changes and the AH header will not match.

AH supports the use of [[MD5]] and [[SHA]] algorithms to perform the hashing. AH may not work if the environment uses [[NAT]].