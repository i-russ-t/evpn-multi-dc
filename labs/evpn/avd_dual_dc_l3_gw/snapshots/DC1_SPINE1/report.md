# DC1_SPINE1 Commands Output

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
Interface       IP Address            Status     Protocol        MTU    Owner  
--------------- --------------------- ---------- ------------ --------- -------
Management0     172.100.100.11/24     up         up             1500
```
## show lldp neighbors

```
Last table change time   : 0:00:15 ago
Number of table inserts  : 23
Number of table deletes  : 1
Number of table drops    : 0
Number of table age-outs : 1

Port          Neighbor Device ID       Neighbor Port ID    TTL
---------- ------------------------ ---------------------- ---
Et1           dc1-leaf1a               Ethernet1           120
Et2           dc1-leaf1b               Ethernet1           120
Et3           dc1-leaf2a               Ethernet1           120
Et4           dc1-leaf2b               Ethernet1           120
Et5           dc1-border-leaf1         Ethernet1           120
Et6           dc1-border-leaf2         Ethernet1           120
Ma0           dc1-spine2               Management0         120
Ma0           dc2-leaf2b               Management0         120
Ma0           dc2-leaf1b               Management0         120
Ma0           dc1-leaf2b               Management0         120
Ma0           dc2-spine2               Management0         120
Ma0           dc2-client4              0242.ac64.6486      120
Ma0           dc2-spine1               Management0         120
Ma0           dc1-client1              0242.ac64.646f      120
Ma0           dc1-client2              0242.ac64.6470      120
Ma0           dc2-client2              0242.ac64.6484      120
Ma0           dc2-client1              0242.ac64.6483      120
Ma0           dc1-client3              0242.ac64.6471      120
Ma0           dc1-client4              0242.ac64.6472      120
Ma0           dc2-client3              0242.ac64.6485      120
Ma0           dc1-leaf1a               Management0         120
Ma0           dc2-border-leaf1         Management0         120
```
## show running-config

```
! Command: show running-config
! device: dc1-spine1 (cEOSLab, EOS-4.32.2.1F-38881786.43221F (engineering build))
!
no aaa root
!
username admin privilege 15 role network-admin secret sha512 $6$ubcSV.NKW0xI5sVT$CKVn3OMS2Q7vxO6E2Y2tVv8IAicJ55XhbqJtUMjT3Js2HYGo95hD8eAtaHMWOm8uiHkOseCY/S/HBCTol9PQL/
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
hostname dc1-spine1
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
   ip address 172.100.100.11/24
   ipv6 address 2001:172:100:100::d/80
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
Serial number: 29CE30E5FE7731E1269643C97EC1E3EA
Hardware MAC address: 001c.735a.8285
System MAC address: 001c.735a.8285

Software image version: 4.32.2.1F-38881786.43221F (engineering build)
Architecture: i686
Internal build version: 4.32.2.1F-38881786.43221F
Internal build ID: 2652b984-57f4-4137-92f4-556d69f54d54
Image format version: 1.0
Image optimization: None

Kernel version: 5.15.0-125-generic

Uptime: 4 minutes
Total memory: 65425696 kB
Free memory: 48238068 kB
```
