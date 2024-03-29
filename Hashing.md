---
tags:
  - Studies
  - CyberSecurity
  - Theory
aliases:
  - Hash Functions
description: The process of transforming any given key or a string of characters into another value.
---
Hashing is the process of transforming any given key or a string of characters into another value. They are used to ==verify and ensure== data integrity. They are also used to verify authentication. 

Hashing is based on a ==one-way mathematical function== that is relatively easy to compute, but significantly harder to reverse. This is what separates it from [[Encryption]]. Encryption is designed to be reversed whereas Hashing is not.

As shown in the image, a hash function takes a variable block of binary data, called the message, and produces a fixed-length, condensed representation, called the hash.

![[Cryptology-20240304130800034.webp#invert|400]]

With hash functions, it is computationally ==infeasible== for two different sets of data to come up with the ==same hash output==. Furthermore, the hash value changes every time the data is changed or altered. Because of this, cryptographic hash values are often called *digital fingerprints*.

[[MD5]], and [[SHA]], are examples of Hash Functions.

## How they Work

Mathematically, the equation $h = H(x)$ is used to explain how a hash algorithm operates. As shown in the image, a hash function $H$ takes an input $x$ and returns a fixed-size string hash value $h$.

![[Cryptology-20240304131010686.webp#invert]]

The example in the figure summarises the mathematical process. A cryptographic hash function should have the following properties:

- The input can be any length.
- The output is always a fixed length.
- $H(x)$ is relatively easy to compute for any given x.
- $H(x)$ is one way and not reversible.
- $H(x)$ is collision free, meaning that two different input values will result in different hash values.

If a hash function is hard to invert, it is considered a one-way hash. 

Hard to invert means that given a hash value of $h$, it is computationally infeasible to find an input for $x$ such that $h = H(x)$.

## Hashing Limitations

While hashing can be used to detect accidental changes, it ==cannot== be used to ==guard against deliberate changes== that are made by a threat actor. There is no unique identifying information from the sender in the hashing procedure. 

This means that *anyone* can compute a hash for any data, as long as they have the correct hash function.

To get around this issue, researchers developed [[Studies/Acronyms with Duplicate Names/MAC|MAC]], which lead to the invention of [[HMAC]].