#networking #AI #hardware 
Forwarding network traffic from one VLAN to another VLAN

>[!important] Practical lab
>Refer this page for more practical hands on understanding
>[[Configuring inter VLAN routing]]

# Legacy method
The first inter-VLAN routing solution relied on using a router with multiple Ethernet interfaces. Each router interface was connected to a switch port in different VLANs. The router interfaces served as the default gateways to the local hosts on the VLAN subnet.

![[Pasted image 20230320062017.png|500]]

# Router-on-a-stick method
connect a router with a single physical link to a switch and perform IP routing between VLANs.
- In the switch, this physical link is configured as a [[Trunk port]] allowing all VLANs that are going to be routed
- In the router, this physical interface is represented as multiple virtual sub-interfaces, one for each VLAN
- An IP address from each VLAN is then configured on each sub- interface and the router performs IP routing between connected networks

![[Pasted image 20230320062413.png|500]]

>[!note]- 802.1Q encapsulation
>Before frames leaving the switch, a tag is inserted.
>![[Pasted image 20230320063202.png|500]]

# Multilayer method
The modern method of performing inter-VLAN routing is to use Layer 3 switches and [[SVI]]. They are more commonly deployed in a campus LAN

![[Pasted image 20230320063949.png]]

## Advantages 
- Latency is much lower because data does not need to leave the switch to be routed to a different network
- There is no need for external links from the switch to the router for routing
- They are not limited to one link because Layer 2 [[EtherChannels]] can be used as trunk links between the switches to increase bandwidth
