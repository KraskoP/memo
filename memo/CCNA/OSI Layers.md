# OSI Layers

The best way to memorize all the layers in OSI is to memorize mnemonic:
1. Please Do Not Throw Sausage Pizza Away.
2. **A**ll **P**eople **S**eem **t**o **N**eed **D**ata **P**rocessing.

To jest obrazek 1 ![to jest opis](osi.png)


### Physical

The lowest layer of the OSI model is concerned with data communication in the form of electrical, optic, or electromagnetic signals physically transmitting information between networking devices and infrastructure. The [physical layer](https://en.wikipedia.org/wiki/Physical_layer) is responsible for the communication of unstructured raw data streams over a physical medium. It defines a range of aspects, including:

- Electrical, mechanical, and physical systems and networking devices that include specifications such as cable size, signal frequency, voltages, etc.
- [Topologies](https://en.wikipedia.org/wiki/Network_topology) such as Bus, Star, Ring, and Mesh
- [Communication modes](https://www.studytonight.com/computer-networks/transmission-mode) such as Simplex, Half Duplex, and Full Duplex
- Data transmission performance, such as [Bit Rate](https://en.wikipedia.org/wiki/Bit_rate) and [Bit Synchronization](https://en.wikipedia.org/wiki/Self-synchronizing_code)
- Modulation, switching, and interfacing with the physical transmission medium
- Common protocols including Wi-Fi, Ethernet, [and others](https://en.wikipedia.org/wiki/List_of_network_protocols_(OSI_model)#Layer_1_(Physical_Layer))
- Hardware including networking devices, antennas, cables, modem, and intermediate devices such as repeaters and hubs

### Data Link

The second layer of the OSI model concerns data transmission between the nodes within a network and manages the connections between physically connected devices such as switches. The raw data received from the physical layer is synchronized and packaged into data [frames](https://en.wikipedia.org/wiki/Frame_(telecommunications)) that contain the necessary protocols to route information between appropriate nodes. The [data link layer](https://en.wikipedia.org/wiki/Data_link_layer) is further divided into two sublayers:

- The Logical Link Control (LLC) sublayer is responsible for [flow controls](https://en.wikipedia.org/wiki/Flow_control_(data)) and [error controls](https://en.wikipedia.org/wiki/Error_control) that ensure error-free and accurate data transmission between the network nodes.
- The Media Access Control (MAC) sublayer is responsible for managing access and permissions to transmit data between the network nodes. The data is transmitted sequentially and the layer expects acknowledgement for the encapsulated raw data sent between the nodes.

### Network

The third layer of the OSI model organizes and transmits data between multiple networks.

The network layer is responsible for routing the data via the best physical path based on a range of factors including network characteristics, best available path, [traffic controls](https://en.wikipedia.org/wiki/Network_traffic_control), congestion of data packets, and priority of service, among others. The network layer implements logical addressing for data packets to distinguish between the source and destination networks.

Other functions include [encapsulation and fragmentation](https://en.wikipedia.org/wiki/Encapsulation_(networking)), congestion controls, and error handling. The outgoing data is divided into packets and incoming data is reassembled into information that is consumable at a higher application level. Network layer hardware includes routes, bridge routers, 3-layer switches, and protocols such as Internet (IPv4) Protocol version 4 and Internet Protocol version 6 (IPv6).

### Transport

The fourth layer of the OSI model ensures complete and reliable delivery of data packets.

- The [transport layer](https://en.wikipedia.org/wiki/Transport_layer) provides mechanisms such as error control, flow control, and congestion control to keep track of the data packets, check for errors and duplication, and resend the information that fails delivery. It involves the service-point addressing function to ensure that the packet is sent in response to a specific process (via a port address).
- [Packet Segmentation](https://en.wikipedia.org/wiki/Packet_segmentation) and reassembly ensure that the data is divided and sequentially sent to the destination where it is rechecked for integrity and accuracy based on the receiving sequence.

Common protocols include the [Transmission Control Protocol (TCP)](https://en.wikipedia.org/wiki/Transmission_Control_Protocol) for connection-oriented data transmission and [User Datagram Protocol (UDP)](https://en.wikipedia.org/wiki/User_Datagram_Protocol) for connectionless data transmission.

### Session

As the first of three layers that deal with the software level, the [session layer](https://en.wikipedia.org/wiki/Session_layer) manages sessions between servers to coordinate communication. Session refers to any interactive data exchange between two entities within a network. Common examples include HTTPS sessions that allow Internet users to visit and browse websites for a specific time period. The Session Layer is responsible for a range of functions including opening, closing, and re-establishing session activities, authentication and authorization of communication between specific apps and servers, identifying full-duplex or half-duplex operations, and synchronizing data streams.

Common Session Layer protocols include:

- Remote procedure call protocol (RPC)
- Point-to-Point Tunneling Protocol (PPTP)
- Session Control Protocol (SCP)
- Session Description Protocol (SDP), as described [here](https://en.wikipedia.org/wiki/Session_layer#Protocols)

### Presentation

The sixth layer of the OSI model converts data formats between applications and the networks. Responsibilities of the [presentation layer](https://en.wikipedia.org/wiki/Presentation_layer) include:

- [Data conversion](https://en.wikipedia.org/wiki/Data_conversion)
- [Character code translation](https://en.wikipedia.org/wiki/Character_encoding#Character_encoding_translation)
- [Data compression](https://en.wikipedia.org/wiki/Data_compression)
- [Encryption and decryption](https://en.wikipedia.org/wiki/Encryption)

The presentation layer, also called the syntax layer, maps the semantics and syntax of the data such that the received information is consumable for every distinct network entity. For example, the data we transfer from our encryption-based communication app is formatted and encrypted at this layer before it is sent across the network.

At the receiving end, the data is decrypted and formatted into text or media information as originally intended. The presentation layer also serializes complex information into transportable formats. The data streams are then deserialized and reassembled into original object format at the destination.

### Application

The [application layer](https://en.wikipedia.org/wiki/Application_layer) concerns the networking processes at the application level. This layer interacts directly with end-users to provide support for email, network data sharing, file transfers, and directory services, among other distributed information services. The upper most layer of the OSI model identifies networking entities to facilitate networking requests by end-user requests, determines resource availability, synchronizes communication, and manages application-specific networking requirements. The application layer also identifies constraints at the application level such as those associated with authentication, privacy, quality of service, networking devices, and data syntax.

Common [application layer protocols](https://en.wikipedia.org/wiki/Application_layer#Application_layer_protocols) include:

- File Transfer Protocol (FTP)
- Simple Mail Transfer Protocol (SMTP)
- Domain Name System (DNS)