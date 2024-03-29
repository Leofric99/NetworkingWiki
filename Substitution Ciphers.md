---
tags:
  - Studies
  - CyberSecurity
  - Theory
description: These cryptography ciphers substitute one letter for another.
---
Substitution ciphers substitute one letter for another. In their simplest form, substitution ciphers retain the letter frequency of the original message.

## Caesar Cipher

The Caesar Cipher is a type of substitution cipher in which each letter is replaced by another letter that is a set number of places away in the alphabet. That number of places is the key. In this example, the key is 3.

![[Substitution Ciphers-20240304110111902.webp#invert]]

Therefore the two scrolls are shifted, and offset, from one another by three letters. The process is reversed to de-encrypt the message.

## Vigenère Cipher

The Vigenère cipher is a type of *polyalphabetic* substitution cipher.

 It was considered unbreakable until 1863. To use the cipher a key text is generated that repeats for the length of the message to be encrypted. 

![[Substitution Ciphers-20240304110259976.webp#invert]]
 
 A combination of the ~~plaintext letter~~ and the ~~corresponding key letter~~ are used to locate the ciphertext value for the letter in a table, shown in the image above, or other device. In the table, the row value would be the key letter, the plaintext would be located in the column. The location where the row and column intersect is the ciphertext letter to be used.

---

To illustrate how the Vigenère Cipher Table works, suppose that a sender and receiver have a shared secret key composed of these letters: SECRETKEY. The sender uses this secret key to encode the plaintext FLANK EAST ATTACK AT DAWN:

- The F (**F**LANK) is encoded by looking at the intersection of column F and the row starting with S (**S**ECRETKEY), resulting in the cipher letter X.
- The L (F**L**ANK) is encoded by looking at the intersection of column L and the row starting with E (S**E**CRETKEY), resulting in the cipher letter P.
- The A (FL**A**NK) is encoded by looking at the intersection of column A and the row starting with C (SE**C**RETKEY), resulting in the cipher letter C.
- The N (FLA**N**K) is encoded by looking at the intersection of column N and the row starting with R (SEC**R**ETKEY), resulting in the cipher letter E.
- The K (FLAN**K**) is encoded by looking at the intersection of column K and the row starting with E (SECR**E**TKEY), resulting in the cipher letter O.

The process continues until the entire text message FLANK EAST ATTACK AT DAWN is encrypted. The process can also be reversed. For instance, the F is still the cipher letter X if encoded by looking at the intersection of row F (**F**LANK) and the column starting with S (**S**ECRETKEY).

When using the Vigenère cipher, if the message is longer than the key, the key is repeated. For example, SECRETKEYSECRETKEYSEC is required to encode FLANK EAST ATTACK AT DAWN:

- **Secret key**: SECRETKEYSECRETKEYSEC
- **Plaintext:** FLANKEASTATTACKATDAWN
- **Cipher text:** XPCEOXKURSXVRGDKXBSAP