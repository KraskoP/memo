# Cabling and packet flows
## Cables

terminators not allow signal bouncing back
baseband - allow only one signal in a wire at a given time
### 10base5
- 10Mbs
- base - baseband
- 5 - 500m
### 10base2
- 10Mbs 
- base
- 2 - 185m

### 10baseT
: 10Mbs
: baseband
: T twisted pair

## MAC Address 
Media Acccess Control
24 bits OUI- Organizational Identifier
24 bits Station Address

On the webpage [www.wireshark.org/tools/oui.lookup](www.wireshark.org/tools/oui.lookup) is a tool do decipher MAC
### Structure  
It consists from 6 bytes -> 3 bytes OUI and 3 bytes NIC (Network Interface Controller Specific) Station Address 
First byte is most significant: 

| b7  | b6  | b5  | b4  | b3  | b2  | b1                       | b0            |
| --- | --- | --- | --- | --- | --- | ------------------------ | ------------- |
|     |     |     |     |     |     | 0 - globally unique      | 0 - unicast   |
|     |     |     |     |     |     | 1 - locally administered | 1 - multicast |
### CSMA/CD
CS  
: Carrier sense
MA  
:  multiple access
CD  
:  collision detection

## HUB
layer 1 device
physical topology - Star
logical topology  - Bus
Single Collision Domain
Single Broadcast Domain
10Mbs shared


### Bridge
layer 2 [[OSI Layers]] device (data link layer)
MAC address table
CAM table - Content Addressable Memory
physical topology - Star
Multiple Collision Domain
Single Broadcast Domain
Software is responsible for maintaining packets

### Switch
layer 2 [[OSI Layers]] device (data link layer)
ASIC is responsible for maintaining traffic
ASIC (Application Specific Integrated Circuits)
Half Duplex is - only one party can talk at the time (CSMA/CD)

Full Duplex - must be on both sides

### Router
works on layer 3- [[OSI Layers]] network Layer