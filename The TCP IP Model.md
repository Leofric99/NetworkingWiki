---
tags:
  - Studies
  - Networking
  - CCNA
  - Theory
  - COM412
description: A concise four-layer conceptual framework that facilitates communication in computer networks.
---

In the TCP/IP Model, unlike in [[The OSI Model]], there are only four layers, this is because some of [[The OSI Model]]'s seven layers are bundled into one.

Although [[The OSI Model]] is the model which Network Engineers generally talk about and use day-to-day, the ==TCP/IP Model is the model which is actually in use==.

| Layer Number | Layer Name | Layer Function |
| :--- | :--- | :--- |
| 4 | Application | This bundle's [[The OSI Model]]'s top three layers into one. It Interacts with software which has a communication component. Protocols at this layer include: [[HTTP and HTTPS]]. This layer can identify communication partners, and synchronise communication.<br><br>It also translates between the application, and network formats, or between two different application protocols. One possible function of this layer is encrypting data.<br><br>Finally, it manages sessions between applications eg. a web browser, and YouTube. It establishes, manages, and terminates the connections as required. |
| 3 | Transport | This layer is bundled. It contains [[The OSI Model]]'s Transport, and Network Layers. <br><br>It segments, and re-assembles data in the correct order for communications. This layer also provides end-to-end communication and manages the connections. <br><br>It also provides end-to-end logical addressing (IP Addressing) |
| 2 | Data Link | This layer is the same as in [[The OSI Model]]. <br><br>It provides node-to-node connectivity (each hop). This layer also handles how data is formatted for transmission over cables. It can also detect and correct Physical layer errors. Uses MAC Addressing.  |
| 1 | Physical | This layer is the same as in [[The OSI Model]]. <br><br>It carries out the physical transmission of bits over the medium. |
