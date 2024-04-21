# NTP
NTP uses UDP port 123
- unicast
- brodcast
- multicast

## Configuration
sh clock - what time is it?
clock timezone - to set timezone
clock summer-time - to set summer time

```cisco
clock timezone GMT ?
clock timezone GMT 0 ?
clock timezone GMT 0 0

clock summer-time ?
clock summer-time reccuring  

clock summer-time reccuring last Sun Mar 1:Fab500px:  las Sun Oct 1:00
clock set ?
```

## NTP configuration
```cisco
conf t
ntp master 10
ntp source loopback 0 , assume 3.3.3.3
exit
sh run | i ntp
sh ntp assoc
sh ntp status
```

on the other devces
``` cisco
conf t
ntp server 3.3.3.3 
end
sh ntp status
ntp associ
```