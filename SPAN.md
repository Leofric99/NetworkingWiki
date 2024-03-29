---
tags:
  - Studies
  - CyberSecurity
  - Acronym
  - Networking
  - Theory
---
  SPAN (Switched Port Analyser) is a network feature that allows the monitoring or mirroring of traffic from one or more ports on a network switch.
  
  > [!tldr]
  > It enables administrators to capture and ==analyse network traffic== for troubleshooting, security, and performance monitoring purposes. SPAN directs a copy of the network packets to a designated monitoring port, ensuring that the ==original traffic continues to flow== normally.

## SPAN Terms

The table identifies and describes terms used by the SPAN feature.

| **SPAN Term**               | **Description**                                                                                                                 |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| **Ingress traffic**         | Traffic that enters the switch.                                                                                                 |
| **Egress traffic**          | Traffic that leaves the switch.                                                                                                 |
| **Source (SPAN) port**      | Source ports are monitored as traffic entering them is replicated (mirrored) to the destination ports.                          |
| **Destination (SPAN) port** | A port that mirrors source ports. Destination SPAN ports often connect to analysis devices such as a packet analyser or an IDS. |

## SPAN Operation

The image below shows a switch that interconnects two hosts and mirrors traffic to an [[IDS]] and network management server.

![[SPAN-20240219153616839.webp#invert|441]]

The switch will forward ingress traffic on `F0/1` and egress traffic on `F0/2` to the destination SPAN port `G0/1` that connects to an [[IDS]]. The association between source ports and a destination port is called a ==SPAN session==. 

In a single session, ==one or multiple ports can be monitored==. On some Cisco switches, session traffic can be copied to more than one destination port. Alternatively, a source VLAN can be specified in which all ports in the source VLAN become sources of SPAN traffic. Each SPAN session can have ports or VLANs as sources, but not both.

> [!note]-
> A variation of SPAN called Remote SPAN [[RSPAN]] enables a network administrator to use the flexibility of VLANs to monitor traffic on remote switches.

For information on configuring SPAN in Cisco IOS, see [[SPAN Commands]].