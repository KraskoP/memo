
# Introduction to Cisco Commands
## Command Modes

Commands from: [https://www.netwrix.com/cisco_commands_cheat_sheet.html](https://www.netwrix.com/cisco_commands_cheat_sheet.html)


- **User exec mode** — This mode is the mode you land in when you first log onto a Cisco device. It provides limited access to commands and configuration settings. For instance, this mode enables you to view status using certain show commands but does not enable you to view or edit configurations.
- **Privileged exec mode** — This mode provides access to all commands, enabling more detailed examination and control of the device's operation and configuration.
- **Global Configuration mode**: Global configuration commands apply to features that affect the device as a whole. While Exec and Privileged Exec are read-only modes, Global Configuration mode gives the user writable access to modify the active configuration file. To use Global Configuration mode, you first need to enter Privileged EXEC Mode and then execute the configure terminal command although numerous shortcuts are accepted such as config t. Global Configuration mode can be further divided into the following command modes, which permit you to configure different components:

|                                     |                                                                                                                                      |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| Mode Control Commands               |                                                                                                                                      |
| **Command**                         | **Description**                                                                                                                      |
| **enable**                          | Moves a user from user exec mode into Privileged EXEC mode. Privileged exec mode is indicated by the # symbol in the command prompt. |
| **configure terminal**              | Logs the user into Global Configuration mode                                                                                         |
| **interface** _fastethernet/number_ | Enters interface configuration mode for the specified fast ethernet interface                                                        |
## Example 
This example is from CCNA Course:
1. show ip int brief
2. en - enable privileged mode
3. configure t - Global Configuration
4. int g0/0/0 - interface 0/0/0
5. ip? - show commands related to IP
6. ip address ?
7. ip address 10.1.1.1 ?
8. ip address 10.1.1.1 255.255.255.0
9. no shut - to bring interface up
10. exit - leave global
11. hostname R1 - change name of Router for R1
12. end
13. Copy running-config startup-config
---
14. sh run - show run 
15. ping 8.8.8.8
16. ping - can be interactive ping 
17. R4\# sh cdp neighbourhs
18. R4\# sh cdp neighbourhs details
19. R4 (config) ip domain-lookup
20. R4 (config) ip name-server 8.8.8.8
21. sh ip int g 0/0/0
22. sh run int g 0/0/
--- 
23. debug ip packet
24. un all (undebug all)
25. debug ip icmp
26. ping 1.1.1.20 repeat 1
---
28. sh run int f0/3 - show running config interface configuration
29. sh int f3/0
30. clear counters - clear "show interface" counters
31. sh int f1/0/5 |include dupl - this is similar to grep, filters output
---
33. sh version - show version of Cisco OS
34. sh run | i dns
35. sh run - show running services
36. sh mac address-table 
---
38. sh ip route - show configured routes
39. no ip routing
40. shut int  range fa0/1 - 24
41. (config) int vlan 1
42. (config) no ip add - remove vlan address from vlan 1
---
44. 
---




 
### Basic Configuration Command List

|   |   |
|---|---|
|**reload**|Reboots the Cisco switch or router|
|**hostname** _name_|Sets a host name to the current Cisco network device|
|**copy** _from-location to-location_|Copies files from one file location to another|
|**copy running-config startup-config**|Replaces the startup config with the active config when  the Cisco network device initializes|
|**copy startup-config running-config**|Merges the startup config with the currently active config in RAM|
|**write erase**   <br>**erase startup-config**|Deletes the startup config|
|**ip address** _ip-address mask_|Assigns the specified IP address and subnet mask|
|**shutdown**  <br>**no shutdown**|Shuts the interface down (shutdown) or brings it up (no shutdown)|
|**ip default-gateway** _ip_address_|Sets the default gateway on the Cisco device|
|**show running-config**|Displays the current configuration of the device|
|**show startup-config**|Displays the saved configuration stored in the device's NVRAM, which will be loaded when the device starts up|
|**description** _string_|Assigns the specified description to an interface|
|**show running-config interface** _interface slot/number_|Displays the running configuration for the specified interface|
|**show ip interface** _[type number]_|Displays the status of a network interface as well as a detailed listing of its IP configurations and related characteristics.|
|**ip name-server** _serverip-1 serverip-2_|Sets the IP address of or more DNS servers that the device can use to resolve hostnames to IP addresses.|

### Troubleshooting Cisco Commands List
|   |   |
|---|---|
|**ping** _{hostname \| system-address} [source source-address]_|Used to diagnose basic network connectivity|
|**speed** _{10 \| 100 \| 1000 \| auto}_|Either configures the transmission speed of a network interface to the specified value in megabits per second (Mbps), or enables automatic speed detection for the port|
|**duplex** _{auto \| full \| half}_|Sets duplex to half, full or auto|
|**cdp run**  <br>**no cdp run**|Enables or disables Cisco Discovery Protocol (CDP) for the device|
|**show mac address-table**|Displays the MAC address table|
|**show cdp**|Shows whether CDP is enabled globally|
|**show cdp neighbors**_[detail]_|Lists summary (or detailed) information about each neighbor connected to the device|
|**show interfaces**|Displays detailed information about interface status, settings and counters|
|**show interface status**|Displays the interface line status|
|**show interfaces switchport**|Displays many configuration settings and current operational status, including VLAN trunking details|
|**show interfaces trunk**|Lists information about the currently operational trunks and the VLANs supported by those trunks|
|**show vlan**  <br>**show vlan brief**|Lists each VLAN and all interfaces assigned to that VLAN but does not include trunks|
|**show vtp status**|Lists the current VLAN Trunk Protocol (VTP) status, including the current mode|
### Routing and VLAN Commands
|                                                                                                           |                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| --------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **show ip route**                                                                                         | Displays the current state of the IP routing of all known routes that are either statically configured or learned dynamically through a routing protocol                                                                                                                                                                                                                                                                                                           |
| **ip route** _network-number network-mask {ip-address \| interface}_                                      | Sets a static route in the IP routing table                                                                                                                                                                                                                                                                                                                                                                                                                        |
| **router rip**                                                                                            | Enables a Routing Information Protocol (RIP) routing process, which places you in router configuration mode                                                                                                                                                                                                                                                                                                                                                        |
| **network** _ip-address_                                                                                  | Associates a network with a RIP routing process                                                                                                                                                                                                                                                                                                                                                                                                                    |
| **version 2**                                                                                             | Configures the software to receive and send only RIP version 2 packets                                                                                                                                                                                                                                                                                                                                                                                             |
| **no auto-summary**                                                                                       | Disables automatic summarization                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| **default-information originate**                                                                         | Generates a default route into RIP                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| **passive-interface** _interface_                                                                         | Sets the specified interface to passive RIP mode, which means RIP routing updates are accepted by, but not sent out of, the interface                                                                                                                                                                                                                                                                                                                              |
| **show ip rip database**                                                                                  | Displays the contents of the RIP routing database                                                                                                                                                                                                                                                                                                                                                                                                                  |
| **ip nat** _[inside \| outside]_                                                                          | Configure Network Address Translation (NAT), which allows private IP addresses on a local network to be translated into public IP addresses before being sent over the internet                                                                                                                                                                                                                                                                                    |
| **ip nat inside source** _{list{access-list-number \| access-list-name}} interface type number[overload]_ | Establishes dynamic source translation. Use of the “list” keyword enables you to use an ACL to identify the traffic that will be subject to NAT. The “overload” option enables the router to use one global address for many local addresses.                                                                                                                                                                                                                      |
| **ip nat inside source static** _local-ip global-ip_                                                      | Establishes a static translation between an inside local address and an inside global address                                                                                                                                                                                                                                                                                                                                                                      |
| **vlan**                                                                                                  | Creates a VLAN and enters VLAN configuration mode for further definitions                                                                                                                                                                                                                                                                                                                                                                                          |
| **switchport access vlan**                                                                                | Sets the VLAN that the interface belongs to.                                                                                                                                                                                                                                                                                                                                                                                                                       |
| **switchport trunk encapsulation dot1q**                                                                  | Specifies 802.1Q encapsulation on the trunk link.                                                                                                                                                                                                                                                                                                                                                                                                                  |
| **switchport access**                                                                                     | Configures a specific Ethernet port on a switch to operate in access mode to accommodate an end device such as a computer, server or printer. The port must then be assigned to a single VLAN.                                                                                                                                                                                                                                                                     |
| **vlan vlan-id** _[name vlan-name]_                                                                       | Configures a specific VLAN name (1 to 32 characters)                                                                                                                                                                                                                                                                                                                                                                                                               |
| **switchport mode** _{ access \| trunk }_                                                                 | Configures the VLAN membership mode of a port. The access port is set to access unconditionally and operates as a non-trunking, single VLAN interface that sends and receives non-encapsulated (non-tagged) frames. An access port can be assigned to only one VLAN. The trunk port sends and receives encapsulated (tagged) frames that identify the VLAN of origination. A trunk is a point-to-point link between two switches or between a switch and a router. |
| **switchport trunk** _{encapsulation { dot1q }_                                                           | Sets the trunk characteristics when the interface is in trunking mode. In this mode, the switch supports simultaneous tagged and untagged traffic on a port.                                                                                                                                                                                                                                                                                                       |
| **encapsulation dot1q vlan-id**                                                                           | Defines the matching criteria to map 802.1Q frames ingress on an interface to the appropriate service instance                                                                                                                                                                                                                                                                                                                                                     |
| **show spanning-tree**                                                                                    | Provides detailed information about the Spanning Tree protocol for all VLANs                                                                                                                                                                                                                                                                                                                                                                                       |