# DC2_LEAF1A Commands Output

## Table of Contents

- [show lldp neighbors](#show-lldp-neighbors)
- [show ip interface brief](#show-ip-interface-brief)
- [show interfaces description](#show-interfaces-description)
- [show version](#show-version)
- [show running-config](#show-running-config)
## show interfaces description

```
Interface                      Status         Protocol           Description
Et1                            up             up                 
Et2                            up             up                 
Et3                            up             up                 
Et4                            up             up                 
Et5                            up             up                 
Et6                            up             up                 
Ma0                            up             up
```
## show ip interface brief

```
Address
Interface       IP Address             Status     Protocol        MTU   Owner  
--------------- ---------------------- ---------- ------------ -------- -------
Management0     172.100.100.121/24     up         up             1500
```
## show lldp neighbors

```
Last table change time   : 0:00:54 ago
Number of table inserts  : 24
Number of table deletes  : 2
Number of table drops    : 0
Number of table age-outs : 2

Port          Neighbor Device ID       Neighbor Port ID    TTL
---------- ------------------------ ---------------------- ---
Et1           dc2-spine1               Ethernet1           120
Et2           dc2-spine2               Ethernet1           120
Et3           dc2-leaf1b               Ethernet3           120
Et4           dc2-leaf1b               Ethernet4           120
Et5           dc2-client1              aac1.abd6.5fab      120
Et6           dc2-client2              aac1.ab2f.bf5d      120
Ma0           dc1-spine2               Management0         120
Ma0           dc2-client1              0242.ac64.6483      120
Ma0           dc1-spine1               Management0         120
Ma0           wan                      Management0         120
Ma0           dc2-border-leaf2         Management0         120
Ma0           dc2-spine1               Management0         120
Ma0           dc1-client2              0242.ac64.6470      120
Ma0           dc1-client1              0242.ac64.646f      120
Ma0           dc2-client2              0242.ac64.6484      120
Ma0           dc2-client3              0242.ac64.6485      120
Ma0           dc2-client4              0242.ac64.6486      120
Ma0           dc1-leaf1b               Management0         120
Ma0           dc2-leaf2a               Management0         120
Ma0           dc1-leaf1a               Management0         120
Ma0           dc1-client3              0242.ac64.6471      120
Ma0           dc1-leaf2a               Management0         120
```
## show running-config

```
! Command: show running-config
! device: dc2-leaf1a (cEOSLab, EOS-4.32.2.1F-38881786.43221F (engineering build))
!
no aaa root
!
username admin privilege 15 role network-admin secret sha512 $6$UboaA0KfkmH/7mNN$Pi.Y/rzORzJl/yoEw/eXCQGbOXTuKTMR8ooIGiDEW76aSaIhQiJwmYapknx690A9Vgjr8w8uPWaseRomnME7f.
!
management api http-commands
   protocol https ssl profile eAPI
   no shutdown
   !
   vrf MGMT
      no shutdown
!
no service interface inactive port-id allocation disabled
!
transceiver qsfp default-mode 4x10G
!
service routing protocols model multi-agent
!
hostname dc2-leaf1a
!
spanning-tree mode mstp
!
system l1
   unsupported speed action error
   unsupported error-correction action error
!
vrf instance MGMT
!
management security
   ssl profile eAPI
      cipher-list HIGH:!eNULL:!aNULL:!MD5:!ADH:!ANULL
      certificate eAPI.crt key eAPI.key
!
interface Ethernet1
!
interface Ethernet2
!
interface Ethernet3
!
interface Ethernet4
!
interface Ethernet5
!
interface Ethernet6
!
interface Management0
   description oob_management
   vrf MGMT
   ip address 172.100.100.121/24
   ipv6 address 2001:172:100:100::2/80
!
no ip routing
no ip routing vrf MGMT
!
ip route vrf MGMT 0.0.0.0/0 172.100.100.1
!
ipv6 route vrf MGMT ::/0 2001:172:100:100::1
!
router multicast
   ipv4
      software-forwarding kernel
   !
   ipv6
      software-forwarding kernel
!
end
```
## show version

```
Arista cEOSLab
Hardware version: 
Serial number: A1EAF8AF83140B82C0FABCEB11631E73
Hardware MAC address: 001c.73e5.d8a2
System MAC address: 001c.73e5.d8a2

Software image version: 4.32.2.1F-38881786.43221F (engineering build)
Architecture: i686
Internal build version: 4.32.2.1F-38881786.43221F
Internal build ID: 2652b984-57f4-4137-92f4-556d69f54d54
Image format version: 1.0
Image optimization: None

Kernel version: 5.15.0-125-generic

Uptime: 9 minutes
Total memory: 65425696 kB
Free memory: 48444156 kB
```
