---
tags:
  - Studies
  - CyberSecurity
  - Theory
  - Networking
  - CCNA
aliases:
  - Diffie-Hellman
description: An asymmetric encryption algorithm that allows two computers to generate an identical shared secret without having communicated before.
---
Diffie-Hellman (DH) is an [[Asymmetric Encryption]] algorithm that allows two computers to generate an identical shared secret without having communicated before. 

The new shared key is never actually exchanged between the sender and receiver. However, because both parties know it, the key can be used by an encryption algorithm to encrypt traffic between the two systems.

Here are two examples of instances when DH is commonly used:

- Data is exchanged using an IPsec VPN
- SSH data is exchanged

## How it Works

To help illustrate how DH operates, refer to the image. The colours in this image represent complex long numbers to simplify the DH key agreement process. 

![[DH-20240304154615846.webp#invert]]

The DH key exchange begins with Alice and Bob agreeing on an arbitrary ==common== colour that does not need to be kept secret. The agreed-on colour in our example is brown (in the inverted image).

Next, Alice and Bob will each select a ==secret== colour. Alice chose red while Bob chose blue. These secret colours will never be shared with anyone. The secret colour represents the chosen secret private key of each party.

Alice and Bob now mix the shared common colour (brown) with their respective secret colour to produce a public colour. Therefore, Alice will mix the brown with her red colour to produce a public colour of orange. Bob will mix the brown and the blue to produce a public colour of green.

Alice sends her public color (orange) to Bob and Bob sends his public color (green) to Alice.

Alice and Bob each mix the colour they received with their own, original secret colour (Red for Alice and blue for Bob.). The result is a light final brown colour mixture that is identical to the partner’s final colour mixture. The brown colour represents the resulting shared secret key between Bob and Alice.

## The Algorithm's Security

The security of DH is based on the fact that it uses ==very large numbers== in its calculations.

## Diffie-Hellman Groups

Diffie-Hellman uses different DH ==groups to determine the strength of the key== that is used in the key agreement process. The higher group numbers are more secure, but require additional time to compute the key. 

The following table identifies the DH groups supported by Cisco IOS Software and their associated prime number value:

| DH Group | Key Size (bits) | Description                                                                                           |
|----------|-----------------|-------------------------------------------------------------------------------------------------------|
| 1        | 768             | No longer recommended due to small key size, vulnerable to attacks.                                   |
| 2        | 1024            | No longer recommended due to small key size, vulnerable to attacks.                                   |
| 5        | 1536            | No longer recommended due to small key size, vulnerable to attacks.                                   |
| 14       | 2048            | Recommended for use until 2030, offering larger and more secure key size.                            |
| 15       | 3072            | Recommended for use until 2030, offering larger and more secure key size.                            |
| 16       | 4096            | Recommended for use until 2030, offering larger and more secure key size.                            |
| 19       | 256             | Support Elliptical Curve Cryptography (ECC), reducing key generation time.                             |
| 20       | 384             | Support Elliptical Curve Cryptography (ECC), reducing key generation time.                             |
| 21       | 521             | Support Elliptical Curve Cryptography (ECC), reducing key generation time.                             |
| 24       | 2048            | Preferred next-generation encryption, supporting Elliptical Curve Cryptography (ECC).                   |
