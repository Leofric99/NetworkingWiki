---
tags:
  - Studies
  - Table
  - Networking
  - Commands
cssclasses:
  - commands
---
You might find it convenient to execute the following sequence of commands before doing any other configuration or troubleshooting tasks on your Cisco device, in order to improve your workflow on the terminal.

| Command                                                    | Additional Notes                                                                                                             |
| ---------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| ``CDevice> enable``                                        | N/A                                                                                                                          |
| ``CDevice# configure terminal``                            | N/A                                                                                                                          |
| ``CDevice(config)# no ip domain-lookup``                   | disable DNS lookup                                                                                                           |
| ``CDevice(config)# cdp run``                               | ensure CDP is running :bulb:(although it is running on Cisco devices by default)                                             |
| ``CDevice(config)# line console 0``                        | N/A                                                                                                                          |
| ``CDevice(config-line)# logging synchronous``              | N/A                                                                                                                          |
| ``CDevice(config-line)# history size [lines]``             | specify the size (number of lines) for the history of executed commands (you can view your history with ``R1#show history``) |
| ``CDevice(config-line)# exec-timeout [minutes] [seconds]`` | N/A                                                                                                                          |
| ``CDevice(config-line)# end``                              | exit to EXEC privileged mode, where the next command will be executed                                                        |
| ``CDevice# copy running-config startup-config``            | Saves the running configuration to the NVRAM                                                                                 |

*Note: If there are non-Cisco devices on your network, you might also want to enable LLDP (Link-Layer Discovery Protocol).*

```
CDevice(config)# lldp run
```
