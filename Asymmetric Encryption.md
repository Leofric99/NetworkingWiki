---
tags:
  - Studies
  - CyberSecurity
  - Theory
description: Encryption algorithms which are designed so that the key that is used for encryption is different from the key that is used for decryption
---
Asymmetric algorithms, also called public-key algorithms, are designed so that the key that is used for encryption is different from the key that is used for decryption, as shown in the image. 

![[Asymmetric Encryption-20240304152924137.webp#invert]]

The decryption key cannot, in any reasonable amount of time, be calculated from the encryption key and vice versa.

Because ==neither party has a shared secret==, very long [[PSKs#Key Length|key lengths]] must be used. Asymmetric encryption can use key lengths between 512 to 4,096 bits. Key lengths greater than or equal to 2,048 bits can be trusted, while key lengths of 1,024 or shorter are considered insufficient.

Asymmetric algorithms are substantially ==slower== than [[Symmetric Encryption]]. Their design is based on computational problems, such as factoring extremely large numbers or computing discrete logarithms of extremely large numbers.

## How it Works

The ==confidentiality== aspect of Asymmetric Encryption can be summarised with this formula:
$$Public Key (Encrypt) + Private Key (Decrypt) = Confidentiality$$

When the public key is used to encrypt the data, the private key must be used to decrypt the data. Only one host has the private key; therefore, confidentiality is achieved.

If the private key is compromised, another key pair must be generated to replace the compromised key.

The ==authentication== aspect of Asymmetric Encryption can be summarised with this formula:
$$ Private Key (Encrypt) + Public Key (Decrypt) = Authentication $$

When the private key is used to encrypt the data, the corresponding public key must be used to decrypt the data. 

Because only one host has the private key, only that host could have encrypted the message, providing authentication of the sender. 

Typically, no attempt is made to preserve the secrecy of the public key, so any number of hosts can decrypt the message. When a host successfully decrypts a message using a public key, it is trusted that ==the private key== encrypted the message, ==which verifies who the sender is==. This is a form of authentication.

Combining the two asymmetric encryption processes provides message confidentiality, authentication, and ==integrity==.

## Diffie-Hellman

[[DH|Diffie-Hellman]] is an asymmetric encryption algorithm that allows two computers to generate an identical shared secret without having communicated before.