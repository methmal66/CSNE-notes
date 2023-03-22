---
tags: networking AI vlan practical packettracer cisco 
author: methmal66
created: [[2023-03-21]]
modified: [[2023-03-21]]
---
- Network admin configure port-by-port
- Each port is assigned with a specific VLAN

![[Pasted image 20230319150419.png]]
![[static vlan.pkt]]

Create VLANs with a VLAN ID, then set a name
```cisco
Switch(config)#vlan 10
Switch(config-vlan)#name IT
Switch(config-vlan)#vlan 20
Switch(config-vlan)#name SALES
```

Assign interfaces to each VLAN. It can be done for each interface or a range of interfaces at once
```cisco
Switch(config)#int fa0/1
Switch(config-if)#switchport mode access
Switch(config-if)#switchport access vlan 10
Switch(config-if)#
Switch(config-if)#int fa0/2
Switch(config-if)#switchport mode access
Switch(config-if)#switchport access vlan 10
Switch(config-if)#
Switch(config-if)#int range fa0/3-4
Switch(config-if-range)#switchport mode access
Switch(config-if-range)#switchport access vlan 20
```
