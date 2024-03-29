---
tags:
  - Studies
  - CyberSecurity
  - Acronym
  - Theory
aliases:
  - Encapsulating Security Payload
description: An [[IPsec]] protocol used to provide confidentiality, integrity, authentication, and anti-replay protection for IP datagrams through encryption and authentication mechanisms.
---
Encapsulating Security Payload (ESP) is an [[IPSec#Framework Layers|IPSec Framework]] protocol used to provide confidentiality, integrity, authentication, and anti-replay protection for IP datagrams through encryption and authentication mechanisms.

## How it Works

If ESP is selected as the [[IPsec]] protocol, an encryption algorithm *must* also be selected.

ESP can also provide integrity and authentication. First, the payload is encrypted. Next, the encrypted payload is sent through a hash algorithm, such as [[SHA256]] or higher. The hash provides authentication and data integrity for the data payload. 

> [!note]
> [[MD5]] and [[SHA1]] should be avoided.

---

Optionally, ESP can also enforce anti-replay protection.

Anti-replay protection verifies that each packet is unique and is not duplicated. This protection ensures that a hacker cannot intercept packets and insert changed packets into the data stream. Anti-replay works by keeping track of packet sequence numbers and using a sliding window on the destination end.

---

When a connection is established between a source and destination, their counters are initialised at zero. 

Each time a packet is sent, a sequence number is appended to the packet by the source. 

The destination uses the sliding window to determine which sequence numbers are expected. The destination verifies that the sequence number of the packet is not duplicated and is received in the correct order.

> [!example]-
> If the sliding window on the destination is set to one, the destination is expecting to receive the packet with the sequence number one. 
> 
> After it is received, the sliding window moves to two. When detection of a replayed packet occurs, such as the destination receiving a second packet with the sequence number of one, an error message is sent, the replayed packet is discarded, and the event is logged.

---

When both authentication *and* encryption are selected, ==encryption is performed first==. 

One reason for this order of processing is that it facilitates rapid detection and rejection of replayed or bogus packets by the receiving device. Prior to decrypting the packet, the receiver can authenticate inbound packets. 

By doing this, it can quickly detect problems and potentially reduce the impact of [[DoS Attacks]]. To reiterate, ESP provides confidentiality with encryption and provides integrity with authentication.

![[ESP-20240318145519615.webp#invert]]

