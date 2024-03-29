---
tags:
  - "#Studies"
  - Networking
  - CCNA
  - Theory
description: An IPv6 address identifier for a group of interfaces (typically on different nodes).
---
[[IPv6]] multicast addresses are one-to-many. They are used to address a range of devices at the same time. It uses the address space `FF00::8` from `FF00::` to an ==all Fs== range.

## IPv6 Multicast Address Scopes

IPv6 Multicast Address Scopes define how far an [[IPv6]] multicast packet should be forwarded. There are four different scopes.

| Name               | Address Prefix | Description                                                                                                                                                                       |
| :----------------- | :------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Interface-local    | `FF01`         | The packet doesn't leave the device. Can be used to send traffic within the device.                                                                                               |
| Link-local         | `FF02`         | Different to [[Link-local Addresses]]. These are specifically for multicast addresses. The packet remains in the local subnet. Routers will not route the packet between subnets. |
| Site-local         | `FF05`         | The packet can be forwarded by routers. Should be limited to a single physical location.                                                                                          |
| Organisation-local | `FF08`         | Wider in scope than site-local (within an entire company or organisation).                                                                                                        |
| Global             | `FF0E`         | No Boundaries. Possible to be routed over the internet.                                                                                                                           |
