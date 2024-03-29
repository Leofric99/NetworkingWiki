---
tags:
  - Studies
  - CyberSecurity
  - Theory
  - COM512
description: The science of making and breaking secret codes.
---
Cryptology is the science of making and breaking secret codes. As shown in the figure, cryptology combines two separate disciplines:

- [[Cryptology#Cryptography|Cryptography]] - the development and use of codes.
- [[Cryptology#Cryptanalysis|Cryptanalysis]] - the breaking of those codes.

There is a symbiotic relationship between the two disciplines because ==each makes the other one stronger==.

> [!example]- Historical Use Case
> There have been times when one of the disciplines has been ahead of the other. For example, during the Hundred Years War between France and England, the cryptanalysts were leading the cryptographers. France mistakenly believed that the Vigenère cipher was unbreakable, and then the British cracked it. Some historians believe that the successful cracking of encrypted codes and messages had a major impact on the outcome of World War II. Currently, it is believed that cryptographers are in the lead.

The secret to Cryptology in modern times is all about the [[PSKs|Pre-Shared Key]]. The two main types of Cryptology used in IT today are [[Hashing]], and [[Encryption]].

## Cryptography

Cryptography is the process of ==hiding or coding information== so that only the person a message was intended for can read it. 

The art of cryptography has been used to code messages for thousands of years and continues to be used in bank cards, computer passwords, and ecommerce. Throughout history there have been many cryptography methods including the following:

- [[The Enigma Machine]]
- [[Transposition Ciphers]]
- [[Substitution Ciphers]]
- [[One-Time Pad Ciphers]]

## Cryptanalysis

Cryptanalysis is the practice and study of determining the meaning of encrypted information or ==cracking the code==, without access to the shared secret key. This is also known as codebreaking.

There are various methods of cryptanalysis:

| Attack Method                        | Description                                                                                                                       |
| ------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------- |
| [[Brute-Force Attacks\|Brute-Force]] | The attacker tries every possible key knowing that eventually one of them will work.                                              |
| Ciphertext                           | The attacker has the ciphertext of several encrypted messages but no knowledge of the underlying plaintext.                       |
| Known-Plaintext                      | The attacker has access to the ciphertext of several messages and knows something about the plaintext underlying that ciphertext. |
| Chosen-Plaintext                     | The attacker chooses which data the encryption device encrypts and observes the ciphertext output.                                |
| Chosen-Ciphertext                    | The attacker can choose different ciphertext to be decrypted and has access to the decrypted plaintext.                           |
| Meet-in-the-Middle                   | The attacker knows a portion of the plaintext and the corresponding ciphertext.                                                   |
When choosing a cryptanalysis method, there are various scientific approaches to use. You could use the fact that ==some characters== in the English alphabet are ==used more often than others==. This method is called ~~frequency analysis~~. 

For example, the graph in the image below shows the frequency of letters in the English language. The letters E, T, and A are the most popular letters used in the English language. The letters J, Q, X, and Z are the least popular. 

![[Cryptography-20240304112910413.webp#invert]]

Understanding this pattern can help discover which letters are probably included in the cipher message.

> [!note] 
> Although cryptanalysis is often linked to mischievous purposes, it is actually a necessity and is often used by governments in military and diplomatic surveillance, by enterprises in testing the strength of security procedures, and by malicious hackers in exploiting weaknesses in websites.

To continue research into Cryptology, see [[Hashing|Hash Functions]] and [[Encryption]].