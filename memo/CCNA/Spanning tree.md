# Spanning tree
Initial protocol 802.1D. This protocol was superseded by Rapid Spanning Tree or Multiple Spanning Tree.


## IEEE 802.1D
Legacy standard with CST - Common Spanning Tree
That was introduced where bridges were used.

CST - One Spanning Tree instance for the entire bridged network

PVST - Per VLAN Spanning Tree only per ISL
PVST+ - Per VLAN Spanning Tree only per ISL and 802.1Q

eg. 802.1S Two Spanning Tree instances: 1-100 Instance1 and 101-200 Instance2

RSTP - Rapid Spanning Tree

### BPDU and Bridge ID
**B**ridge **P**rotocol **D**ata **U**nit

If Spanning tree is enables BPDU packet is sent every 2 sec to allow switch to inform about themselves.
https://networklessons.com/spanning-tree/spanning-tree-port-states

- **Listening state**: Only a root or designated port will move to the listening state. The non-designated port will stay in the blocking state. No data transmission occurs at this state for 15 seconds just to make sure the topology doesn’t change in the meantime. After the listening state, we move to the learning state.
- **Learning state:** At this moment the interface will process Ethernet frames by looking at the source MAC address to fill the mac-address-table. Ethernet frames, however, are not forwarded to the destination. It takes 15 seconds to move to the next state, called the forwarding state.
- **Forwarding state:** This is the final state of the interface, and finally, the interface will forward Ethernet frames so that we have data transmission!

When a port is not a designated or root port, it will be in **blocking mode**.

| State      | Forward Frames | Learn MAC Addresses | Duration   |
| ---------- | -------------- | ------------------- | ---------- |
| Blocking   | No             | No                  | 20 seconds |
| Listening  | No             | No                  | 15 seconds |
| Learning   | No             | Yes                 | 15 seconds |
| Forwarding | Yes            | Yes                 | –          |



S1# sh run | include span
S1# sh spanning-tree

### Root port and Designated port
How the process of elections looks like?

1. first decision - Determine who the root switch is
	1. based on Bridge ID
	2. and MAC. The lowest MAC wins
2. [Lowest path cost](https://en.wikipedia.org/wiki/Spanning_Tree_Protocol)

| Data rate (link bandwidth) | Original STP cost (802.1D-1998) | RSTP/MSTP cost  [recommended value](https://en.wikipedia.org/wiki/Spanning_Tree_Protocol#cite_note-802.1Q-3) |
| -------------------------- | ------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| 4 Mbit/s                   | 250                             | 5,000,000                                                                                                    |
| 10 Mbit/s                  | 100                             | 2,000,000                                                                                                    |
| 16 Mbit/s                  | 62                              | 1,250,000                                                                                                    |
| 100 Mbit/s                 | 19                              | 200,000                                                                                                      |
| 1 Gbit/s                   | 4                               | 20,000                                                                                                       |
| 2 Gbit/s                   | 3                               | 10,000                                                                                                       |
| 10 Gbit/s                  | 2                               | 2,000                                                                                                        |
| 100 Gbit/s                 | N/A                             | 200                                                                                                          |
| 1 Tbit/s                   | N/A                             | 20                                                                                                           |
3. Neighbor Bridge ID
4. XX
5. XX

## Extended Bridge ID and PortFast
Great source of information is [here](https://notes.networklessons.com/stp-bridge-priority-values)

### Extended Bridge ID

Valid values for bridge priorities are between 0 and 61440, but the value must be in increments of 4096. This is because the VLAN ID is a 12-bit value that can represent up to 4096 VLAN IDs. The Bridge Priority is effectively a 4-bit value and is stored in a 16-bit field along with the VLAN ID:

![[Bridge_ID.png]]

In the Per-VLAN Spanning Tree Plus (PVST+) variant of STP, which is common on Cisco devices, the 2-byte (16-bit) Priority field in the BPDU is divided into two parts. The most significant 4 bits are for the Priority, and the least significant 12 bits are for the VLAN ID.

Thus only Bridge priorities incremented in steps of 2^12 (4096) are valid. For instance, a bridge with a set priority of 12288 that is using VLAN 7 will actually have a priority value in the BPDU field of 12288+7 = 12295. That priority value is unique to VLAN 7 since there can be a root bridge for each individual VLAN, and the priorities must be unique.
### Port Fast
Portfast is a Cisco proprietary solution to deal with [STP topology changes](https://notes.networklessons.com/stp-topology-change-process).
**Edge Port** - name for other vendors

Portfast does two things for us:

- Interfaces with portfast enabled that come up will go to forwarding mode immediately, the interface will skip the listening and learning state.
- A switch will never generate a topology change notification for an interface that has portfast enabled.

It’s a good idea to [enable portfast](https://notes.networklessons.com/stp-configuring-portfast) on interfaces that are connected to hosts because these interfaces are likely to go up and down all the time. Don’t enable portfast on an interface to another hub or switch.

For additional [STP](https://notes.networklessons.com/spanning-tree-protocol-stp) fine tuning features, take a look at [STP fine tuning the spanning tree protocol](https://notes.networklessons.com/stp-fine-tuning-the-spanning-tree-protocol).

Links:

[https://networklessons.com/spanning-tree/cisco-portfast-configuration](https://networklessons.com/spanning-tree/cisco-portfast-configuration)

[https://networklessons.com/spanning-tree/spanning-tree-topology-change-notification-tcn/](https://networklessons.com/spanning-tree/spanning-tree-topology-change-notification-tcn/)

### Cisco Commands
[[CISCO Commands]] related to STP VSTP+

S1# sh spanning-tree

### BPDU Guard
BPDU Guard is mechanism to protect your spanning-tree network. 
Malicious actions, errors, loop, connecting switch with lowest ID to negatively change our network, changing root.

BPDU Guard disables port if any BPDU traffic reaches this port.
Should be enabled on all *portfast* ports.
It can be enabled globally on the switch or on per interface basis.

S2(config)# Spanning-tree portfast edge bpduguard - globally enable bpdu guaard on S2
S2# show spanning-tree inter gigabitethernet 0/1 portfast

S2# show spanning-tree inconsistentporst - pokaż jakie porty są (err-disabled) turned off because of bpdu guard
S2# show spanning-tree summary
S2(config-if)# do sh run int g0/1
S2(config-if)# no spanning-tree  portfast
S2# sh spanning-tree blockedports



