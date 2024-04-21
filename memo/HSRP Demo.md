# HSRP Demo
What [[CISCO Commands]]use to accomplish this lab.

![[LAB_HSRP_CCNA.png]]

## Router0
``` Cisco
IntRouter# conf t
IntRouter(config)#int g 0/0/0
IntRouter(config)#int 
IntRouter(config-if)#ip address 10.1.1.253 255.255.255.0
IntRouter(config-if)#exit
IntRouter(config)#int g
IntRouter(config)#int gigabitEthernet 0/0/1
IntRouter(config-if)#ip add
IntRouter(config-if)#ip address dhcp
IntRouter(config)#sh ip int brief
Interface IP-Address OK? Method Status Protocol
GigabitEthernet0/0/0 10.1.1.253 YES manual up up
GigabitEthernet0/0/1 8.8.8.100 YES DHCP up up
Vlan1 unassigned YES unset administratively down down
```
# HSRP
Core1 and Core2 have: 
SVI (Swiched Virtual Intervace Configured)
VLAN SVI cofigured
## Core1
```cisco
Core1#sh ip int brief

Interface IP-Address OK? Method Status Protocol
Port-channel1 unassigned YES unset up up
GigabitEthernet1/0/1 unassigned YES unset up up
GigabitEthernet1/0/2 unassigned YES unset up up
GigabitEthernet1/0/3 unassigned YES unset up up
GigabitEthernet1/0/20 unassigned YES unset up up
GigabitEthernet1/0/21 unassigned YES unset administratively down down
GigabitEthernet1/0/22 unassigned YES unset administratively down down
GigabitEthernet1/0/23 unassigned YES unset up up
GigabitEthernet1/0/24 unassigned YES unset up up

Vlan1 10.1.1.251 YES manual up up
Vlan10 10.1.10.251 YES manual up up
Vlan20 10.1.20.251 YES manual up up
Vlan30 10.1.30.251 YES manual up up
Vlan100 10.1.100.251 YES manual up up

Core1# sh standby
<empty>
```
### configure HSRP for VLANS
``` cisco
Core1# conf t
Core1(config)# int vlan 10
Core1(config-if)# standby 1 ip 10.1.10.254
Core1(config-if)# standby 1 priority 200
Core1(config-if)# standby 1 preempt
```
we can see that this is an active HSRP router because there is no other in this conf.
We want this router become default we set priority 200. Default is 100. The higher the better
We want this router to become active even after malfunction, defect. That is preempt

## Core2
``` cisco
Core2# conf t
Core2(config)# int vlan 10
Core2(config-if)# standby 1 ip 10.1.10.254
```

repeat the same for vlans 20,30, 100, 1
but default router should be the Spanning tree root.
we have different roots for different vlans

```cisco
sh spanning-tree
conf t
spanning-tree vlan 10 prority
```
#### Outcome:
Core1#sh standby

*Vlan1 - Group 1
State is Active
5 state changes, last state change 21:28:26
Virtual IP address is 10.1.1.254
Active virtual MAC address is 0000.0C07.AC01
Local virtual MAC address is 0000.0C07.AC01 (v1 default)
Hello time 3 sec, hold time 10 sec
Next hello sent in 0.941 secs
Preemption enabled
Active router is local
Standby router is 10.1.1.252
Priority 200 (configured 200)
Group name is hsrp-Vl1-1 (default)
Vlan10 - Group 1
State is Active
5 state changes, last state change 12:49:23
Virtual IP address is 10.1.10.254
Active virtual MAC address is 0000.0C07.AC01
Local virtual MAC address is 0000.0C07.AC01 (v1 default)
Hello time 3 sec, hold time 10 sec
Next hello sent in 1.058 secs
Preemption enabled
Active router is local
Standby router is 10.1.10.252
Priority 200 (configured 200)
Group name is hsrp-Vl1-1 (default)
Vlan20 - Group 1
State is Standby
9 state changes, last state change 21:13:54
Virtual IP address is 10.1.20.254
Active virtual MAC address is 0000.0C07.AC01
Local virtual MAC address is 0000.0C07.AC01 (v1 default)
Hello time 3 sec, hold time 10 sec
Next hello sent in 1.598 secs
Preemption disabled
Active router is 10.1.20.252, priority 200 (expires in 8 sec)
MAC address is 0000.0C07.AC01
Standby router is local
Priority 100 (default 100)
Group name is hsrp-Vl2-1 (default)
Vlan30 - Group 1
State is Active
9 state changes, last state change 21:02:04
Virtual IP address is 10.1.30.254
Active virtual MAC address is 0000.0C07.AC01
Local virtual MAC address is 0000.0C07.AC01 (v1 default)
Hello time 3 sec, hold time 10 sec
Next hello sent in 1.195 secs
Preemption enabled
Active router is local
Standby router is 10.1.30.252
Priority 200 (configured 200)
Group name is hsrp-Vl3-1 (default)
Vlan100 - Group 1
State is Standby
3 state changes, last state change 21:26:50
Virtual IP address is 10.1.100.254
Active virtual MAC address is 0000.0C07.AC01
Local virtual MAC address is 0000.0C07.AC01 (v1 default)
Hello time 3 sec, hold time 10 sec
Next hello sent in 0.347 secs
Preemption disabled
Active router is 10.1.100.252
Standby router is local
Priority 100 (default 100)
Group name is hsrp-Vl1-1 (default)*

Now we still cant ping local switch SVI eg. 10.1.1.1
Because switch does not have default-gateway set
```cisco
Access1#sh ip route

Default gateway is not set
Host Gateway Last Use Total Uses Interface
ICMP redirect cache is empty
Access1#sh protocols

Global values:

Internet Protocol routing is enabled

GigabitEthernet1/0/1 is up, line protocol is up

 

Access1#conf t

Enter configuration commands, one per line. End with CNTL/Z.

Access1(config)#ip default-gateway ?

A.B.C.D IP address of default gateway

Access1(config)#ip default-gateway 10.1.1.254

Access1(config)#exit
```
usefull command: [[Troubleshooting]]
```cisco
un all
debug ip icmp
no debug ip icmp
no ip domain-lookup

```
#### EIGRP
last thing is to configure eigrp on the Router0, Core1 and Core 2

Router 0
``` cisco
conf t
router eigrp 100
network 10.0.0.0
no autosummary
network 1.0.0.0
```

Core1 and Core 1
``` cisco
conf t
router eigrp 100
network 10.0.0.0
no auto
```

