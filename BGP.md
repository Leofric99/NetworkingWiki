---
tags:
  - Studies
  - Acronym
  - Networking
  - Theory
  - CCNA
aliases:
  - Border Gateway Protocol
description: Facilitates the exchange of routing and reachability information between different autonomous systems.
---
Border Gateway Protocol (BGP) is a standardised gateway protocol that ==facilitates the exchange of routing and reachability information== between different autonomous systems (AS) on the internet.

> [!info]- QRH
> Click [[QRH-BGP.pdf|here]] for the quick reference handbook.

BGP is used when an [[AS]] has connections to multiple other [[AS|ASes]]. This is known as multi-homed. Two routers exchanging BGP routing information are known as BGP peers.

## When *not* to use BGP

BGP ==should not be used when== one of the following conditions exist:

- There is a single connection to the Internet or another [[AS]]. Known as single-homed.
- When there is a limited understanding of BGP.

## Differing Implementation Methods

There are three common ways an organisation can implement BGP in a multi-homed environment:

- Default Route Only
- Default Route and ISP Routes
- All Internet Routes (this would include routes to over 550,000 networks)

## Types of BGP

There are two different types of BGP. [[eBGP]] and [[iBGP]].

![[eBGP]]

![[iBGP]]