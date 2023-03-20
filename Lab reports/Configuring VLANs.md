#networking #AI #practical #cisco #packettracer 

# Check default configs
![[Pasted image 20230319073014.png]]
VLAN 1 of a switch is the system default. It is used to management purposes, every interface is already assigend to that VLAN. We are supposed to reassign them. Other VLANs from 1002-1005 are also used for system purposes, but not interfaces are assigned to them. Confi

# Static config
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

# Dynamic config
We cannot communicate with above PCs unless there are IPs assigned with them. Rather than assigning IPs and config VLANs seperately, we can config the switch to create VLANs based on the network each PC belong to.
 
```embed
title: 'Configure Subnet-based VLAN Groups on a Switch through the CLI'
image: 'https://www.cisco.com/c/dam/en/us/support/docs/smb/switches/cisco-350-series-managed-switches/images/ijgm-07192017-create-subnet-based-vlan-group-step1.png'
description: 'his article provides instructions on how to configure subnet-based groups on Sx350, SG350X, Sx500, Sx550X series switches through the CLI.'
url: 'https://www.cisco.com/c/en/us/support/docs/smb/switches/cisco-350-series-managed-switches/smb5658-configure-subnet-based-vlan-groups-on-a-switch-through-the-c.html'
```


