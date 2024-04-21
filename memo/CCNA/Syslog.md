# Syslog
## logging to a console

A source of knowledge of syslog protocol: [RFC 5424](https://datatracker.ietf.org/doc/html/rfc5424)
or [wikipedia](https://en.wikipedia.org/wiki/Syslog)

logging synchronous - that is - during consol operation, when there is a log message our command is recreated
no logging synchronoun - command is **not** recreated



sh logging - shows the level of logging

debug is a command for turn on /off debug level.

debug ip ospf adj - command turns on debugging ospf protocol adj messages
sh debug  - shows what we are debuggind
undebug all - turns off all debugs

logging ?
logging console 3
we changed level of logs on the console

debug is what kind and at what level of comunicats we want to see 
logging - where to see logs and at what level

**telnet is not console** 
logging on console is differnet that logging on telnet session
if we want to **see logs on the console we have to run command**
```cisco
term monitor
term no monitor - to stop
```
### logging to monitor
```
conf t
logging monitor errors
sh logging
```
in this case we will see all the logs on console (because default level is debugging)
but on the monitor we will see only errors (level 3)

to stop logging on the console (or monitor- telnet)
```cisco
no logging console
```
### buffer logging 
to check buffer logging - sh logging
to change that:
``` cisco
conf t
logging buffered 7
exit
sh log
``` 
we can change the buffer size: logging buffered < >

sh log - contains now a logs 

### centralized log server
```cisco
conf t
logging a.b.c.d
logging trap 7
sh log
```
### timestamps and seq numbers

We can add timestamps in different format
```cisco
conf t
service timestamps ?
service timestamps log or debug
service timestamps log ?
daytime or uptime

```

we can format day, time, year, sec, msec...
```cisco
service timestamps log datetime ?
no service timestamps - no timestampsq
```
