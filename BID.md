---
tags:
  - Studies
  - Acronym
  - Networking
  - CCNA
  - Theory
aliases:
  - Bridge ID
description: A unique identifier assigned to a network bridge.
---
A Bridge ID (BID) is a unique identifier assigned to a network bridge, typically composed of a combination of the bridge's priority value and its [[Studies/MAC|MAC Address]]. The BID is crucial in [[STP]] to determine the root bridge and establish a hierarchy in the network topology.

## Structure

The BID contains a priority value, the [[Studies/MAC|MAC Address]] of the switch, and an extended system ID. The lowest BID value is determined by the combination of these fields.

The BID together with the extended system ID will look like this:

![[BPDUs-20240305110512851.webp#invert]]

| Field              | Description                                                                                                                                                                                               |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Bridge Priority    | The default priority for all Cisco switches is the decimal value 32768. The range is 0 to 61440 in increments of 4096. A lower bridge priority is preferable.                                             |
| Extended System ID | The extended system ID value is a decimal value added to the bridge priority value in the BID to identify the VLAN for this BPDU.                                                                         |
| MAC Address        | When two switches are configured with the same priority and have the same extended system ID, the switch having the MAC address with the lowest value, expressed in hexadecimal, will have the lower BID. |
