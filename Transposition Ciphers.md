---
tags:
  - Studies
  - CyberSecurity
  - Theory
description: A cryptography method wherein letters are rearranged.
---
In [[Cryptology]] transposition ciphers, no letters are replaced; they are simply rearranged. 

Modern encryption block cipher algorithms, such as [[AES]] and the legacy [[3DES]], still use transposition as part of the algorithm.

An example of this type of cipher is taking the FLANK EAST ATTACK AT DAWN message and transposing it to read NWAD TA KCATTA TSAE KNALF. In this example, the key is to reverse the letters.

## Rail Fence Cipher

The plaintext message will be encoded using a key of 3. This key value specifies that three lines are required when creating the encrypted code.

```
FLANK EAST
ATTACK AT DAWN
```

A rail fence cipher is used with the key of 3.

```
F   K   T   A   T   N
 L N E S A T C A D W 
  A   A   T   K   A
```

And as such, the encrypted text becomes:

```
FKTATN
LNESATCADW
AATKA
```

## Scytales

A scytale is a device used to generate a transposition cipher. 

A strip of paper or other material is wrapped around a rod of a known diameter, as shown in the figure. The message is written on the paper across rows. When the strip is removed, the message is unreadable until it is wrapped around another rod of the same diameter.

![[Transposition Ciphers-20240304104846431.webp|400]]