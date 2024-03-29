---
tags:
  - Studies
  - CyberSecurity
  - Theory
description: An attack which involves pretending to be a rogue DHCP server.
---
A [[DHCP]] spoofing attack occurs when a rogue DHCP server is connected to the network and ==provides false IP configuration parameters== to legitimate clients. A rogue server can provide a variety of misleading information:

| Bogus Information     | Description                                                                                                                                                                                                                                                  |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Wrong Default Gateway | The rogue server provides an invalid gateway, or its own IP address, to create a man-in-the-middle attack. This may go entirely undetected as the intruder intercepts the data flow through the network and then forwards it on to the real default gateway. |
| Wrong DNS Server      | The rogue server provides an incorrect DNS server address that points the user to a nefarious website.                                                                                                                                                       |
| Wrong IP Address      | The rogue server provides an invalid IP address, effectively creating a DoS attack on the DHCP client.                                                                                                                                                       |

## How it Works

First, a threat actor successfully ==connects a rogue DHCP server== to a switch port on the same subnet and VLANs as the target clients. The goal of the rogue server is to provide clients with false IP configuration information.

![[DHCP Spoofing Attacks-20240302141026662.webp#invert|370]]

Then, a legitimate client connects to the network and requires IP configuration parameters. Therefore, the ==client broadcasts a DHCP Discovery== request looking for a response from a DHCP server. Both servers will receive the message and respond.

![[DHCP Spoofing Attacks-20240302141125344.webp#invert|400]]

The legitimate DHCP server responds with valid IP configuration parameters. However, the rogue server also responds with a DHCP offer containing IP configuration parameters defined by the threat actor. The client will reply to the first offer received.

![[DHCP Spoofing Attacks-20240302141223811.webp#invert|400]]

The rogue offer was received first, and therefore, the client broadcasts a DHCP request accepting the IP parameters defined by the threat actor. The legitimate and rogue server will receive the request.

![[DHCP Spoofing Attacks-20240302141306776.webp#invert|400]]

The rogue server unicasts a reply to the client to acknowledge its request. The legitimate server will cease communicating with the client.

![[DHCP Spoofing Attacks-20240302141358424.webp#invert|400]]

## Mitigation Techniques

For information about mitigation, see [[DHCP Attacks#DHCP Attack Mitigation]].