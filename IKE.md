---
tags:
  - Studies
  - CyberSecurity
  - Acronym
  - Theory
aliases:
  - Internet Key Exchange
description: A protocol used to establish security associations and negotiate cryptographic parameters for IPsec VPNs.
---
The Internet Key Exchange (IKE) protocol is a key management protocol standard. 

IKE is used in conjunction with the [[IPsec]] standard. As shown in the figure, IKE automatically negotiates IPsec security associations and enables IPsec secure communications. 

IKE enhances IPsec by adding features and simplifies configuration for the IPsec standard. Without IKE in place, IPsec configuration would be a complex, manual configuration process that would not scale well.

![[IKE-20240318153059766.webp#invert]]

IKE is a hybrid protocol that implements key exchange protocols inside the [[ISAKMP]] framework.

Instead of transmitting keys directly across a network, IKE calculates shared keys based on the exchange of a series of data packets. 

This disables a third party from decrypting the keys even if the third party captured all of the exchanged data that was used to calculate the keys. IKE uses UDP port 500 to exchange IKE information between the security gateways. UDP port 500 packets must be permitted on any IP interface that is connecting a security gateway peer.

## Phases of Key Negotiation

IKE uses [[ISAKMP]] for phase 1 and phase 2 of key negotiation.

#### Phase One

Phase 1 negotiates a security association (a key) between two IKE peers. The key negotiated in phase 1 enables IKE peers to communicate securely in phase 2. During phase 2 negotiation, IKE establishes keys (security associations) for other applications, such as IPsec.

In Phase 1, two IPsec peers perform the initial negotiation of [[SA|SAs]]. The basic purpose of Phase 1 is to negotiate ISAKMP policy, authenticate the peers, and set up a secure tunnel between the peers. This tunnel will then be used in Phase 2 to negotiate the IPsec policy, as shown in the figure

![[IKE-20240318153532190.webp#invert]]

Phase 1 can be implemented in ==main mode or aggressive mode==. 

When main mode is used, the identities of the two IKE peers are hidden. Aggressive mode takes less time than main mode to negotiate keys between peers. However, since the authentication hash is sent unencrypted before the tunnel is established, aggressive mode is vulnerable to brute-force attacks.

#### Phase Two

The purpose of IKE Phase 2 is to ==negotiate the IPsec security parameters== that will be used to secure the IPsec tunnel, as shown in the figure. IKE Phase 2 is called quick mode and can only occur after IKE has established a secure tunnel in Phase 1. 

[[SA|SAs]] are negotiated by the IKE process [[ISAKMP]] on behalf of [[IPsec]], which needs encryption keys for operation. Quick mode negotiates the IKE Phase 2 SAs. In this phase, the SAs that IPsec uses are unidirectional; therefore, a separate key exchange is required for each data flow.

Quick mode also renegotiates a new IPsec SA when the IPsec SA lifetime expires. Basically, quick mode refreshes the keying material that creates the shared secret key. This is based on the keying material that is derived from the [[DH]] exchange in Phase 1.

![[IKE-20240318153743657.webp#invert]]

## IKE Version Two

IKE version 2, a next-generation key management protocol based on RFC 5996, is an enhancement of the IKE protocol. IKE version 2 supports NAT detection and NAT Traversal (NAT-T) during Phase 1. 

If both VPN devices are NAT-T capable, and if they detect that they are connecting to each other through a NAT device, NAT-T is auto detected and auto negotiated. NAT-T encapsulates ESP packets inside UDP and assigns both the Source and Destination ports as 4500. Now ESP packets can traverse NAT.