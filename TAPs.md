---
tags:
  - Studies
  - CyberSecurity
  - Acronym
  - Theory
aliases:
  - Test Access Points
  - Network Taps
---
A network tap is typically a passive splitting device implemented inline between a device of interest and the network. A tap ==forwards all traffic==, including physical layer errors, to an analysis device while also allowing the traffic to reach its intended destination similar to an [[IDS]]. The image below displays a simple use case.

![[TAPs-20240219152615279.webp#invert|488]]

Notice how the tap simultaneously sends both the transmit (TX) data stream from the internal router and the receive (RX) data stream to the internal router on separate, dedicated channels. This ensures that ==all data arrives at the monitoring device in real time==. Therefore, network performance is not affected or degraded by monitoring the connection.

Taps are also typically ==fail-safe==, which means if a tap fails or loses power, traffic between the firewall and internal router is not affected.