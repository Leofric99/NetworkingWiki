---
tags:
  - Studies
  - CyberSecurity
  - Theory
---
A layered defence uses ==different types of firewalls== that are combined in layers to add depth to the security of an organisation. 

Policies can be enforced between the layers and inside the layers. These policy enforcement points determine whether traffic is forwarded or discarded.

A layered defence approach is not all that is needed to ensure a safe internal network. A network administrator must consider many factors when building a complete in-depth defence:

- [[Firewalls]] typically do not stop intrusions that come from hosts within a network or zone.
- They do not protect against rogue access point installations.
- They do not replace backup and disaster recovery mechanisms resulting from attack or hardware failure.
- They are no substitute for informed administrators and users.

> [!example]-
> 1. Any traffic that comes in from an untrusted network first encounters a filter on the edge router. 
>    
> 2. If allowed by the policy, the traffic goes to the screened firewall or bastion host system.
>    
> 3. This then analyses the packet using more rules and discards any suspect packets.
>    
> Once packets have been checked by a [[Firewalls|firewall]] or [[Bastion Hosts|bastion host]], they move on to an interior screening router. The traffic moves to the internal destination host *only* after successfully passing through all policy enforcement points between the outside router and the inside network.
> 
> This type of [[DMZ]] setup is called a ==screened subnet configuration==.

## Layered Network Sections

| Layer Name     | Purpose                                                                                                                       |
|:---------------|:------------------------------------------------------------------------------------------------------------------------------|
| Network Core   | This section protects against malicious software and traffic anomalies, enforces network policies, and ensures survivability. |
| Perimeter      | This section secures the boundaries between zones.                                                                            |
| Communications | This section provides information assurance.                                                                                  |
| Endpoint       | This section provides identity and device security policy compliance.                                                         |  
## Layered Network Best Practices

This partial list of best practices can serve as a starting point for a firewall security policy.

- Position firewalls at security boundaries. Firewalls are a critical part of network security, but it is unwise to rely exclusively on a firewall for security.
- Deny all traffic by default.
- Permit only services that are needed.
- Ensure that physical access to the firewall is controlled.
- Regularly monitor firewall logs.
- Practice change management for firewall configuration changes.
- Remember that firewalls primarily protect from technical attacks originating from the outside.