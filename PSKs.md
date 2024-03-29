---
tags:
  - Studies
  - CyberSecurity
  - Acronym
  - Theory
aliases:
  - Pre-Shared Keys
description: A secret key that has been established between the parties who are authorised to use it by means of some secure method.
---
In [[Cryptology]], a pre-shared key is a shared secret which was previously shared between the two parties using some secure channel before it needs to be used.

In the world of communications and networking, [[The CIA Security Triad]] is implemented in many ways using various protocols and algorithms. The choice of protocol and algorithm varies based on the level of security required to meet the goals of the network security policy.

## PSK Examples %% fold %%

As an example, for message integrity, [[MD5]] is faster than [[SHA2]]. However, MD5 is now considered to be insecure. Confidentiality can be implemented using the legacy [[3DES]] or the more secure [[AES]]. 

Additional considerations are the ==computing power== that is required to encrypt and decrypt data, and the acceptance of the protocol in the security community. The table lists some common cryptographic hashes, protocols, and algorithms.

| **Integrity**    | **Authenticity**      | **Confidentiality** |
| ---------------- | --------------------- | ------------------- |
| [[MD5]] (legacy) | [[HMAC]]-MD5 (legacy) | [[3DES]] (legacy)   |
| [[SHA]]          | HMAC-SHA-256          | [[AES]]             |
|                  | [[RSA]] and [[DSA]]   |                     |
Old encryption algorithms, such as the Caesar cipher or the Enigma machine, were based on the secrecy of the algorithm to achieve confidentiality. 

With modern technology, where ==reverse engineering is often simple==, public-domain algorithms are frequently used. With most modern algorithms, successful decryption requires knowledge of the appropriate cryptographic keys. This means that the security of encryption lies in the ==secrecy of the keys, not the algorithm==.

## Key Management

Key management is often considered the most difficult part of designing a cryptosystem. As shown in the table, there are several essential characteristics of key management to consider.

| **Characteristic**             | **Description**                                                                                                                                                                                                                                                                                                                                                                                         |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Key Generation                 | It was up to Caesar to choose the key of his cipher. The Vigenère cipher key is also chosen by the sender and receiver. In a modern cryptographic system, key generation is usually automated and not left to the end user. The use of good random number generators is needed to ensure that all keys are equally generated so that the attacker cannot predict which keys are more likely to be used. |
| Key Verification               | Some keys are better than others. Almost all cryptographic algorithms have some weak keys that should not be used. With the help of key verification procedures, weak keys can be identified and regenerated to provide a more secure encryption. With the Caesar cipher, using a key of 0 or 25 does not encrypt the message, so it should not be used.                                                |
| Key Exchange                   | Key management procedures should provide a secure key exchange mechanism that allows secure agreement on the keying material with the other party, probably over an untrusted medium.                                                                                                                                                                                                                   |
| Key Storage                    | On a modern multi-user operating system that uses cryptography, a key can be stored in memory. This presents a possible problem when that memory is swapped to the disk, because a Trojan horse program installed on the PC of a user could then have access to the private keys of that user.                                                                                                          |
| Key Lifetime                   | Using short key lifetimes improves the security of legacy ciphers that are used on high-speed connections. In IPsec a 24-hour lifetime is typical. However, changing the lifetime to 30 minutes improves the security of the algorithms.                                                                                                                                                                |
| Key Revocation and Destruction | Revocation notifies all interested parties that a certain key has been compromised and should no longer be used. Destruction erases old keys in a manner that prevents malicious attackers from recovering them.                                                                                                                                                                                        |

#### Key Types

Several types of cryptographic keys can be generated for different purposes as shown in the table below:

| Key Type               | Application                                                                          | Explanation                                                                                                            |
| ---------------------- | ------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------- |
| Symmetric keys         | VPN between two routers                                                              | Keys that can be exchanged between two routers supporting a Virtual Private Network (VPN).                             |
| Asymmetric keys        | Secure HTTPS applications                                                            | Keys used in secure [[HTTP and HTTPS\|HTTPS]] applications for secure communication over the internet.                 |
| Digital signatures     | Connecting to a secure website                                                       | Signatures used in the process of connecting to a secure website, providing authentication and integrity verification. |
| [[Hashing\|Hash]] keys | Symmetric and asymmetric key generation, digital signatures, and other applications. | Keys used in symmetric and asymmetric key generation, digital signatures, and various other applications.              |

Regardless of the key type, ==all keys share similar issues==. Choosing a suitable key length is one issue.

If the keyspace is large enough, the search requires an enormous amount of time, making such an exhaustive effort impractical. The table below summarises the key length required to secure data for the indicated amount of time.

| Length of Protection                 | Symmetric Key | Asymmetric Key | Digital Signature | Hash |
| ------------------------------------ | ------------- | -------------- | ----------------- | ---- |
| 3 years                              | 80            | 1248           | 160               | 160  |
| 10 years                             | 96            | 1776           | 192               | 192  |
| 20 years                             | 112           | 2432           | 224               | 224  |
| 30 years                             | 128           | 3248           | 256               | 256  |
| Protection against quantum computers | 256           | 15424          | 512               | 512  |

Current key lengths can easily make any attempt insignificant because it takes millions or billions of years to complete the search when a sufficiently long key is used. With modern algorithms that are trusted, the ==strength of protection depends solely on the size of the key==.

#### Key Length, and Keyspace

Two terms that are used to describe keys are:

- Key length - Also called the key size, this is the ==measure in bits==. In this course, we will use the term key length.
- Keyspace - This is the ==number of possibilities== that can be generated by a specific key length.

#### Key Length

As key length increase, the keyspace increases exponentially:

| Key Length    | Keyspace          | Explanation                                                   |
| ------------- | ----------------- | ------------------------------------------------------------- |
| 2-bit (2^2)   | 4                 | Four possible keys (00, 01, 10, and 11).                      |
| 3-bit (2^3)   | 8                 | Eight possible keys (000, 001, 010, 011, 100, 101, 110, 111). |
| 4-bit (2^4)   | 16                | Sixteen possible keys.                                        |
| 40-bit (2^40) | 1,099,511,627,776 | A vast keyspace with over a trillion possible keys.           |
See [[AES#Characteristics]] for an example of a use case for long key lengths.

#### Keyspace

The keyspace of an algorithm is the set of all possible key values. 

A key that has $n$ bits produces a keyspace that has $2n$ possible key values. By adding one bit to the key, the keyspace is effectively doubled. For an example of a keyspace, see [[DES#Key Length, and Keyspace]].

Almost every algorithm has some weak keys in its keyspace that enable an attacker to break the encryption via a shortcut. 

Weak keys show the regularities in encryption. For instance, DES has four keys for which encryption is the same as decryption. This means that if one of these weak keys is used to encrypt plaintext, an attacker can use the weak key to decrypt the ciphertext and reveal the plaintext.

## Key Choice

When choosing a key type, it all comes down to ==how much performance== you are capable of squeezing out of your hardware. The better the performance, the more secure your keys. Algorithms such as [[RSA]] will run slowly due to having large key lengths unless the hardware has surplus performance to spare.

The estimated ==funding of the attacker== should also affect the choice of key length. For example, classic ~~[[DES]] can be broken~~ by a $1 million machine in a couple of minutes.

The rule: *the longer the key, the better* is valid, except for possible performance reasons. Shorter keys equal faster processing, but are less secure. Longer keys equal slower processing, but are more secure.