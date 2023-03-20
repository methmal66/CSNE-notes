#networking #hardware #practical #cisco #packettracer #AI 

# Legacy method
![[Pasted image 20230320072434.png|500]]
![[legacy inter vlan routing.pkt]]

Create VLANs and assign interfaces
```cisco
S(config)#vlan 10
S(config-vlan)#name IT
S(config-vlan)#vlan 20
S(config-vlan)#name SALES

S(config)#int range fa0/1-3
S(config-if-range)#switchport mode access
S(config-if-range)#switchport access vlan 10
S(config-if-range)#int range fa0/4-6
S(config-if-range)#switchport mode access
S(config-if-range)#switchport access vlan 20
```

# Router-on-a-stick
