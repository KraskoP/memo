# Routing
## Routed Protocols
- IPv4
- IPv6
- Carry user information
- each router making independent decision in determining path
- routers are making decisions based on destination IP address
## Routing protocols
- examples EIGRP, OSPF, RIP, ISIS, BGP
- communicate information about networks
- determine the best route between networks
- if router does not now where to send packet (uniast) it drops packet

Distance Vector Routing protocols: RIP, 
LinkState - topology database. Exactly knows, has full view of the 
Advanced Distance Vector: EIGRP

AS - Autonomous System
IGP - Interior Gateway Protocol
EGP - Exterior Gateway Protocol

IGP are used inside AS: RIP, OSPF, EIGRP
EGP are used between AS: BGP 



## Cisco Commands
Cisco Commands [[CISCO Commands]]
S1# sh run | include ip route

R1(config)# ip route 10.1.2.0 255.255.255.0. 10.1.1.2
static route to **network** 10.1.2.0/24 is available through interface 10.1.1.2




R1(config)# ip route 0.0.0.0 0.0.0.0 192.168.1.254
default gateway

R1(config)# no ip route 1.1.1.1 255.255.255.0 10.1.2.1
remove route

R1(config)# do sh run | include ip route


R3# debug ip packet
useful command but stay carefull, to not kill your Router
R3# un all - undebug all
R3# debug ip icmp - debug only icmp

R1# sh ip route
shows ip route table

R2# show ip cef
shows what ip dest address is available on which interface

when we send ping we can tell from which interface.
R1# ping 10.1.2.2 means that we send ping from one interface.
R1# ping 10.1.2.2 source loop 0 sends ping from loopback 0

R1# sh run int loop 0
shows what are param of int 0

## Routing protocols types

``` cisco
sh run
sh run | include rip
sh run | section rip
sh run | begin rip
```
to check what routing protocol is used on the router:
``` cisco
sh ip protocols
```
to dig dipper
``` cisco
sh ip rip datbase
```

## Administrative distance
Administrative Distance, or AD is a feature that routers use to determine which is the best path to install in the routing table when routing information to a particular destination is made available from multiple routing protocols.

The default ADs used by Cisco IOS routing devices are as follows:

| Route Source        | Default AD |
| ------------------- | ---------- |
| Connected Interface | 0          |
| Static Route        | 1          |
| External BGP        | 20         |
| EIGRP               | 90         |
| OSPF                | 110        |
| IS-IS               | 115        |
| RIP                 | 120        |


- 0 Connected interface
- 1 [Static route](https://notes.networklessons.com/ip-routing-table-static-route)
- 5 Enhanced Interior Gateway Routing Protocol ([EIGRP](https://notes.networklessons.com/eigrp)) summary route
- 20 External Border Gateway Protocol ([BGP](https://notes.networklessons.com/bgp))
- 90 Internal EIGRP
- 100 IGRP
- 110 Open Shortest Path First ([OSPF](https://notes.networklessons.com/ospf))
- 115 Intermediate System-to-Intermediate System ([IS-IS](https://notes.networklessons.com/is-is))
- 120 Routing Information Protocol ([RIP](https://notes.networklessons.com/rip))
- 140 Exterior Gateway Protocol (EGP)
- 160 On Demand Routing (ODR)
- 170 External EIGRP
- 200 Internal BGP
- 255 Unknown

If the AD is 255, this means that the router does not consider the source of that route to be reliable, and does not install it in the routing table.

Links:

[https://networklessons.com/cisco/ccna-routing-switching-icnd1-100-105/introduction-to-administrative-distance](https://networklessons.com/cisco/ccna-routing-switching-icnd1-100-105/introduction-to-administrative-distance)

[https://www.cisco.com/c/en/us/support/docs/ip/border-gateway-protocol-bgp/15986-admin-distance.html](https://www.cisco.com/c/en/us/support/docs/ip/border-gateway-protocol-bgp/15986-admin-distance.html)

## RIP Configuration

```cisco
R1(config)#router rip
R1(config-router)#version 2
R1(config-router)#network 10.0.0.0
```
no subnet is  specified. Network - classful network
RIP automatically does auto summary, and this is almost always undesirable.

Sometimes is ok to summarize networks:
``` cisco
R1(config-router)#interface F0/1
R1(config-if)#ip summary-address rip 10.0.0.0 255.255.0.0.
```
This configuration is on the interface we are going to advertise (not summarize)

### Default route injection
When we have e.g internet connection: 203.0.113.2 we want to advertise this default route to all routers using RIP
```cisco
R4(config)# ip route 0.0.0.0. 0.0.0.0 203.0.113.2
R1(config)#router rip
R1(config)#default-information originate
```
### Don't share network information with external organization
```cisco
R4(config-router)#router rip
R4(config-router)#passive-interface fast3/0
R4(config-router)#network 203.0.113.0
R4(config-router)#end
```
# EIGRP
```cisco
R1(config)#router eigrp 100
R1(config-router)#network 10.0.0.0
```




how to monitor:
show ip eigrp inter
show ip eigrp neighbors
show ip route