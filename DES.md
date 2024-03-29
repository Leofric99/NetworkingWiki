---
tags:
  - Studies
  - CyberSecurity
  - Theory
aliases:
  - Data Encryption Standard
description: An outdated symmetric key method of data encryption.
---
The Data Encryption Standard is a legacy symmetric-key algorithm for the encryption of digital data. Although its short key length of 56 bits makes it too insecure for modern applications, it has been highly influential in the advancement of [[Cryptology]].

DES Can be broken by a $1M machine in a couple of minutes so it may not be a suitable choice for most modern applications.

## Key Length, and Keyspace

As shown in the table, DES with its 56-bit keys has a keyspace of more than 72,000,000,000,000,000 (256) possible keys. 

By adding one bit to the key length, the keyspace doubles, and an attacker needs twice the amount of time to search the keyspace. Adding an additional bit to a 57-bit key size means that it would now take an attacker four times the amount of time to search the keyspace.

| **DES Key** | **Keyspace**                                                                           | **Approximate Number  <br>of Possible Keys** |
| ----------- | -------------------------------------------------------------------------------------- | -------------------------------------------- |
| 56-bit      | $2^{56}$<br>11111111 11111111 11111111<br>11111111 11111111 11111111 11111111          | ~72,000,000,000,000,000                      |
| 57-bit      | $2^{57}$<br>11111111 11111111 11111111<br>11111111 11111111 11111111 11111111 **1**    | ~144,000,000,000,000,000                     |
| 58-bit      | $2^{58}$<br>11111111 11111111 11111111<br>11111111 11111111 11111111 11111111 **11**   | ~288,000,000,000,000,000                     |
| 59-bit      | $2^{59}$<br>11111111 11111111 11111111<br>11111111 11111111 11111111 11111111 **111**  | ~576,000,000,000,000,000                     |
| 60-bit      | $2^{60}$<br>11111111 11111111 11111111<br>11111111 11111111 11111111 11111111 **1111** | ~1,152,000,000,000,000,000                   |

> [!note]
> Longer keys are more secure; however, they are also more resource intensive. Caution should be exercised when choosing longer keys because handling them could add a significant load to the processor in lower-end products.*

--- 

DES does have *weak keys* which are those keys that produce 16 identical subkeys. This occurs when the key bits are:

- Alternating ones and zeros (0101010101010101)
- Alternating F and E (FEFEFEFEFEFEFEFE)
- E0E0E0E0F1F1F1F1
- 1F1F1F1F0E0E0E0E