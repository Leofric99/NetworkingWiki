---
tags:
  - Studies
  - CyberSecurity
  - Theory
description: Encryption algorithms which uses the same pre-shared key to encrypt and decrypt data.
---
Symmetric encryption algorithms such as [[DES]], [[3DES]], and [[AES]] are different from [[Asymmetric Encryption]] in that it is based on the premise that each communicating party knows the pre-shared key.

Symmetric algorithms use the same [[PSKs|Pre-Shared Key]] to encrypt and decrypt data, and are typically used for [[VPNs]] because they require less CPU resources than asymmetric encryption.

To ensure that the encryption is safe, a minimum [[PSKs#Key Length|key length]] of 128 bits should be used. Use a longer key for more secure communications at the cost of performance.

## Symmetric Encryption Example %% fold %%

To help illustrate how symmetric encryption works, consider an example where Alice and Bob live in different locations and want to exchange secret messages with one another through the mail system. In this example, Alice wants to send a secret message to Bob.

In the image, Alice and Bob ==have identical keys== to a single padlock. These keys were exchanged prior to sending any secret messages. Alice writes a secret message and puts it in a small box that ==she locks using the padlock with her key==. She mails the box to Bob. The message is safely locked inside the box as the box makes its way through the post office system. When Bob receives the box, ==he uses his key to unlock the padlock== and retrieve the message. Bob can use the same box and padlock to send a secret reply back to Alice.

![[Encryption-20240304150825651.webp#invert]]

## Block Ciphers

Symmetric encryption algorithms are sometimes classified as either a block cipher or a stream cipher. 

Block ciphers transform a fixed-length block of plaintext into a common block of ciphertext of 64 or 128 bits. Common block ciphers include [[DES]] with a 64-bit block size and [[AES]] with a 128-bit block size.

![[Encryption-20240304151329537.webp#invert]]

## Stream Ciphers

Symmetric encryption algorithms are sometimes classified as either a block cipher or a stream cipher.

Stream ciphers encrypt plaintext one byte or one bit at a time. Stream ciphers are basically a block cipher with a block size of one byte or bit. Stream ciphers are typically faster than block ciphers because data is continuously encrypted. Examples of stream ciphers include [[RC4]] and [[A5]] which is used to encrypt [[GSM]].

![[Encryption-20240304152250466.webp#invert]]
