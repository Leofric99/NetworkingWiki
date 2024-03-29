---
tags:
  - Studies
  - CyberSecurity
  - Acronym
  - Theory
  - COM512
aliases:
  - Intrusion Prevention System
  - Intrusion Prevention Systems
description:
---
Cost-effective detection and prevention systems, such as [[IDS|Intrusion Detection Systems]] or the more scalable intrusion prevention systems (IPS), are essential for defending against fast-moving and evolving attacks. 

The network architecture integrates these solutions into the ==entry and exit points== of the network. When implementing IDS or IPS, it is important to be familiar with the types of systems available. Both host-based and network-based approaches.

## IPS Operation

1. Malicious traffic is sent to the target host that is inside the network.
2. The traffic is received by an IPS-enabled sensor where it is blocked.
3. The IPS-enabled sensor sends logs to the network security management console.
4. The IPS-enabled sensor kills the traffic by sending it to the 'Bit Bucket'.

![[IPS-20240219124037602.webp#invert|400]]

[[IDS]] and IPS technologies are both deployed as sensors. An IDS or IPS sensor can be in the form of several different devices:

- A router with IPS software
- A device specifically designed to provide dedicated IDS or IPS services
- A hardware module installed in an [[ASAs|Adaptive Security Appliance]], switch, or router

IDS and IPS technologies use [[IDS and IPS Signatures|signatures]] to detect patterns in network traffic. A ==signature is a set of rules== that an IDS or IPS uses to ==detect malicious activity==. Signatures can be used to detect severe breaches of security, to detect common network attacks, and to gather information. IDS and IPS technologies can detect atomic signature patterns (single-packet) or composite signature patterns (multi-packet).

## Pros & Cons of Using an IPS

#### Pros
There are numerous benefits to using an IPS. Most notably that an IPS, unlike an [[IDS]], will stop malicious packets if they are detected. IPS systems can also use [[Stream Normalisation|stream normalisation techniques]].

#### Cons
There are a few drawbacks to an IPS all of which relate to latency, and jitter, usually caused in some way by the IDS's sensor. This is the price to pay for real-time protection.

## Types of IPS

There are two main types of IPS. [[HIPS|Host-Based IPS]] and [[NIPS|Network-Based IPS]].

 