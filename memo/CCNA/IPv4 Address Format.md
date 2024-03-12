# IPv4 Address Format

CIDR - Classless Inter-Domain Routing
## Format
- IP address is 32 bit binary number
- Divided into 4 octets (8 bits or 1 byte)
- 00001010.00000001.00001000.00000010
- which is 10.1.8.2
## Address Classes
Are used from 1981 until introduction of Classless in domain routing in 1993
There are 5 classes
- Class A - unicast
- Class B - unicast 
- Class C - unicast
- Class D - multicast
- Class E - reserved for future, experimental purposes

IPv6 - does not use address classes
IPv4 - address classes was replaced by CIDR
## Class A
x.x.x.x
first octet always stats with 0
00000000 up to 01111111 (from 0 to 127)

### Exceptions:
127 is reserved for loopback: 127.0.0.1

127.0.0.1 - everything starting with 127.x.x.x is a loopback address"
- 127.0.0.1
- 127.2.3.4
- 127.127.127.127

entire network is .... wasted 16 mln addresses (=255\*255\*255)

0 network is reserved for default network - 0.1.1.1

Actual range is 1.0.0.0 up to 126.255.255.255

| decimal | binary   |
| ------- | -------- |
| 1       | 00000001 |
| 126     | 01111110 |
**00000000**.00000000.00000000.00000000
**networks**.hosts
## Class B
x.x.x.x
First octet always starts with binary 10 (one&zero)
Binary range:
128.0.0.0. to 191.255.255.255

| decimal | binary   |
| ------- | -------- |
| 128     | 10000000 |
| 191     | 10111111 |
**00000000.00000000**.00000000.00000000
**networks**.hosts

### Class C
x.x.x.x
First octet always starts with binary 110 (one&one&zero)
Binary range:
192.0.0.0. to 223.255.255.255

| decimal | binary   |
| ------- | -------- |
| 192     | 11000000 |
| 223     | 11011111 |
**00000000.00000000.00000000**.00000000
**networks**.hosts

### Class D
this is for multicast
x.x.x.x
First octet always starts with binary 1110 (one&one&one&zero)

On device is talking to group of devices:
224.0.0.0 to 239.255.255.255

| decimal | binary   |
| ------- | -------- |
| 224     | 11000000 |
| 239     | 11011111 |
### Class E
x.x.x.x
starts with 1111 (one&one&one&one)
240.0.0.0. to 255.255.255.255

## Local loopback Address
IPv4: 127.0.0.1
IPv6: \::\1

**Note**
routers have loopback addresses which are not the same ad the local loopback addresses
Router loopback address 10.1.1.1/32

## Private Addresses
RFC1918 - Private IP Addresses 
not routable on the internet
You can find this RFC [here](tools.ietf.org/html/rfc1918)

10.0.0.0 - 10.255.255.255 (10/8 prefix) 1 class A Network
172.16.0.0. 172.31.255.255 (172.16/12 prefix) 16 class B networks
192.168.0.0. 192.168.255.255 (256 class C networks)

IPv4 Link - Local Addresses
PC configured for DHCP
when no server is available
169.254.0.0/16
Those computes can communicate when there is no DHCP.
This IP is not routable.
