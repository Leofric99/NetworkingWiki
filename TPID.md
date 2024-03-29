---
tags:
  - Studies
  - Acronym
  - Networking
aliases:
  - Tag Protocol Identifier
---
TPID (Tag Protocol Identifier) is a field in [[The Ethernet Frame]] header that ==specifies the protocol used for frame tagging== when using [[Trunking]] to carry multiple [[VLANs]].

This field is ==16 bits in length== (2 bytes) which is *always* set to `0x8100` (0x means [[Hexadecimal Notation|Hexadecimal]]). This simply means that the frame *is* VLAN tagged.