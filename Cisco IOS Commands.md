---
tags:
  - Studies
  - Networking
  - CyberSecurity
  - Commands
  - MOC
description: The MOC for all Cisco IOS Command Notes.
---
Cisco's Internetworking Operating System is a family of proprietary network operating systems used on several router and network switch models manufactured by Cisco Systems. 

> [!note]
> To skip to the list of command pages, click [[Cisco IOS Commands#Command Topic Pages|here]].

## Command Notation

In my command notation, there are several key differences to Cisco's notation.

1. `[]` - Square brackets signify a choice or option. These around a single word indicate that the word is optional, however they usually signify a choice (see item three). If they signify an optional value I will mention this explicitly.
2. `{}` - Curly brackets signify that there is a variable to enter. These around a word signify that the word should be substituted with a number or string.
3. `[x / y]` - As markdown pipe characters break tables, I use a forward slash in place of pipe characters to signify options. This would mean either enter `x` or `y`.
4. `[{x}]` - Combining previous notation, this signifies that `{x}` is optional, but as the `x` is within curly brackets, it is a variable to be substituted with a number or string.
5. Any command which must break this convention will have an explanation accompanying it in the table.


## Configuration Modes

There are three basic configuration modes on Cisco IOS devices. The examples below are for a router, however the device names can be substituted for switches too. Nothing is different here.

|Mode (prompt)|Mode|Mode change (current -> next)|
|---|---|---|
|`R1>`|user EXEC mode AKA _view-only mode_|type `enable` to pass to next mode|
|`R1#`|Privileged EXEC mode|type `configure terminal` to pass to next mode|
|`R1(config)#`|Global configuration mode|N/A|

## Command Topic Pages

```dataview
TABLE WITHOUT ID 
  file.link AS "Name"
FROM #Commands AND !"Templates" AND !"Temporary" AND!#MOC
SORT file.name ASC
```