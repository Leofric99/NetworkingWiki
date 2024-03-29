---
tags:
  - Studies
  - Acronym
  - CyberSecurity
  - Theory
aliases:
  - Authentication Authorisation and Accounting
description: Provides the primary framework to set up access control.
---
AAA network security services provide the ==primary framework to set up access control on a network device==. 

AAA is a way to control who is permitted to access a network (authenticate) and what they can do while they are there (authorise). AAA also allows auditing of the actions that users perform while accessing the network (accounting).

There are three main parts to it:

- **Authentication** - Users and administrators must ==prove their identity before accessing== the network and network resources.
  
- **Authorisation** - After the user is authenticated, authorisation services determine ==which resources== the user can access and ==which operations== the user is allowed to perform.
  
- **Accounting and auditing** - Accounting ==records what the user does==, including what is accessed, the amount of time the resource is accessed, and any changes that were made. Accounting keeps track of how network resources are used.

## Authentication

AAA Authentication can be used to authenticate users for administrative access or it can be used to authenticate users for remote network access. Cisco provides ==two common methods== of implementing AAA services:

## Local AAA Authentication

Local AAA uses a ==local database for authentication==. This method is sometimes known as self-contained authentication. 

This method stores usernames and passwords locally in the Cisco router, and users authenticate against the local database, as shown in the image below. This database is the same one that is required for establishing role-based CLI. Local AAA is ideal for small networks.

![[Authentication, Authorisation, and Accounting-20240213121044701.webp#invert|500]]

## Server Based AAA Authentication

With the server-based method, the router ==accesses a central AAA server==. The central AAA server contains the usernames and password for all users. 

The router uses either the Remote Authentication Dial-In User Service (RADIUS) or Terminal Access Controller Access Control System (TACACS+) protocols to communicate with the AAA server. 

When there are ==multiple routers and switches, server-based AAA is more appropriate== because accounts can be administered from a central location rather than on individual devices.

![[Authentication, Authorisation, and Accounting-20240213121116394.webp#invert|500]]

1. The client establishes a connection with the router.
2. The AAA router prompts the user for a username and password.
3. The router authenticates the username and password using a AAA server.
4. The user is provided access to the network based on information on the remote AAA server.

## Authorisation

==After users are successfully authenticated== against the selected AAA data source, either local or server-based, they are then authorized for specific network resources.

![[Authentication, Authorisation, and Accounting-20240213121229889.webp#invert|500]]

1. When a user has been authenticated, a session is established between the router and the server.
2. The router requests Authorisation from the AAA server for the client's requested service.
3. The AAA server returns a PASS/FAIL for Authorisation.

Authorisation ==controls what users can and cannot do on the network== after they are authenticated. Authorisation is automatic and does not require users to perform additional steps after authentication. Authorisation is implemented ==immediately after the user is authenticated==.
## Accounting

AAA Accounting ==collects and reports usage data==. This data can be used for such purposes as auditing or billing. The collected data might include the start and stop connection times, the commands executed, the number of packets, and the number of bytes.

==Accounting is implemented using a AAA server==. This service reports usage statistics back to the ACS server. These statistics can be extracted to create detailed reports about the configuration of the network. 

The AAA servers keep a detailed log of ==exactly what the authenticated user does== on the device, as shown in the figure.

![[Authentication, Authorisation, and Accounting-20240213121357468.webp#invert|500]]

1. When a user has been authenticated, the AAA accounting process generates a start message to begin the accounting process.
2. When the user finishes, a stop message is recorded and the accounting process ends.

To view commands associated with AAA, see [[AAA Commands]].