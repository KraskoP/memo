# VLAN Demo
### Demo definition
![[VLAN_basic_lab.png]]


- Configure the network as follows:

3650 = layer 3 switch with IP addresses and interVLAN routing:
VLAN 1 = 10.1.1.254/24
VLAN 10 = 10.1.10.254/24,
VLAN 20 = 10.1.20.254/24
VLAN 30 = 10.1.30.254/24,
VLAN 100 = 10.1.100.254/24

- Access layer switches will only have management IP addresses in VLAN 1:
Switch 1 = 10.1.1.1/24
Switch 2 = 10.1.1.2/24
Switch 3 = 10.1.1.3/24

- Configure access ports as follows:
PC1 in VLAN 10 - 10.1.10.10/24
PC2 in VLAN 20 - 10.1.20.20/24
PC3 in VLAN 30 - 10.1.30.30/24
Server1 in VLAN 100 - 10.1.100.100/24

- Configure ports between switches as trunks
- Make sure that PCs can ping each other and the server
- Make sure that switches can ping the PCs and server
## Commands
### 3650 Main-switch
en
conf t 
hostname main-switch
Switch(config)# vlan 100
Switch(config-vlan)# name server

now I have to add int g0/1/20 into VLAN100
#### Configure VLAN access port
main-switch(config)int g0/1/20
main-switch(config-if)switchport access vlan 100
end


main-switch(config-if)#no ip add
main-switch(config-if)#exit

Switch(config)#int vlan 100


#### Routing
sh spanning-tree 
sh spanning-tree summary

---

On most switches IP routing is enabled by default
(config)# ip routing  - enable ip routing
(config)# no ip routing  - diasable ip routing

---
Show interface configuration
sh run 
to chceck in bulk if there are some confiugrations on the interfaces

sh int g0/0/0 switchport 
encapsulatuon dot1q



#### Configure VLAN trunk port
main-switch(config)int g0/2
main-switch(config-if)switchport mode trunk
if fails we have to do encapsulation


#### Configure SVI (Switch Virtual Interfaces)
Those SVI are for inter VLAN routing purposes
main-switch(config)int vlan 20
main-switch(config-if)ip add 10.1.20.254 255.255.255.0
main-switch(config-if) no shut


#### Show port configuration
main-switch#sh int gigabitEthernet 1/0/1 sw
main-switch#sh int gigabitEthernet 1/0/1 switchport