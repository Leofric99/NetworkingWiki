---
tags:
  - Studies
  - Acronym
  - Networking
aliases:
  - MTU
  - Maximum Transmission Unit
---

**Maximum Transmission Unit**

The maximum size of one single packet. *Usually* this value is 1500 bytes.

Any packet larger than this size will need to be split into multiple parts (Fragments). [[The IPv4 Header#Identification]] field, [[The IPv4 Header#Flags]] field, and [[The IPv4 Header#Fragment Offset]] field are used to keep track of the different parts.