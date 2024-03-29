---
tags:
  - MOC
  - Studies
  - Networking
aliases:
  - Cisco Certified Network Associate
colour: R190 G50 B50
description: The MOC for all Computer Networking knowledge.
---
Click [[Home Page|here]] to return to the Home Page MOC.
## Cisco Certified Network Associate

The CCNA, or Cisco Certified Network Associate, is a widely recognised certification in the field of computer networking. 

It validates the foundational skills and knowledge required to install, operate, and troubleshoot small to medium-sized enterprise networks, making it a valuable credential for individuals pursuing a career in computer systems and networks engineering.

```dataview
TABLE WITHOUT ID 
  file.link AS "Title", description as Description
FROM #Networking AND #Theory AND #CCNA AND !"Templates" AND !#MOC AND #COM412 OR #COM414 OR #COM515 AND !#Assessment
SORT file.name ASC
```

#### Commands

```dataview
TABLE WITHOUT ID 
  file.link AS "Title"
FROM #Networking AND #Commands AND #CCNA AND !"Templates" AND !#MOC AND !#Assessment
SORT file.name ASC
```

## All Concepts

All concepts within Networking regardless of whether it's CCNA, CCNP, or beyond. Excludes commands. For commands see [[Networking Knowledge Base#All Commands]]. There will be some crossover with Cyber Security here.

```dataview
TABLE WITHOUT ID 
  file.link AS "Title", description as Description
FROM #Networking AND #Theory OR #Acronym AND !"Templates" AND !#MOC
SORT file.name ASC
```

## All Commands

All command pages regardless of whether it's CCNA, CCNP, or beyond.

```dataview
TABLE WITHOUT ID 
  file.link AS "Title"
FROM #Networking AND #Commands AND !"Templates" AND !#MOC AND !"Temporary" AND !#Assessment
SORT file.name ASC
```