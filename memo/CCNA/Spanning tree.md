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
**B**ridge **P**rotocol **D**ata **U**nit is sent every 2 sec to allow switch to inform about themselves.

If Spanning tree is enables BPDU