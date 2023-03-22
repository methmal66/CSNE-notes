---
tags: networking AI cisco packettracer practical ipv6 
author: mthmal66
created: [[2023-03-22]]
modified: [[2023-03-22]]
---
![[Pasted image 20230314080928.png|500]]
![[auto slaac ipv6.pkt]]

Assign automatic ip to interfaces. Network prefix together with standard to use `eui-64` must be given
```cisco
R(config)#int gi0/0/0
R(config-if)#ipv6 add auto
R(config-if)#ipv6 add 2001:db8:acad:1::/64 eui-64
R(config-if)#no shutdown

R(config-if)#int gi0/0/1
R(config-if)#ipv6 add auto
R(config-if)#ipv6 add 2001:db8:acad:2::/64 eui-64
R(config-if)#no shut
```

Check the newly assigned ip addresses
>[!example]- R#show ipv6 int b
>![[Untitled.png]]

Enable ipv6 routing, so this router can be identified as a default gateway
```cisco
R(config)#ipv6 unicast-routing
```

>[!example]- Enable ipv6 auto config in PC
>![[Pasted image 20230314080714.png]]

