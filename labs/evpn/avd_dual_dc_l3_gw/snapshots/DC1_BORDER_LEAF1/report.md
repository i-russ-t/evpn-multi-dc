# DC1_BORDER_LEAF1 Commands Output

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
Ma0                            up             up
```
## show ip interface brief

```
Address
Interface       IP Address            Status     Protocol        MTU    Owner  
--------------- --------------------- ---------- ------------ --------- -------
Management0     172.100.100.13/24     up         up             1500
```
## show lldp neighbors

```
Last table change time   : 0:01:40 ago
Number of table inserts  : 21
Number of table deletes  : 0
Number of table drops    : 0
Number of table age-outs : 0

Port          Neighbor Device ID       Neighbor Port ID    TTL
---------- ------------------------ ---------------------- ---
Et1           dc1-spine1               Ethernet5           120
Et2           dc1-spine2               Ethernet5           120
Et3           dc1-border-leaf2         Ethernet3           120
Et4           dc1-border-leaf2         Ethernet4           120
Et5           wan                      Ethernet1           120
Ma0           dc2-client1              0242.ac64.6483      120
Ma0           dc2-client4              0242.ac64.6486      120
Ma0           dc1-client3              0242.ac64.6471      120
Ma0           dc2-client3              0242.ac64.6485      120
Ma0           dc1-client4              0242.ac64.6472      120
Ma0           dc1-client2              0242.ac64.6470      120
Ma0           dc1-client1              0242.ac64.646f      120
Ma0           dc2-client2              0242.ac64.6484      120
Ma0           dc2-border-leaf1         Management0         120
Ma0           dc2-leaf2a               Management0         120
Ma0           001c.7399.c093           Management0         120
Ma0           dc2-leaf1a               Management0         120
Ma0           dc2-border-leaf2         Management0         120
Ma0           dc1-leaf2a               Management0         120
Ma0           dc1-border-leaf2         Management0         120
Ma0           wan                      Management0         120
```
## show running-config

```
! Command: show running-config
! device: dc1-border-leaf1 (cEOSLab, EOS-4.32.2.1F-38881786.43221F (engineering build))
!
no aaa root
!
username admin privilege 15 role network-admin secret sha512 $6$zgJ50MZRX44o2WmW$xJDo008ZjOyzvD/vtCeHCj3pG.NeHWQI5G.US.Xb3XlvL/J9xh7NN9.ZwpV/reOI1LoroF9uV64qp/63rsiZk1
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
hostname dc1-border-leaf1
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
interface Management0
   description oob_management
   vrf MGMT
   ip address 172.100.100.13/24
   ipv6 address 2001:172:100:100::12/80
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
Serial number: 171872B91A9CEBB6111D00F34184355C
Hardware MAC address: 001c.7394.3f3e
System MAC address: 001c.7394.3f3e

Software image version: 4.32.2.1F-38881786.43221F (engineering build)
Architecture: i686
Internal build version: 4.32.2.1F-38881786.43221F
Internal build ID: 2652b984-57f4-4137-92f4-556d69f54d54
Image format version: 1.0
Image optimization: None

Kernel version: 5.15.0-125-generic

Uptime: 3 minutes
Total memory: 65425696 kB
Free memory: 48250836 kB
```
