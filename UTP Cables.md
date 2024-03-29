---
tags:
  - Studies
  - Acronym
  - Networking
  - CCNA
  - Theory
  - COM412
description: A common type of copper cabling used in networking, consisting of twisted pairs of insulated copper wires.
aliases:
  - Unshielded Twisted Pair Cables
---

UTP stands for Unshielded Twisted Pair. 

These cables have no metallic shield to guard against Electromagnetic interference from external sources, although they can guard against most EMI from their neighbouring cables due to their twisted nature.

UTP Cables have 8 cables in total, bound in to 4 twisted pairs. As separate wires are used for sending and receiving, these cables can operate in ==full-duplex== meaning that they can send and receive at the same time without any data collisions.

![[Pasted image 20240126142746.png|200]]

There are two basic different types of UTP cable (although there are other denominations which have different cable orders). These are Straight through, and Crossover.

==Straight-through cables== are wired so that the transmitting wires on one end are connected to receiving wires for end devices on the other end. Networking devices on the other hand will all have their transmitting and receiving nodes on the same pins, and so ==Crossover cables== are required. These cables cross over the wires so that two of the same type of networking interface can be directly connected such as a router to a switch, or router to another router.

Most modern networking devices have a feature called ==Auto-[[MDIX]]== which can alter which pins are sending and which are receiving so that it can automatically adjust if the wrong type of UTP cable is connected.