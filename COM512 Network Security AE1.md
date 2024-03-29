---
tags:
  - Studies
  - COM512
  - CyberSecurity
  - Assessment
---
## Soton Router

#### Passwords

- Privileged Exec = cisco
- User chodges = oywb3vz%J(
- User jbloggs = fh32novr83
- Permission level 5 = wbl8wlnyto8n
- View root = cisco
- View VIEW-ONLY = nvyp389vcd
- View TROUBLESHOOT-ONLY = vn289yr3
#### Tasks
###### Task 1

1. Privileged Exec Mode Password: `vy8nh32q9%!` 
   
   Local Account Creation & Setting this as the login method for console connections: `oywb3vz%J(`
   
1. Setting minimum password length (4 for the assessment. Should be 10+ in reality): 

2. Block access if repeated login attempts made with invalid passwords:
   
   Blocks access for 10 mins if 10 wrong attempts made within 5 minutes.

4. Set up SSH access:

```
Soton(config)# enable secret vy8nh32q9%!  
  
Soton(config)# username chodges privilege 15 password oywb3vz%J(  
Soton(config)# line console 0  
Soton(config-line)# login local  
Soton(config-line)# exit  
  
Soton(config)# security passwords min-length 4  
Soton(config)# login block-for 600 attempts 10 within 300  
  
Soton(config)# ip domain-name acme.com  
Soton(config)# crypto key generate rsa general-keys modulus 2048  
  
---- (Output Omitted) ----  
  
Soton(config)# line vty 0 15  
Soton(config-line)# transport input ssh  
Soton(config-line)# ip ssh version 2  
Soton(config)# line vty 0 15  
Soton(config-line)# login local
```
###### Task 2

```bash
# Restricting the reload command to permission level 5.

privilege exec level 5 reload

# Password protecting direct access to level 5 permissions.

enable secret level 5 wbl8wlnyto8n

# Creating a user with level 5 permissions.

username jbloggs privilege 5 password fh32novr83

# Password protecting level 15 with the password 'cisco'.

enable secret level 15 cisco

# Creating a user view that only has access to show the configuration of network devices.
aaa new-model
enable view # Password = cisco
parser view VIEW-ONLY
secret nvyp389vcd
commands exec include show

# Creating a user view that can only ping and show the ip interface addresses.
enable view # Password = cisco
parser view TROUBLESHOOT-ONLY
secret vn289yr3
commands exec include ping
commands exec include show ip interface brief

# Creating an admin view with full access.
enable view # Password = cisco
parser view ADMIN
secret owhn4tfa
commands exec include all view full

# Creating a superview that includes the previous three views.
enable view # Password = cisco
parser view VIEW-TROUB-ADMIN superview
view VIEW-ONLY
view TROUBLESHOOT-ONLY
view ADMIN
secret lynaw89cxm
exit
```

###### Task 3

Information from Netacad Network Security 6.5.8

```powershell
# Setting the Syslog Server address
logging 192.168.20.4

# Setting which messages to send to Syslog Server
logging trap debugging # Packet tracer only supports debugging

# Optional set the IPv4 or IPv6 address of the packet as originating from a specific interface (logging source-interface lo0). No need as I want it to be interface G0/1

# Enable logging
logging on

# Exit
exit
```

Information from Netacad Network Security 6.6.3

```powershell
# Set the NTP source server
ntp server 192.168.20.4

# Exit
exit

# Optional - test config:
show ntp associations
```

###### Task 4

```
# Enable AAA
aaa new-model

# Tell the router about the RADIUS server
radius server LOCALRAD
# acct-port (below) doesn't work in packet tracer
address ipv4 192.168.20.2 auth-port 1645 acct-port 1646
key secret01
exit

# Set the login authentication method (fall back to local if unreachable)
aaa authentication login default group radius local

# Create a local aaa user for if RADIUS is unreachable
username chodges privilege 15 secret qwo038q39hn(!

# Allow access to exec commands via RADIUS
aaa authorization exec default group radius

# Set accounting via RADIUS for exec commands
aaa accounting exec default start-stop group radius
```
###### Task 5

```
# Configure the 1st ACL
ip access-list extended SOU-SERVER-PROTECT

# Permit traffic from Newbury & Southampton users to the Intranet Server
permit ip 192.168.5.0 0.0.0.255 host 184.15.10.5
permit ip 194.34.5.0 0.0.0.255 host 184.15.10.5
permit ip 192.168.10.0 0.0.0.255 host 184.15.10.5
permit ip 192.168.20.0 0.0.0.255 host 184.15.10.5

# Permit any traffic Web Servers via ports: 53, 80, & 443 & ICMP.
permit udp any host 184.15.10.2 eq 53
permit tcp any host 184.15.10.2 eq 80
permit tcp any host 184.15.10.2 eq 443
permit icmp any host 184.15.10.2

# Permit any traffic Web Servers via ports: 53, 80, & 443 & ICMP.
permit udp any host 184.15.10.3 eq 53
permit tcp any host 184.15.10.3 eq 80
permit tcp any host 184.15.10.3 eq 443
permit icmp any host 184.15.10.3
deny ip any any
exit

# Apply the ACL on Soton Router
interface G0/0
ip access-group SOU-SERVER-PROTECT out
exit

# Configure the 2nd ACL
ip access-list extended PERMIT-NEWBURY
permit ip 192.168.5.0 0.0.0.255 any
permit ip 194.34.5.0 0.0.0.255 any
permit ip 184.15.10.0 0.0.0.255 any
deny ip any any
exit

# Apply the 2nd ACL
interface G0/1.10
ip access-group PERMIT-NEWBURY out
exit

interface G0/1.20
ip access-group PERMIT-NEWBURY out
exit

# Task Complete
```
###### Task 6

```
# Internal Zone 1
zone security Soton1

# External Zone 1
zone security Soton_Ext
```

###### Task 7

```
```
```
# Configure SPAN from port facing Soton Router to Sniffer Port.
monitor session 10 source interface G0/2
monitor session 10 destination interface F0/2

# Then simply adjust the sniffer to only monitor DNS, and ICMP.
```

Ping from Soton's PC0 to Newbury's PC5 Cisco Admin
![[COM512 Network Security AE1-20240328154204646.webp]]

NSLookup from PC4 Cisco Admin to DNS Server in DMZ
![[COM512 Network Security AE1-20240328154546668.webp]]

Web Page Access from PC3 to Web server in DMZ:
![[COM512 Network Security AE1-20240328154939126.webp]]
###### Task 8

```
# Protect Soton Switches Against VLAN Attacks

# Switch 0
int range f0/3-4
switchport mode access
switchport access vlan 10
int range f0/5, f0/10
switchport mode access
switchport access vlan 20
int range f0/6-9, f0/11-24, g0/1-2
switchport mode access
switchport access vlan 1000
int range F0/1-2
switchport mode trunk
switchport nonegotiate
switchport trunk native vlan 50
switchport trunk allowed vlan 10,50,20

# Switch 1
int range f0/2-3
switchport mode access
switchport access vlan 20
int range f0/4, f0/10
switchport mode access
switchport access vlan 10
int range f0/5-9, f0/11-24, g0/2
switchport mode access
switchport access vlan 1000
int range f0/1, g0/1
switchport mode trunk
switchport nonegotiate
switchport trunk native vlan 50
switchport trunk allowed vlan 10,50,20

# Switch 2
int f0/2
switchport mode access
int range f0/3-24
switchport mode access
switchport access vlan 1000
int range f0/1, g0/1-2
switchport mode trunk
switchport nonegotiate
switchport trunk native vlan 50
switchport trunk allowed vlan 10,50,20

# Protect Soton from STP Attacks
# Switch 0
int range F0/3-5, F0/10
spanning-tree portfast
spanning-tree bpduguard enable
exit
spanning-tree loopguard default # Not in Packet Tracer

# Switch 1
int range F0/2-4, F0/10
spanning-tree portfast
spanning-tree bpduguard enable
exit
spanning-tree loopguard default # Not in Packet Tracer
int f0/1
spanning-tree guard root

# Switch 2
int F0/2
spanning-tree portfast
spanning-tree bpduguard enable
spanning-tree loopguard default # Not in Packet Tracer
int range f0/1, g0/1
spanning-tree guard root
exit

# Unused Ports must be shut down
# Switch 0
int range F0/6-9, F0/11-24, G0/1-2
shutdown

# Switch 1
int range F0/5-9, F0/11-24, G0/2
shutdown

# Switch 2
int range F0/3-24
shutdown

# Change of native VLAN (already covered).

# Make sure to adjust native vlan on soton router.
```

###### Task 9

```
# Install the module
license boot module c1900 technology-package securityk9
exit
copy running-config startup-config
reload

# Create the ACL
ip access-list extended VPN_TO_NEWB
# Soton VLAN 10 to Newbury Zone 1
permit ip 192.168.10.0 0.0.0.255 192.168.5.0 0.0.0.255
# Soton VLAN 20 to Newbury Zone 1
permit ip 192.168.20.0 0.0.0.255 192.168.5.0 0.0.0.255
# Soton VLAN 10 to Newbury Zone 2
permit ip 192.168.10.0 0.0.0.255 194.34.5.0 0.0.0.255
# Soton VLAN 20 to Newbury Zone 2
permit ip 192.168.20.0 0.0.0.255 194.34.5.0 0.0.0.255
deny ip any any
exit

# Create the ISAKMP policy
crypto isakmp policy 10
encryption aes 256
authentication pre-share
group 5 # Only 5 supported in packet tracer.
exit

# Set PSK options and create transform-set
crypto isakmp key sha address 20.0.0.1
crypto ipsec transform-set SECURE_TRANSFORM esp-aes esp-sha-hmac

# Create a crypto map
crypto map SECURE_SOTON_NEWB 10 ipsec-isakmp
description Links to Newbury Router. IPSec and ISAKMP in use.
set peer 20.0.0.1
set transform-set SECURE_TRANSFORM
match address VPN_TO_NEWB

# Apply the IPSec VPN
int s0/0/0
crypto map SECURE_SOTON_NEWB
exit
```

## Newbury Router

#### Passwords

#### Tasks

###### Task 1

1. Setting Privileged Exec Password: `wqnt0vr!$e`
   
   Local Account Creation & Setting this as the login method for console connections: `qwo038q39hn(!`

2. Setting minimum password length (4 for the assessment. Should be 10+ in reality): 

3. Block access if repeated login attempts made with invalid passwords:
   
   Blocks access for 10 mins if 10 wrong attempts made within 5 minutes.

4. Set up SSH access:

###### Task 2

```bash
# Restricting the reload command to permission level 5.

privilege exec level 5 reload

# Password protecting direct access to level 5 permissions.

enable secret level 5 wbl8wlnyto8n

# Creating a user with level 5 permissions.

username jbloggs privilege 5 password fh32novr83

# Password protecting level 15 with the password 'cisco'.

enable secret level 15 cisco

# Creating a user view that only has access to show the configuration of network devices.

# conf mode
aaa new-model

# privileged exec mode
enable view # Password = cisco

# conf mode
parser view VIEW-ONLY
secret nvyp389vcd
commands exec include show

# Creating a user view that can only ping and show the ip interface addresses.

# conf mode
aaa new-model 

# privileged exec mode
enable view # Password = cisco
# No need to do this after the first time

# conf mode
parser view TROUBLESHOOT-ONLY
secret vn289yr3
commands exec include ping
commands exec include show ip interface brief

# Creating an admin view with full access.

# conf mode
aaa new-model 

# privileged exec mode
enable view # Password = cisco 
# No need to do this after the first time

# conf mode
parser view ADMIN
secret owhn4tfa
commands exec include all view full

# Creating a superview that includes the previous three views.

# conf mode
aaa new-model

# privileged exec mode
enable view # Password = cisco

# conf mode
parser view VIEW-TROUB-ADMIN superview
view VIEW-ONLY
view TROUBLESHOOT-ONLY
view ADMIN
secret lynaw89cxm
exit
```

###### Task 3

Information from Netacad Network Security 6.5.8

```powershell
# Setting the Syslog Server address
logging 192.168.5.2

# Setting which messages to send to Syslog Server
logging trap debugging # Packet tracer only supports debugging

# Optional set the IPv4 or IPv6 address of the packet as originating from a specific interface (logging source-interface lo0). No need as I want it to be interface G0/0

# Enable logging
logging on

# Exit
exit
```

Information from Netacad Network Security 6.6.3

```powershell
# Set the NTP source server
ntp server 192.168.5.2

# Exit
exit

# Optional - test config:
show ntp associations
```

Information from Netacad Network Security 6.7.8

```powershell
# Create an ACL to permit/deny
ip access-list standard NET-MANAGER

# permit the allowed network
permit 192.168.20.0 255.255.255.0

# Exit
exit

# LOOK INTO THIS BIT:
R1(config)# snmp-server view SNMP-RO iso included
R1(config)# snmp-server group ADMIN v3 priv read SNMP-RO access PERMIT-ADMIN
R1(config)# snmp-server user BOB ADMIN v3 auth sha cisco12345 priv aes 128 cisco54321  
R1(config)# end
```

###### Task 4

```
# Enable AAA
aaa new-model

# Tell the router about the RADIUS server
radius server LOCALRAD
# acct-port (below) doesn't work in packet tracer
address ipv4 192.168.5.2 auth-port 1645 acct-port 1646
key secret01
exit

# Set the login authentication method (fall back to local if unreachable)
aaa authentication login default group radius local

# Create a local aaa user for if RADIUS is unreachable
username chodges privilege 15 secret qwo038q39hn(!

# Allow access to exec commands if RADIUS authenticated
aaa authorization exec default group radius

# Set accounting via RADIUS for exec commands
aaa accounting exec default start-stop group radius
```
###### Task 6

```
# Create internal and external zone(s)
zone security Newbury1
zone security Newbury2
zone security Newbury_Ext

# Assign interfaces to zones
interface G0/0
  zone-member security Newbury1
interface G0/1
  zone-member security Newbury2
interface S0/0/1
  zone-member security Newbury_Ext

# Define class-maps to identify traffic
class-map type inspect match-any Outside-to-Newbury1
  match any
class-map type inspect match-any Outside-to-Newbury2
  match any
class-map type inspect match-any Newbury1-to-outside
  match any
class-map type inspect match-any Newbury2-to-outside
  match any
class-map type inspect match-any Newbury1-to-Newbury2
  match any
class-map type inspect match-any Newbury2-to-Newbury1
  match any

# Define policy maps for each zone pair
policy-map type inspect Outside-to-Newbury1-policy
  class type inspect Outside-to-Newbury1
    inspect
policy-map type inspect Outside-to-Newbury2-policy
  class type inspect Outside-to-Newbury2
    inspect
policy-map type inspect Newbury1-to-outside-policy
  class type inspect Newbury1-to-outside
    inspect
policy-map type inspect Newbury2-to-outside-policy
  class type inspect Newbury2-to-outside
    inspect
policy-map type inspect Newbury1-to-Newbury2-policy
  class type inspect Newbury1-to-Newbury2
    inspect
policy-map type inspect Newbury2-to-Newbury1-policy
  class type inspect Newbury2-to-Newbury1
    inspect

# Create zone pairs and apply policy-maps
zone-pair security Outside-to-Newbury1 source Newbury_Ext destination Newbury1
  service-policy type inspect Outside-to-Newbury1-policy
zone-pair security Outside-to-Newbury2 source Newbury_Ext destination Newbury2
  service-policy type inspect Outside-to-Newbury2-policy
zone-pair security Newbury1-to-outside source Newbury1 destination Newbury_Ext
  service-policy type inspect Newbury1-to-outside-policy
zone-pair security Newbury2-to-outside source Newbury2 destination Newbury_Ext
  service-policy type inspect Newbury2-to-outside-policy
zone-pair security Newbury1-to-Newbury2 source Newbury1 destination Newbury2
  service-policy type inspect Newbury1-to-Newbury2-policy
zone-pair security Newbury2-to-Newbury1 source Newbury2 destination Newbury1
  service-policy type inspect Newbury2-to-Newbury1-policy

```

###### Task 8

```
# Switch 5 - DHCP Attacks
ip dhcp snooping
int range f0/1-2
ip dhcp snooping trust
exit
int range F0/3-24, G0/1-2
ip dhcp snooping limit rate 6
exit
ip dhcp snooping vlan 1

# Switch 5 - ARP Attacks
int range f0/1-2
ip arp inspection trust
exit
ip arp inspection vlan 1
ip arp inspection validate ip src-mac dst-mac

# Switch 5 - MAC Table Attacks
int range F0/2-4
switchport mode access
switchport port-security
switchport port-security aging time 120
switchport port-security aging type inactivity
switchport port-security maximum 2
switchport port-security mac-address sticky
exit
int f0/1
switchport mode trunk # best practice
exit

# Switch 4 and 5 - Protection against rogue switches
int f0/1
switchport mode trunk
int range f0/2-24, G0/1-2
switchport mode access
exit

# Switch 4 - Shutdown unused ports
int range F0/4-24, G0/1-2
shutdown
exit

# Switch 5 - Shutdown unused ports
int range F0/5-24, G0/1-2
shutdown
exit
```

###### Task 9

```
# Install the module
license boot module c1900 technology-package securityk9
exit
copy running-config startup-config
reload

# Create the ACL
ip access-list extended VPN_TO_SOTON
# Newbury Zone 1 to Soton VLAN 10
permit ip 192.168.5.0 0.0.0.255 192.168.10.0 0.0.0.255
# Newbury Zone 1 to Soton VLAN 20
permit ip 192.168.5.0 0.0.0.255 192.168.20.0 0.0.0.255
# Newbury Zone 2 to Soton VLAN 10
permit ip 194.34.5.0 0.0.0.255 192.168.10.0 0.0.0.255
# Newbury Zone 2 to Soton VLAN 20
permit ip 194.34.5.0 0.0.0.255 192.168.20.0 0.0.0.255
deny ip any any
exit

# Create the ISAKMP policy
crypto isakmp policy 10
encryption aes 256
authentication pre-share
group 5 # Only 5 supported in packet tracer.
exit

# Set PSK options
crypto isakmp key sha address 16.0.0.2

# Create the transform set named SECURE_TRANSFORM
crypto ipsec transform-set SECURE_TRANSFORM esp-aes esp-sha-hmac

# Create a crypto map
crypto map SECURE_SOTON_NEWB 10 ipsec-isakmp
description Links to Soton Router. IPSec and ISAKMP in use.
set peer 16.0.0.2
set transform-set SECURE_TRANSFORM
match address VPN_TO_SOTON

# Apply the IPSec VPN
int s0/0/1
crypto map SECURE_SOTON_NEWB
exit
```