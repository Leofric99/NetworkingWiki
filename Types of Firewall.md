---
tags:
  - Studies
  - CyberSecurity
aliases:
  - Types of Firewalls
---
There are four main types of firewall as follows.
## Packet Filtering (Stateless) Firewalls

Packet filtering firewalls are usually part of a router firewall, which permits or denies traffic based on Layer 3 and Layer 4 information. 

They are stateless firewalls that use a simple ==policy table look-up== that filters traffic based on specific criteria.

![[Types of Firewall-20240215122203040.webp#invert|384]]

## Stateful Firewalls

Stateful firewalls are the most versatile and the most common firewall technologies in use. They provide stateful packet filtering by ==using connection information== maintained in a state table. Stateful filtering is a firewall architecture that is classified at the network layer. 

It also analyses traffic at OSI Layer 4 and Layer 5.

![[Types of Firewall-20240215122243376.webp#invert|288]]

## Application Gateway Firewalls

An application gateway firewall (proxy firewall), filters information at Layers 3, 4, 5, and 7 of the OSI reference model. Most of the firewall control and filtering is done in software. 

When a client needs to access a remote server, it connects to a proxy server. The proxy server connects to the remote server on behalf of the client. Therefore, the server only sees a connection from the proxy server.

![[Types of Firewall-20240215122317587.webp#invert|370]]

## Next Generation Firewalls (NGFW)

Next-generation firewalls (NGFW) go beyond stateful firewalls by providing:

- Integrated intrusion prevention
- Application awareness and control to see and block risky apps
- Upgrade paths to include future information feeds
- Techniques to address evolving security threats

## Other Firewall Types

Other methods of implementing firewalls include:

- **Host-based (server and personal) firewall** - A PC or server with firewall software running on it.
- **Transparent firewall** - Filters IP traffic between a pair of bridged interfaces.
- **Hybrid firewall** - A combination of the various firewall types. For example, an application inspection firewall combines a stateful firewall with an application gateway firewall.