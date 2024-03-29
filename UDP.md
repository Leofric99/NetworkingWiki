---
tags:
  - Studies
  - Acronym
  - Networking
  - CCNA
  - Theory
aliases:
  - User Datagram Protocol
description: A layer four protocol like TCP which is connectionless and prioritises speed over reliability.
---
The User Datagram Protocol (UDP) is a connectionless transport layer protocol that prioritises speed over reliability for real-time applications. 

## Header

This is the UDP header. It is considerably more simple than the [[TCP#Header]], as UDP does far less and is far less complicated.

![[UDP-20240316160437657.webp#invert]]

The only thing in the header which might help the receiving device check for errors is the final checksum field. UDP generally does not check errors itself however. See [[UDP#Error Checking]].

## Establishing Connections

Unlike [[TCP]], it forgoes establishing a connection before sending data, making it faster which is ideal for real-time applications like video streams that can tolerate some data loss.

## Error Checking

UDP doesn't guarantee delivery or check for errors; it is known as *'best effort'*. If segments arrive, great; if segments don't arrive, UDP makes no effort to check or re-transmit. 

## Ordering / Sequencing

Unlike [[TCP]], UDP does not keep track of the order of the packets it sends, so if data arrives out of order, the receiving device will just have to do it's best through other means (probably in the application layer) to put things right.

## Flow Control

Unlike [[TCP#Window Size]], UDP has no method for controlling the flow of data it sends.