---
tags:
  - Studies
  - Commands
  - CyberSecurity
aliases:
  - ZPF Cisco IOS Commands
  - Zone-based Policy Firewall Commands
cssclasses:
  - commands
---
## Configuration Commands

There are five initial steps to configuring a [[ZPFs|ZPF]]. These steps are as follows:

1. Create the zones
2. Identify traffic with a class-map.
3. Define an action with a policy-map.
4. Identify a zone pair and match it to a policy-map.
5. Assign zones to the appropriate interfaces.

*Note: there is some overlap here with [[ZPF Design]].*

### Creating the Zones

When creating the zones, there are three questions you must ask yourself: 

- *What interfaces should be included?*
- *What should I name the zones?*
- *What traffic needs to be permitted between the zones, in which direction(s)?*.

Then, to create the zones, use the following command:

| Mode   | Command                     | Description                                                  |
| :----- | :-------------------------- | :----------------------------------------------------------- |
| Config | `zone security {zone-name}` | Creates a zone, names it, and enters `config-sec-zone` mode. |
### Identifying the Traffic with a Class Map

The second step is to use a class-map to identify the traffic to which a policy will be applied.

A class is a way of identifying a set of packets based on its contents using “match” conditions. Typically, you define a class so that you can apply an action to the identified traffic that reflects a policy. A class is defined with class-maps.

The table below shows the syntax for the `class-map` command. There are several types of class-maps. For a ZPF configuration, use the `inspect` keyword to define a class-map.

| Mode     | Command                                                          | Description                                        | Variable Name                                                                     |
| :------- | :--------------------------------------------------------------- | :------------------------------------------------- | --------------------------------------------------------------------------------- |
| `config` | `class-map type {type} [match-any / match-all] {class-map-name}` | Creates a class-map and enters `config-cmap` mode. | `{type}` is `inspect` for ZPF. `{class-map-name}` is your desired class-map name. |
In the context of this command, `match-any` means that packets must meet one of the match criteria to be considered a member of the class, and `match-all` means that packets must meet all of the match criteria to be considered a member of the class.

#### Config-cmap Mode

The command below shows the syntax for the match statements in `config-cmap` sub-configuration mode. 

| Mode | Command | Description | Variables |
| :--- | :--- | :--- | ---- |
| `config-cmap` | `match {choice-type} {choice-option}` | Matches traffic to either an ACL, protocol, or another class map. | `{choice-type}` can be either `access-group`, `protocol`, or `class-map`. `{choice option}` can be either the ACL name or number, the protocol name, or the class map name. |
### Define an Action with a Class Map

The third step is to use a policy-map to define what action should be taken for traffic that is a member of a class. The command below shows is used to configure a policy-map. An action is a specific functionality. It is typically associated with a traffic class. For example, **inspect**, **drop**, and **pass** are actions.

| Mode            | Command                                    | Description                             | Variables                                                                           |
| :-------------- | :----------------------------------------- | :-------------------------------------- | ----------------------------------------------------------------------------------- |
| `config`        | `policy-map type {type} {policy-map-name}` | Creates a new policy-map.               | `{type}` is `inspect` for ZPF. `{policy-map-name}` is your desired policy-map name. |
| `config-pmap`   | `class type {type} {class-map-name}`       | Creates a class-map for the policy-map. | `{type}` is `inspect` for ZPF. `{class-map-name}` is your desired class-map name.   |
| `config-pmap-c` | `[inspect / drop / pass]`                  | Sets the action for the class-map.      | Defined in the [[ZPF Commands#Class Map Options fold]].                             |

### Identifying a Zone-Pair & Matching to a Policy

The fourth step is to identify a zone pair and associate that zone pair to a policy-map. The table below shows the command syntax.

| Mode | Command | Description | Variables |
| :--- | :--- | :--- | ---- |
| `config` | `zone-pair security zone-pair-name source [{source-zone-name} / self] destination [{destination-zone-name} / self]` | Creates a zone-pair. | `{source-zone-name}` is the name of the source zone for the pair. `{destination-zone-name}` is the name of the destination zone for the pair. |
| `config-sec-zone-pair` | `service-policy type {type} {policy-map-name}` | Attaches a policy map and associated action to the zone-pair. | `{type}` is `inspect` for ZPF.  `{policy-map-name}` is the desired policy-map name to attach.  |

### Assigning Zones to Interfaces

The fifth step is to assign zones to the appropriate interfaces. Associating a zone to an interface will immediately apply the service-policy that has been associated with the zone. If no service-policy is yet configured for the zone, all transit traffic will be dropped. 

Use the **zone-member security** command to assign a zone to an interface, as shown in the example below.

| Mode | Command | Description | Variables |
| :--- | :--- | :--- | ---- |
| `config-if` | `zone-member security {zone-name}` | Assigns a zone to an interface. | `{zone-name}` is the name of the zone you want to apply. |

## Show Commands

| Command | Description | Variables |
| :--- | :--- | :--- |
| `show run` | Shows the running config of the router. | N/A |
| `show policy-map type {type}` | Shows the policy-map. | `{type}` is `inspect` for ZPF. |
| `show policy-map type {type} zone-pair sessions` | Shows the policy-map zone-pair and details about traffic. | `{type}` is `inspect` for ZPF. |
| `show class-map type {type}` | Shows class-map section of policy-map. | `{type}` is `inspect` for ZPF. |
| `show zone {zone-name}` | Shows information about a particular zone. | `{zone-name}` is for the desired zone. |
| `show zone-pair {zone-name}` | Shows information about a particular zone-pair. | `{zone-name}` is for the desired zone. |
## Class Map Options 

The table below details the three options for setting the action for the class-map:

|Parameter|Description|
|---|---|
|`inspect` |An action that offers state−based traffic control. The router maintains session information for TCP and UDP and permits return traffic.|
|`drop` |Discards unwanted traffic|
|`pass` |A stateless action that allows the router to forward traffic from one zone to another|
