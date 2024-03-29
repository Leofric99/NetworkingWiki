---
tags:
  - Studies
  - CyberSecurity
  - Theory
description: An attack which involves embedding a hidden VLAN tag inside the frame that already has a VLAN tag.
---
A threat actor in specific situations could embed a hidden 802.1Q tag inside the frame that already has an 802.1Q tag.

This tag allows the frame to go to a VLAN that the original 802.1Q tag did not specify.
## How it Works

The threat actor begins by sending a double-tagged 802.1Q frame to the switch. The outer header has the VLAN tag of the threat actor, which is the same as the native VLAN of the trunk port. 

For the purposes of this example, assume that this is VLAN 10. The inner tag is the victim VLAN, in this example, VLAN 20.

![[VLAN Double-Tagging Attacks-20240302131918152.webp#invert|500]]

The frame then arrives on the first switch, which looks at the first 4-byte 802.1Q tag. The switch sees that the frame is destined for VLAN 10, which is the native VLAN. 

The ==switch forwards== the packet out all VLAN 10 ports after stripping the VLAN 10 tag. The frame is not retagged because it is part of the native VLAN. At this point, the ==VLAN 20 tag is still intact== and has not been inspected by the first switch.

---

The frame arrives at the second switch which has no knowledge that it was supposed to be for VLAN 10. 

==Native VLAN traffic is not tagged== by the sending switch as specified in the 802.1Q specification. The second switch looks only at the inner 802.1Q tag that the threat actor inserted and sees that the frame is ==destined for VLAN 20==, the target VLAN. 

The second switch sends the frame on to the target or floods it, depending on whether there is an existing MAC address table entry for the target.

![[VLAN Double-Tagging Attacks-20240302132159919.webp#invert|500]]

---

A VLAN double-tagging attack is unidirectional and works only when the attacker is connected to a port residing in the ==same VLAN as the native VLAN== of the trunk port. The idea is that double tagging allows the attacker to send data to hosts or servers on a VLAN that otherwise would be blocked by some type of access control configuration.

![[VLAN Attacks#Mitigating VLAN Attacks]]