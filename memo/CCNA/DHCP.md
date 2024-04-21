# DHCP
```cisco OS
R1# sh ip dhcp bin
R1# sh ip dhcp pool WORD

```
#### how to configure DHCP server?
```cisco OS
ip dhcp pool PC
network 10.1.1.0 255.255.255.0
default-router 10.1.1.254
dns-server 10.1.1.254
lease 1
domain-name krasko.com
ip dhcp excluded-address 10.1.1.254
end
sh ip dhcp pool 
```

#### how to configure client?
``` cisco
conf t
ing f 0/0
ip addr dhcp
no shut
```
on the server site we can see all the leases
``` cisco
show ip dhcp binding

```
in the output Client ID/hw Address or user name can be not ease readable. In this case we can change that:
``` cisco
ip dhcp client-id ascii PC2
```

### VLAN and DHCP
in VLAN env, when we have DHCP serwer located outside the VLAN, we have to point at this serwer.

``` cisco
en
conf t
int vlan 10
ip helper-address 10.1.1.254
exit
```
what is [helper address:](https://notes.networklessons.com/dhcp-relay-agent)

