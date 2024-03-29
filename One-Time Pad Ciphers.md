---
tags:
  - Studies
  - CyberSecurity
  - Theory
description: An encryption technique that cannot be cracked, but requires the use of a single-use pre-shared key.
---
In [[Cryptology]], the one-time pad is an encryption technique that cannot be cracked, but requires the use of a single-use [[PSKs|Pre-Shared Key]] that is larger than or equal to the size of the message being sent. In this technique, a plaintext is paired with a random secret key.

Gilbert Vernam proposed the one-time pad cypher. A cipher in which a prepared key consisting of an arbitrarily long, non-repeating sequence of numbers was kept on paper tape. It was then combined character by character with the plaintext message to produce the ciphertext.

![[One-Time Pad Ciphers-20240304110659200.webp|400]]

To decipher the ciphertext, the same paper tape key was again combined character by character, producing the plaintext. Each tape was used only once; hence, the name one-time pad. 

As long as the key tape does not repeat or is not reused, this type of cipher is immune to cryptanalytic attack. This is because the available ciphertext does not display the pattern of the key.