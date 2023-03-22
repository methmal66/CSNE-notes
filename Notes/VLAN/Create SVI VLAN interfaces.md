---
tags: networking AI packettracer practical cisco vlan
author: methmal66
created: [[2023-03-22]]
modified: [[2023-03-22]]
---
The IP addresses that are configured will serve as the default gateways to the hosts in the respective VLANs. Notice the informational messages showing the line protocol on both SVIs changed to up.
```cisco
S(config)#int vlan10
S(config-if)#ip add 192.168.10.1 255.255.255.0
S(config-if)#no shut

S(config-if)#int vlan20
S(config-if)#ip add 192.168.20.1 255.255.255.0
S(config-if)#no shut
```
