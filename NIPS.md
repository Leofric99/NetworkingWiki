---
tags:
  - Studies
  - CyberSecurity
  - Acronym
  - Theory
---
A network-based IPS can be ==implemented using a dedicated or non-dedicated IPS device== such as a router. Network-based IPS implementations are a critical component of intrusion prevention. Host-based [[IDS]]/[[IPS]] solutions such as [[HIPS]] must be integrated with a network-based IPS implementation to ensure a robust security architecture.

## Network-Based IPS Operation

Sensors ==detect malicious and unauthorised activity in real-time== and can take action when required. As shown in the image, sensors are deployed at designated network splits. This enables security managers to monitor network activity while it is occurring, regardless of the location of the attack target.

![[NIPS-20240219132601083.webp#invert]]

## Network-Based IPS Implementation

Network-based IPS Sensors can be implemented in several ways:

- On a Cisco Firepower appliance
- On an [[ASAs|ASA]] firewall device
- On an [[ISR]] router
- As a virtual Next-Generation IPS (NGIPSv) for VMware

An example of a network-based IPS is the Cisco Firepower NGIPS. It is tuned for intrusion prevention analysis. The underlying operating system of the platform is stripped of unnecessary network services, and essential services are secured. This is known as ==hardening==.

The hardware of all network-based sensors includes three components:

- **NIC** - The network-based IPS must be able to connect to any network, such as Ethernet, Fast Ethernet, and Gigabit Ethernet.
- **Processor** - Intrusion prevention requires CPU power to perform intrusion detection analysis and pattern matching.
- **Memory** - Intrusion detection analysis is memory-intensive. Memory directly affects the ability of a network-based IPS to efficiently and accurately detect an attack.

Network-based IPS gives security managers real-time security insight into their networks regardless of growth. Additional hosts can be added to protected networks without requiring more sensors. 

Additional sensors are only required when their rated traffic capacity is exceeded, when their performance does not meet current needs, or when a revision in security policy or network design requires additional sensors to help enforce security boundaries. When new networks are added, additional sensors are easy to deploy.