# Troubleshooting

If you send a wrong command on CISCO OS, interface will be frozen because of domain lookup.
S4>eb
Translating "eb" ... domain name (255.255.255.255)
S4> en
S4# Conf t
S4# no ip domain-lookup

### 217 IP default gateway vs. default route

S2# sh ip route 
default gateway is not set
and if no ip routing func is enabled we don't have entries in ip route table

S2# conf t
S2(config)# ip default-gateway 10.1.1.254
now we have default-gateway

S2(config)# ip routing 
now we enable ip routing. From this point our swich don't use default-gateway

**if IP routing is enabled we have to set up default route**

S2(config)# ip route 0.0.0.0 0.0.0.0 10.1.1.254


### 219 static and default IP routes

most specific route wins
R1# ping 5.5.5.5
..... 
Success rate is 0%

---
#### debug from source
``` cisco OS
R1# debug ip packet
R1# ping 5.5.5.5 repeat 1

```
---

you can have multiple default routes? Yes you can.
```cisco OS
ip route 0.0.0.0 0.0.0.0 10.1.1.2
ip route 0.0.0.0 0.0.0.0 10.1.1.2
ip route 0.0.0.0 0.0.0.0 10.1.1.2
```
```cisco OS
R1(config)# do sh run | i route
```
allows to show running config from configuration terminal level


### how to change administrative distance
``` cisco OS
ip route 0.0.0.0 0.0.0.0 10.1.1.2 100
```
we added administrative distance 100.  We can add multiple default routes with different admin distance.
``` cisco OS
ip route 0.0.0.0 0.0.0.0 10.1.2.2 150
ip route 0.0.0.0 0.0.0.0 10.1.3.2 200
```
in this case:
``` cisco OS
sh ip route 
```
shows us just 1 static route - this one with a lowest admin distance
but
``` cisco OS
sh run | include ip route 
```
shows us all static routes
This is an way ti set up preffered routing way. and in case when interface go down, the second route will be preffered.

### DHCP
debug ip dhcp server

sh ip dhcp server stat

