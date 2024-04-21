# Tech Deep Dive NSX 

[Smartsheet](https://app.smartsheet.com/dashboards/Qf34Cfx4Wm63RQ6mjX8fM32X3q95wmrfPVpHF261_)
[Lab roster](https://broadcom.ent.box.com/file/1496517136358?sb=/activity)

## NAP NSX Application Platform
![[Pasted image 20240410112522.png]]

This is Appliance. 

Deployment and design in NSX:
![[Pasted image 20240410113024.png]]

1) Security on VDS only. We don't need to migrate VM. We nned to understand Client's needs and strategy. If Client wants to continue we have to consider second design. There is no simple 
	1) VIB for security only are different than VIB for network and security.
	2) This is security based on VLANs not on NSX zones (NSX VLAN segments)
	3) Mikrosegmentation
2) We need create overlay layer.  We must migrate VM from standard PG to NSX PG
	1) standard NSX Installation

## Network segmentation consideration
Network segmentation - do it properly -  we need to know a lot of things:
![[Pasted image 20240410114325.png]]

![[Pasted image 20240410114752.png]]

Another part is to define a policy model... Security model architecture is crucial. 
We have to define policy model for all the layers, not only for Applications.

![[Pasted image 20240410114959.png]]

First phase is zone definition
![[Pasted image 20240410115448.png]]

And after that something more complex. Segmentation at the app level
![[Pasted image 20240410115613.png]]

The last stage is microsegmetation. EG APP with Mid layer. Mid layer with DB or queue service.

![[Pasted image 20240410115718.png]]

## NSX Groupng
Based on Network, Workload, Application and User Context

![[Pasted image 20240410120544.png]]

There are dynamic and static groups. Tags are a big friends for Security.
We can combine tags. 

**DR** Distributed Routing
![[Pasted image 20240410121014.png]]


![[Pasted image 20240410121044.png]]

By default when you create rule, this rule is applied to all FW.
You should apply rules to policies or rules level.

Policy rule has a precedence... 


![[Pasted image 20240410122257.png]]

![[Pasted image 20240410122404.png]]

![[Pasted image 20240410122625.png]]

![[Pasted image 20240410122704.png]]

![[Pasted image 20240410122903.png]]

![[Pasted image 20240410122922.png]]

### VPC

![[Pasted image 20240410123011.png]]

![[Pasted image 20240410123145.png]]

![[Pasted image 20240410123559.png]]

## Visibility and Enforcement across the Attack Chain
![[Pasted image 20240410123902.png]]

![[Pasted image 20240410124229.png]]

![[Pasted image 20240410124443.png]]

![[Pasted image 20240410124724.png]]


![[Pasted image 20240410125124.png]]

![[Pasted image 20240410125149.png]]

![[Pasted image 20240410125416.png]]

![[Pasted image 20240410125933.png]]

![[Pasted image 20240410131612.png]]

![[Pasted image 20240410131630.png]]

![[Pasted image 20240410132817.png]]

![[Pasted image 20240410133131.png]]


![[Pasted image 20240410133600.png]]










