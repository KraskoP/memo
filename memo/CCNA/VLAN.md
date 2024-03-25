# VLAN
**802.1Q**, often referred to as **Dot1q**, is the [networking](https://en.wikipedia.org/wiki/Computer_network "Computer network") standard that supports [virtual local area networking](https://en.wikipedia.org/wiki/Virtual_local_area_network "Virtual local area network") (VLANs) on an [IEEE 802.3](https://en.wikipedia.org/wiki/IEEE_802.3 "IEEE 802.3") [Ethernet](https://en.wikipedia.org/wiki/Ethernet "Ethernet") network. The standard defines a system of **VLAN tagging** for [Ethernet frames](https://en.wikipedia.org/wiki/Ethernet_frame "Ethernet frame") and the accompanying procedures to be used by [bridges](https://en.wikipedia.org/wiki/Network_bridge "Network bridge") and [switches](https://en.wikipedia.org/wiki/Network_switch "Network switch") in handling such frames.
### Frame format

![[1280px-Ethernet_802.1Q_Insert.svg (1).png]]

802.1Q adds a 32-bit field between the source [MAC address](https://en.wikipedia.org/wiki/MAC_address "MAC address") and the [EtherType](https://en.wikipedia.org/wiki/EtherType "EtherType") fields of the original frame. Under 802.1Q, the maximum frame size is extended from 1,518 bytes to 1,522 bytes. The minimum frame size remains 64 bytes, but a bridge may extend the minimum size frame from 64 to 68 bytes on transmission. This allows a tag to be popped without needing additional padding.[[2]](https://en.wikipedia.org/wiki/IEEE_802.1Q#cite_note-3)[[3]](https://en.wikipedia.org/wiki/IEEE_802.1Q#cite_note-4) Two bytes are used for the tag protocol identifier (TPID), the other two bytes for tag control information (TCI). The TCI field is further divided into PCP, DEI, and VID.[[4]](https://en.wikipedia.org/wiki/IEEE_802.1Q#cite_note-5)

![[802.1q_frame_format.png]]
#### Tag protocol identifier (TPID)
A 16-bit field set to a value of 0x8100[[b]](https://en.wikipedia.org/wiki/IEEE_802.1Q#cite_note-6) in order to identify the frame as an IEEE 802.1Q-tagged frame. This field is located at the same position as the EtherType field in untagged frames, and is thus used to distinguish the frame from untagged frames.
#### Tag control information (TCI)
A 16-bit field containing the following sub-fields:
#### Priority code point (PCP)
A 3-bit field which refers to the [IEEE 802.1p](https://en.wikipedia.org/wiki/IEEE_802.1p "IEEE 802.1p") [class of service (CoS)](https://en.wikipedia.org/wiki/Class_of_service "Class of service") and maps to the frame priority level. Different PCP values can be used to prioritize different classes of traffic.[[5]](https://en.wikipedia.org/wiki/IEEE_802.1Q#cite_note-7)
#### Drop eligible indicator (DEI)
A 1-bit field. (formerly CFI[[c]](https://en.wikipedia.org/wiki/IEEE_802.1Q#cite_note-9)) May be used separately or in conjunction with PCP to indicate frames eligible to be dropped in the presence of congestion.[[7]](https://en.wikipedia.org/wiki/IEEE_802.1Q#cite_note-10)
#### VLAN identifier (VID)
A 12-bit field specifying the VLAN to which the frame belongs. The values of 0 and 4095 (0x000 and 0xFFF in [hexadecimal](https://en.wikipedia.org/wiki/Hexadecimal "Hexadecimal")) are reserved. All other values may be used as VLAN identifiers, allowing up to 4,094 VLANs. The reserved value 0x000 indicates that the frame does not carry a VLAN ID; in this case, the 802.1Q tag specifies only a priority (in PCP and DEI fields) and is referred to as a _priority tag_. On bridges, VID 0x001 (the default VLAN ID) is often reserved for a [network management](https://en.wikipedia.org/wiki/Network_management "Network management") VLAN; this is vendor-specific. The VID value 0xFFF is reserved for implementation use; it must not be configured or transmitted. 0xFFF can be used to indicate a wildcard match in management operations or filtering database entries.[[8]](https://en.wikipedia.org/wiki/IEEE_802.1Q#cite_note-11)

### Terminology
**Trunking:** Carrying multiple VLANs over the same physical connection
**Native VLAN:** By default, frames in this VLAN are untagged when sent across a trunk
**Access VLAN:** The VLAN to which an access port is assigned
**Voice VLAN:** If configured, enables minimal trunking to support voice traffic in addition to data traffic on an access port
**Switched Virtual Interface (SVI):** A virtual interface which provides a routed gateway into and out of a VLAN
### CISCO Commands
[[CISCO Commands]] related to VLANs. This is an

| VLAN Creation                         |
| ------------------------------------- |
| Switch(config)# vlan 100              |
| Switch(config-vlan)# name Engineering |

| Access Port Configuration                     |
| --------------------------------------------- |
| Switch(config-if)# switchport mode acces      |
| Switch(config-if)# switchport negotiate       |
| Switch(config-if)# switchport access vlan 100 |
| Switch(config-if)# switchport voice vlan 150  |

| SVI Configuration                                         |
| --------------------------------------------------------- |
| Switch(config)# interface vlan100                         |
| Switch(config-if)# ip address 192.168.100.1 255.255.255.0 |

---
## DTP Dynamic Trunking Protocol
### DTP

![[DTP1.png]]



- _**Access**_ — Puts the [Ethernet](https://en.wikipedia.org/wiki/Ethernet "Ethernet") port into permanent nontrunking mode and negotiates to convert the link into a nontrunk link. The Ethernet port becomes a nontrunk port even if the neighboring port does not agree to the change.
- _**Trunk**_ — Puts the Ethernet port into permanent trunking mode and negotiates to convert the link into a trunk link. The port becomes a trunk port even if the neighboring port does not agree to the change.
- _**Dynamic Auto**_ — Makes the Ethernet port willing to convert the link to a trunk link. The port becomes a trunk port if the neighboring port is set to trunk or _dynamic desirable_ mode. This is the default mode for some switchports.
- _**Dynamic** **Desirable**_ — Makes the port actively attempt to convert the link to a trunk link. The port becomes a trunk port if the neighboring Ethernet port is set to trunk, _dynamic desirable_ or _dynamic auto_ mode.
- _**No**-**negotiate**_ — Disables DTP. The port will not send out DTP frames or be affected by any incoming DTP frames. If you want to set a trunk between two switches when DTP is disabled, you must manually configure trunking using the (switchport mode trunk) command on both sides.



S1# sh int trunk
S1(config) int g0/0
S1 (config-if) switchport mode dynamic auto (desirable)
