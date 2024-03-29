---
tags:
  - Studies
  - CyberSecurity
  - Acronym
  - Theory
aliases:
  - Hash-Based Message Authentication Code
description: A specific type of message authentication code involving a cryptographic hash function and a secret cryptographic key.
---
In [[Cryptology]], a Hash-Based Message Authentication Code (HMAC) is a specific type of [[Studies/Acronyms with Duplicate Names/MAC|MAC]] which incorporates both a ==cryptographic hash function== *and* a ==secret cryptographic key==.

Only the ~~sender~~ and the ~~receiver~~ know the *secret key*, and the output of the hash function now depends on the input data and the secret key. 

Only parties who have access to that secret key can compute the digest of an HMAC function. This defeats [[MITM Attacks]] and provides authentication of the data origin.

## How it Works

As shown in the image, the ~~sending~~ device inputs data (such as Terry Smith’s pay of $100 and the secret key) into the hashing algorithm and calculates the *fixed-length HMAC digest*. 

This authenticated digest is then attached to the message and sent to the receiver.

![[HMAC-20240304133315480.webp#invert]]

The receiving device then removes the *digest* from the message and uses the plaintext message ==with its secret key== as input into the same hashing function. 

If the digest that is calculated by the receiving device is equal to the digest that was sent, the message has not been altered. Additionally, the origin of the message is authenticated because ==only the sender== possesses a copy of the shared secret key.

![[HMAC-20240304134456345.webp#invert]]

## Cisco Router HMAC Example

The image shows how HMACs are used by Cisco routers that are configured to use [[OSPF]] routing authentication.

R1 is sending an  regarding a route to network 10.2.0.0/16:

1. R1 calculates the hash value using the [[LSUs|LSU]] message and the secret key.
2. The resulting hash value is sent with the LSU to R2.
3. R2 calculates the hash value using the LSU and its secret key. R2 accepts the update if the hash values match. If they do not match, R2 discards the update.

![[HMAC-20240304135026263.webp#invert]]