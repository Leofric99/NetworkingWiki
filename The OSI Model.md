---
tags:
  - Studies
  - Networking
  - CCNA
  - Theory
  - COM412
description: A conceptual framework that standardises network architecture into seven layers.
---

OSI Stands for Open Systems Interconnection. It is a standard which is used industry-wide to categorise the different functions performed by a network, created by the [[ISO]]. It is broken into seven layers as shown below.

| Layer Number | Layer Name   | Layer Function                                                                                                                                                                                                                                            |
| :----------- | :----------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 7            | Application  | Interacts with software which has a communication component. Protocols at this layer include: [[HTTP and HTTPS]]. This layer can identify communication partners, and synchronise communication.                                                          |
| 6            | Presentation | Translates between the application, and network formats, or between two different application protocols. One possible function of this layer is encrypting data.                                                                                          |
| 5            | Session      | Manages sessions between applications eg. a web browser, and YouTube. It establishes, manages, and terminates the connections as required. Data at all three of these top layers is called ==data==.                                                      |
| 4            | Transport    | Segments, and re-assembles data in the correct order for communications. This layer also provides end-to-end communication and manages the connections. Data at this stage is called a ==segment==. Protocols at this layer include: [[TCP]] and [[UDP]]. |
| 3            | Network      | Provides end-to-end logical addressing (IP Addresses). Data at this stage is called a ==packet==.                                                                                                                                                         |
| 2            | Data Link    | Provides node-to-node connectivity (each hop). This layer also handles how data is formatted for transmission over cables. It can also detect and correct Physical layer errors. Uses MAC Addressing. Data at this stage is called a ==frame==.           |
| 1            | Physical     | The physical transmission of bits over the medium. Data at this stage are called ==bits==.                                                                                                                                                                |

A layer two frame just before it is transmitted will appear as in the image below as it is encapsulated at each layer (Between 2 and 4). This is a Frame.

![[Pasted image 20240126150528.png#invert]]

Whether the data is at layer seven, six, five, four, three, two, or one, the data, segments, packets, or frames, have a collective term: Protocol Data Units ([[PDUs]]).

There is another model used for the same thing which is actually used in modern networks. [[The TCP IP Model]]. But the OSI Model is actually how Network Engineers think about Networking.