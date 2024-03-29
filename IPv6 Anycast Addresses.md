---
tags:
  - "#Studies"
  - Networking
  - CCNA
  - Theory
description: An IPv6 packet that specifies one-of-many destinations.
---
[[IPv6]] Anycast addresses are addresses that specify one-of-many devices. A good way of thinking about anycast addresses is as a kind of [[HSRP]] for IPv6 routers.

Multiple routers are configured with the ==same IPv6 anycast address==. They use a routing protocol to advertise this address. Then, when devices send traffic to that address, it goes to (the closest) one of the many routers.

## IPv6 Anycast Address Ranges

There is no specified range for IPv6 anycast addresses. They simply use a regular unicast address - either [[GUAs]] or [[ULAs]] and then when configuring the address you specify that this is an anycast address.

> [!example]- 
> ```
> R1(config-if)# ipv6 address 2001:db8:1:1::99/128 anycast
> ```
