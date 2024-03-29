---
tags:
  - Studies
  - Networking
  - CCNA
  - Theory
aliases:
  - Open Shortest Path First Elections
  - DR Elections
  - DR & BDR Elections
description: The elected DR manages communication between OSPF routers.
---
During the [[OSPF]] initialisation process, in most cases a [[DR]], and a [[BDR]], must be elected for each OSPF area. This process is detailed as follows:

1. The OSPF election is triggered. The election can be triggered at two different times. Either during initial OSPF configuration, or when the current DR becomes unavailable.
   
2. If the election was triggered because the current [[DR]] became unavailable, the current [[BDR]] temporarily assumes the role.
   
3. The election is then held. The criteria for winning is to have the highest OSPF interface priority, or if this is equal, to have the highest [[RID]]. Adjusting both of these can be done with the [[OSPF Commands]].