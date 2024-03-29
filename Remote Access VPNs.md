---
tags:
  - "#Studies"
  - Networking
  - CCNA
  - Theory
  - CyberSecurity
aliases:
  - Remote Access Virtual Private Networks
description: "[[VPNs]] which create secure tunnels for remote users to access private networks."
---
A remote-access VPN is ==dynamically created== to establish a secure connection between a client and a VPN terminating device. For example, a remote access [[SSL]] [[VPNs|VPN]] is used when you check your banking information online.

![[VPNs-20240318120723963.webp#invert]]

## How it Works

As shown in the image, remote-access VPNs let remote and mobile users securely connect to the enterprise by creating an ==encrypted tunnel==. Remote-access VPNs also allow contractors and partners to have limited access to the specific servers, web pages, or files as required.

![[Remote Access VPNs-20240318121359490.webp#invert]]

When a client negotiates an [[SSL]] connection with the VPN gateway, it actually connects using [[TLS]].

SSL uses the public key infrastructure and digital certificates to authenticate peers. Both [[IPSec]] and SSL VPN technologies offer access to virtually any network application or resource. However, when security is an issue, IPsec is the superior choice. If support and ease of deployment are the primary issues, consider SSL. The type of VPN method implemented is based on the access requirements of the users and the organisation’s IT processes. 

The table compares IPsec and SSL remote access deployments.

| Feature                   | IPsec                                                                             | SSL                                                                                                      |
| ------------------------- | --------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
|                           | IPsec works at Layer 3, the Network layer of the OSI model directly on top of IP. | SSL operates at Layer 7, the Application layer of the OSI model it encrypts HTTP traffic not IP packets. |
| **Connection complexity** | **Medium** - Because it requires a VPN client pre-installed on a host.            | **Low** - It only requires a web browser on a host.                                                      |
| **Connection option**     | **Limited** - Only specific devices with specific configurations can connect.     | **Extensive** - Any device with a web browser can connect.                                               |

It is important to understand that IPsec and SSL VPNs are ==not mutually exclusive==. Instead, they are complementary; both technologies solve different problems, and an organisation may implement IPsec, SSL, or both, depending on the needs of its telecommuters.

