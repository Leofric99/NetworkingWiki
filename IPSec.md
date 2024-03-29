---
tags:
  - Studies
  - Acronym
  - Networking
  - CCNA
  - Theory
  - CyberSecurity
aliases:
  - Internet Protocol Security
description: A secure network protocol suite that authenticates and encrypts packets of data to provide secure encrypted communication over a network.
---
IPsec is an IETF standard (RFC 2401-2412) that defines how a [[VPNs|VPN]] can be secured across IP networks. 

> [!info]- QRH
> Click [[QRH-IPSec.pdf|here]] for the quick reference handbook.

IPsec protects and authenticates IP packets between source and destination. IPsec can protect traffic from the Transport Layer through to the Application Layer.

## Overview

IPsec provides these essential security functions:

| Security Principle    | Description                                                                                                                                                                   |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Confidentiality       | IPsec utilises encryption algorithms to safeguard packet contents from unauthorised access by cybercriminals.                                                                 |
| Integrity             | IPsec employs hashing algorithms to verify that packets have not been tampered with during transit from source to destination.                                                |
| Origin authentication | IPsec utilises the [[IKE]] to authenticate the source and destination. Authentication methods include pre-shared keys (passwords), digital certificates, or RSA certificates. |
| [[DH]]                | Secure key exchange mechanism, often employing various groups of the Diffie-Hellman algorithm to establish secure communication channels.                                     |

IPsec is ==not bound to any specific rules== for secure communications. This flexibility of the framework allows IPsec to easily integrate new security technologies without updating the existing IPsec standards.

## How it Works (The Framework)

The open slots shown in this IPsec framework in the figure can be filled with any of the choices that are available for that IPsec function to create a unique [[SA]].

![[IPSec-20240318133005629.webp#invert]]

These security functions are listed in the table.

| **IPsec Function**  | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **IPsec Protocol**  | The choices for IPsec Protocol include [[AH]] or [[ESP]]. AH authenticates the Layer 3 packet. ESP encrypts the Layer 3 packet.                                                                                                                                                                                                                                                                                                         |
| **Confidentiality** | Encryption ensures confidentiality of the Layer 3 packet. Secure choices include [[AES]] or [[SEAL]]. Legacy algorithms that should avoided include [[DES]] and [[3DES]].                                                                                                                                                                                                                                                               |
| **Integrity**       | Integrity ensures that data arrives unchanged at the destination by using a hash algorithm. Examples include [[SHA]] and [[MD5]]. MD5 is insecure and should be avoided. There are several versions of SHA. [[SHA1]] is the original version and should be avoided. Instead, [[SHA256]] is recommended to protect sensitive information. [[SHA384]] and [[SHA512]] are required to protect classified information of higher importance. |
| **Authentication**  | IPsec uses [[IKE]] to authenticate users and devices that can carry out communication independently. IKE uses several types of authentication, including username and password, one-time password, biometrics, [[PSKs]], and digital certificates using the [[RSA]] algorithm.                                                                                                                                                          |
| **Diffie-Hellman**  | IPsec uses the [[DH]] algorithm to provide a public key exchange method for two peers to establish a shared secret key. There are several [[DH#Diffie-Hellman Groups]] to choose from.                                                                                                                                                                                                                                                  |

## The Framework Layers

The open slots shown in this IPsec framework in the figure can be filled with any of the choices that are available for that IPsec function to create a unique [[SA]].

#### The Encapsulation Layer

Choosing the IPsec protocol encapsulation is the first building block of the framework. IPsec encapsulates packets using [[AH]] or [[ESP]]. This choice establishes which other building blocks are available.

![[IPSec-20240318135304468.webp#invert]]

> [!note]
> For more information on [[AH]], and [[ESP]], see their respective pages, and [[IPSec#Transport and Tunnel Modes]].

#### The Confidentiality Layer

Confidentiality is achieved by ==encrypting the data==. The degree of confidentiality depends on the encryption algorithm and the length of the key used in the encryption algorithm. 

If someone tries to hack the key through a brute-force attack, the number of possibilities to try is a direct function of the length of the key.

![[IPSec-20240318135759375.webp#invert]]

As shown in the image, the choice of [[Encryption]] protocols from least secure to most secure is [[DES]] -> [[3DES]] -> [[AES]] -> [[SEAL]].

#### The Integrity Layer

Data integrity means that the ==data that is received is exactly the same data that was sent==. Potentially, data could be intercepted and modified. This layer prevents that.

![[IPSec-20240318140022888.webp#invert]]

As shown in the image, the choice of [[Hashing]] protocols from least secure to most secure is [[MD5]] -> [[SHA]].

> [!note]
> Cisco now rates [[SHA1]] as legacy and recommends at least SHA-256 for integrity.

#### The Authentication Layer

When conducting business long distance, you must know who is at the other end of the phone, email, or fax. The same is true of VPN networks. The ==device on the other end== of the VPN tunnel ==must be authenticated== before the communication path is considered secure.

![[IPSec-20240318140340212.webp#invert]]

As shown in the image, the choice of authentication protocols from least secure to most secure is [[PSKs|PSK]] -> [[RSA]].

#### The Key Exchange Layer

Encryption algorithms require a symmetric, shared secret key to perform encryption and decryption. How do the encrypting and decrypting devices get the shared secret key? The easiest key exchange method is to use a public key exchange method, such as [[DH]].

![[IPSec-20240318140617764.webp#invert]]

As shown in the image, the choice of key exchange protocols from least secure to most secure is DH1, DH2, DH5, and so on as per [[DH#Diffie-Hellman Groups]].

## Transport and Tunnel Modes

[[ESP]] and [[AH]] at the first encapsulation layer of IPSec can be applied to IP packets in two different modes, transport mode and tunnel mode. The image below illustrates these two modes, and what is encrypted and authenticated in each mode.

![[IPSec-20240318151218976.webp#invert]]

This table shows what the two modes do:

| Mode               | Description                                                                                                                                                           |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Transport Mode** | Security provided only for the transport layer and above. Protects the payload but leaves the original IP address in plaintext. Used between hosts.                   |
| **Tunnel Mode**    | Provides security for the complete original IP packet. Original IP packet is encrypted and encapsulated in another IP packet (IP-in-IP encryption). Used for routing. |

[[ESP]] tunnel mode is used between a host and a security gateway, or between two security gateways.

As shown in the image below, [[AH]] transport mode provides authentication and integrity for the entire packet. It ==does not encrypt the data==, but it is protected from modification.

![[IPSec-20240318151333574.webp#invert|500]]

[[AH]] tunnel mode encapsulates the IP packet with an AH and a new IP header, and signs the entire packet for integrity and authentication.