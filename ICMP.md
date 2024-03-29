---
tags:
  - Studies
  - Acronym
  - Networking
  - CCNA
  - Theory
  - COM412
description: A supporting protocol in the Internet protocol suite that is used by network devices for error messaging and operational information.
---

The ==Internet Control Message Protocol== is a supporting protocol in the Internet protocol (IP) suite that is used by network devices, like routers, to send error messages and operational information. It also helps in diagnosing network-related issues by sending and receiving diagnostic and error messages.

## Ping

Ping, as it is commonly known, is a useful tool. It is also a part of the ICMP. Ping uses ==two message types== for communication:

- ICMP Echo Request
- ICMP Echo Reply

The command to use on Windows, Linux, and Cisco IOS for sending 'pings' is `ping {ip-address}`.

The `ping` command sends several packets of information to a specific URL or IP address and waits for a response. When it gets the response, the `ping` tool provides the following details:

- **Round-trip time**: This is the ==time taken== for each packet to reach the target host and return. It helps in assessing the speed of the network connection.
- **Packet loss**: If some packets do not get a reply within a certain timeout period, they are considered lost. ==Packet loss== can indicate network issues.
- **Active or inactive status**: `Ping` can determine whether a remote host is ==active or inactive== based on whether it receives a reply or not.

