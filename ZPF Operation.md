---
tags:
  - Studies
  - CyberSecurity
aliases:
  - Zone-based Policy Firewall Operation
---
Policies identify actions that the ZPF will perform on network traffic. Three possible actions can be configured to process traffic by protocol, source and destination zones (zone pairs), and other criteria.

| Action | Description |
|:-------|:------------|
| Inspect       | This performs Cisco IOS stateful packet inspection.            |
| Drop       | This is the same as a deny statement in an ACL. A log option is available to log the rejected packets.            |
| Pass       | This is the same as a permit statement in an ACL. The pass action does not track the state of connections or sessions within the traffic.            |  
## Rules for Transiting Traffic

Traffic transiting through router interfaces is subject to several rules governing interface behaviour. The rule behaviour is dictated by the [[ZPF Policy Operation|ZPF policy operation]]. The table below summarises these rules.

|Source Interface Member of Zone?|Destination Interface Member of Zone?|Zone-Pair Exists?|Policy Exists?|Result|
|---|---|---|---|---|
|NO|NO|N/A|N/A|PASS|
|YES|NO|N/A|N/A|DROP|
|NO|YES|N/A|N/A|DROP|
|YES (private)|YES (private)|N/A|N/A|PASS|
|YES (private)|YES (public)|NO|N/A|DROP|
|YES (private)|YES (public)|YES|NO|PASS|
|YES (private)|YES (public)|YES|YES|INSPECT|

The rules depend on whether or not the ingress and egress interfaces are members of the same zone.

## The Self Zone

The self zone is the router itself and includes all of the IP addresses assigned to the router interfaces. This is traffic that originates at the router or is addressed to a router interface.

Specifically, the traffic is either for device management, for example SSH, or traffic forwarding control, such as routing protocol traffic. The rules for a ZPF are different for the self zone.

The rules depend on whether the router is the source or the destination of the traffic, as shown in the table. If the router is the source or the destination, then all traffic is permitted. The only exception is if the source and destination are a zone-pair with a specific service-policy. In that case, the policy is applied to all traffic.

|Source Interface Member of Zone?|Destination Interface Member of Zone?|Zone-Pair Exists?|Policy Exists?|Result|
|---|---|---|---|---|
|YES (self zone)|YES|NO|N/A|PASS|
|YES (self zone)|YES|YES|NO|PASS|
|YES (self zone)|YES|YES|YES|INSPECT|
|YES|YES (self zone)|NO|N/A|PASS|
|YES|YES (self zone)|YES|NO|PASS|
|YES|YES (self zone)|YES|YES|INSPECT|
