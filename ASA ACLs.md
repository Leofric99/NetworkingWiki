---
tags:
  - Studies
  - CyberSecurity
  - Acronym
  - Theory
  - Networking
aliases:
  - Adaptive Security Appliance Access Control Lists
description: A method of controlling access in a network by preventing defined traffic from entering or exiting on ASAs.
---
A Cisco [[ASAs|ASA]] provides basic traffic filtering capabilities with [[ACLs]]. 

ACLs control access in a network by preventing defined traffic from entering or exiting. In addition, an ACL can be used to select traffic to which a feature will apply, thereby performing a matching service rather than a control service.

## Differences to IOS [[ACLs]]

There are many similarities between ASA ACLs and IOS ACLs, but also a few differences. Here are those differences:

| Differences                                                                                 |
| ------------------------------------------------------------------------------------------- |
| The ASA uses a network mask (e.g., 255.255.255.0) and not a wildcard mask (e.g. 0.0.0.255). |
| ACLs are always named instead of numbered.                                                  |
| By default, interface security levels apply access control without an ACL configured.       |
|                                                                                             |
## Types of ASA ACL Filtering

ACLs on a security appliance can be used not only to filter packets that are passing through the appliance but also to filter packets destined for the appliance.

| Filtering Type                   | Description                                                                                                                                                                                                 |
| -------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Through-traffic filtering**    | Traffic passing through the security appliance from one interface to another. Configured in two steps: setting up an ACL and applying it to an interface.                                                   |
| **To-the-box-traffic filtering** | Also known as a management access rule. Applies to traffic terminating at the ASA, filtering traffic destined for the ASA's control plane. Configured in one step with additional rules for access control. |

ASA devices ==differ== from their router counterparts because of ==interface security levels==. By default, security levels apply access control without an ACL configured. 

For instance, traffic from a more secure interface, such as security level 100, is allowed to access less secure interfaces, such as level 0. Traffic from a less secure interface is ~~blocked~~ from accessing more secure interfaces.

> [!example]-
> For example, a host from the inside network with security level 100 can access the outside interface with security level 0 as shown below.
> 
> ![[ASA ACLs-20240318105400804.webp#invert|500]]
> 
> However, a host from an outside interface with security level 0 cannot access the inside higher-level interface, as shown below. Less secure interfaces are blocked from accessing more secure interfaces. If required, an ACL would have to be explicitly configured to permit traffic from a lower security level to a higher security level.
> 
> ![[ASA ACLs-20240318105448515.webp#invert|500]]
> 
> To allow connectivity between interfaces with the same security levels, the `same-security-traffic permit inter-interface` global configuration mode command is required. 
> 
> To enable traffic to enter and exit the same interface, such as when encrypted traffic enters an interface and is then routed out the same interface unencrypted, use the `same-security-traffic permit intra-interface` global configuration mode command.

## Types of ASA ACLs

[[ASAs]] support five types of access lists:

| Access List Type        | Description                                                                                                                                                                                                                                                                                                |
|-------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Extended access list    | The most common type of ACL. Contains one or more ACEs to specify source and destination addresses, protocol, ports (for TCP or UDP), or the ICMP type (for ICMP). Used for traffic filtering and identifying traffic for various features.                                                                                                               |
| Standard access list    | Unlike IOS standard ACLs that identify the source host/network, ASA standard ACLs are used to identify destination IP addresses. Typically used for OSPF routes and in route maps for OSPF redistribution. Cannot be applied to interfaces for traffic control.                                                                                           |
| EtherType access list   | Configured only if the security appliance is running in transparent mode. Used to filter traffic based on EtherType.                                                                                                                                                                                       |
| Webtype access list     | Used for filtering clientless SSL VPN traffic. These ACLs can deny access based on URLs or destination addresses.                                                                                                                                                                                           |
| IPv6 access list        | Determines IPv6 traffic to block or forward at router interfaces.                                                                                                                                                                                                                                          |

The table provides examples of the uses of ==extended ACLs==.

|**ACL Use**|**Description**|
|---|---|
|Control network access for IP traffic|The ASA does not allow any traffic from a lower security interface to a higher security interface unless it is explicitly permitted by an extended access list.|
|Identify traffic for AAA rules|AAA rules use access lists to identify traffic.|
|Identify addresses for NAT|Policy NAT lets you identify local traffic for address translation by specifying the source and destination addresses in an extended access list.|
|Establish VPN access|Extended access list can be used in VPN commands.|
|Identify traffic for Modular Policy Framework (MPF)|- Access lists can be used to identify traffic in a class map, which is used for features that support MPF.<br>- Features that support MPF include TCP, general connection settings, and inspection.|

The table provides examples of uses of ==standard ACLs==.

|**ACL Use**|**Description**|
|---|---|
|Identify OSPF destination network in route maps|- Standard access lists include only the destination address.<br>- It can be used to control the redistribution of OSPF routes.|
|VPN filters|Filter traffic for LAN-to-LAN (L2L), Cisco VPN Client, and the Cisco AnyConnect Secure Mobility Client traffic.|

The table provides an example for the use of ==IPv6 ACLs==.

|**ACL Use**|**Description**|
|---|---|
|Control network access for IPv6 networks|Can be used to add and apply access lists to control traffic in IPv6 networks.|

## ASA ACLs with Object Groups

Object grouping is a way to group similar items together to reduce the number of ACEs. 

By grouping like objects together, object groups can be used in an ACL instead of having to enter an ACE for each object separately. Without object grouping, the security appliance configuration may contain thousands of lines of ACEs, which can become difficult to manage.

The example displays a condensed ACL syntax.

The security appliance follows the multiplication factor rule when ACEs are defined. For example, if two outside hosts need to access two internal servers running HTTP and SMTP services, the ASA will have eight host-based ACEs. They should be calculated as follows:

*Number of ACEs = (2 outside hosts) x (2 internal servers) x (2 services) = 8*

Object grouping can cluster network objects into one group and outside hosts into another, as shown in the following syntax. The security appliance can also combine both TCP services into a service object group.

```
access-list {id} extended [deny / permit] {protocol}  object-group {source_net-obj-grp_id} object-group {dest_net-obj-grp_id} object-group {service-obj-grp_id}
```