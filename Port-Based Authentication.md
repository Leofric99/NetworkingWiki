---
tags:
  - Studies
  - CyberSecurity
  - Theory
  - COM512
aliases:
  - IEEE 802.1X
  - 802.1X
description: A port-based access control and authentication protocol that restricts unauthorised workstations from connecting to a LAN.
---
The [[IEEE]] 802.1X standard defines a port-based access control and authentication protocol that ==restricts unauthorised workstations== from connecting to a LAN through publicly accessible switch ports. 

Until a workstation is authenticated, 802.1X access control enables only [[EAPoL]], [[CDP]], and [[STP]] traffic through the port to which the workstation is connected. After authentication succeeds, normal traffic can pass through the port.

## 802.1X Roles

The authentication server authenticates each workstation that is connected to a switch port before making available any services offered by the switch or the [[LANs|LAN]].

This image shows that, with 802.1X port-based authentication, the ==devices== in the network have ==specific roles==.


![[Port-Based Authentication-20240301152912325.webp#invert|500]]

| Role                   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Supplicant (Client)    | The device (workstation) that requests access to [[LANs\|LAN]] and switch services and then responds to requests from the switch. The workstation must be running 802.1X-compliant client software. (The port that the client is attached to is the supplicant client in the IEEE 802.1X specification.)                                                                                                                                                                                                                                                                           |
| Authenticator (Switch) | This device controls physical access to the network based on the authentication status of the client. The switch acts as an intermediary (proxy) between the client (supplicant) and the authentication server, requesting identifying information from the client, verifying that information with the authentication server, and relaying a response to the client. The switch uses a RADIUS software agent, which is responsible for encapsulating and de-encapsulating the [[EAP]] (Extensible Authentication Protocol) frames and interacting with the authentication server. |
| Authentication Server  | This server performs the actual authentication of the client. The authentication server validates the identity of the client and notifies the switch whether the client is authorized to access the LAN and switch services. Because the switch acts as the proxy, the authentication service is transparent to the client. The RADIUS security system with EAP extensions is the only supported authentication server.                                                                                                                                                            |
## 802.1X Message Exchange

The following image shows the message exchange which occurs when port-based authentication using 802.1X takes place.

![[Port-Based Authentication-20240301154038275.webp#invert]]

If the client is ==successfully authenticated== (the switch receives an *“accept”* frame from the authentication server), the port state changes to authorised, and all frames from the authenticated client are enabled through the port.

If the ==authentication fails==, the port remains in the unauthorised state, but authentication can be retried. If the authentication server cannot be reached, the switch can retransmit the request. If no response is received from the server after the specified number of attempts, authentication fails, and network access is not granted.

