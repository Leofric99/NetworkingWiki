---
tags:
  - Studies
  - Acronym
  - Theory
  - CyberSecurity
  - COM512
aliases:
  - Network Access Control
description: A security solution that enforces policy on devices that access networks to increase network visibility and reduce risk.
---
The purpose of network access control (NAC) is to allow only authorised and compliant systems (whether managed or unmanaged) to access the network. 

## Overview

NAC ==unifies endpoint security technologies== with user or device authentication and network security policy enforcement. 

A NAC system ==can deny network access== to noncompliant devices, place them in a quarantined area, or give them only restricted access to computing resources, thus keeping insecure nodes from infecting the network.

NAC systems can have the following capabilities:

| Capability                | Description                                                                                                                                                              |
| :------------------------ | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Profiling and visibility  | This recognises and profiles users and their devices before malicious code can cause damage.                                                                             |
| Guest Network Access      | This manages guests through a customizable, self-service portal that includes guest registration, guest authentication, guest sponsoring, and a guest management portal. |
| Security Posture Checking | This evaluates security-policy compliance by user type, device type, and operating system.                                                                               |
| Incident Response         | This mitigates network threats by enforcing security policies that block, isolate, and repair noncompliant machines without administrator attention.                     |
NAC systems should extend NAC to all network access methods, including access through [[LANs]], remote-access gateways, and wireless access points.

The Cisco [[ISE|Identity Services Engine]] combines [[AAA]] and network device profiling into a single system.

## Functions

The goal of NAC systems is to ensure that only hosts that are authenticated and have had their security posture examined and approved are permitted onto the network.

An example of a Network Access Control setup is shown below. It involves many network devices working together:

![[NAC-20240301152347048.webp#invert|550]]

