---
tags:
  - Studies
  - Table
  - Commands
  - CyberSecurity
  - Networking
cssclasses:
  - commands
---
IP Source Guard (IPSG) prevents MAC spoofing attacks, like [[ARP Spoofing Attacks|ARP Poisoning]], and IP spoofing attacks which are harder to prevent. It does this by dynamically maintains [[PVACLs]]. Click [[IPSG|here]] for more information.

## Configuration Commands

Ensure that [[DHCP Commands#Configuring DHCP Snooping|DHCP Snooping]] is enabled prior to following this configuration. It is required by [[IPSG]].

| Mode        | Command            | Description                                                                                                                         | Variables `{}` or Options `[]` |
| :---------- | :----------------- | :---------------------------------------------------------------------------------------------------------------------------------- | :----------------------------- |
| `config-if` | `ip verify source` | Enables [[IPSG]] on untrusted ports on trunk or access ports on layer two switches. Can be done for one, or a range, of interfaces. | N/A                            |

## Show Commands

| Command                 | Description                               | Variables `{}` or Options `[]` |
| :---------------------- | :---------------------------------------- | :----------------------------- |
| `show running-config`   | Shows the device's running configuration. | N/A                            |
| `show ip verify source` | Shows the status of IPSG on the device.   | N/A                            |