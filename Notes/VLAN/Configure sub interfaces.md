---
tags: networking AI cisco packettracer practical 
author: methmal66
created: [[2023-03-21]]
modified: [[2023-03-21]]
---
First, turn on the interface which we wannt to have sub interfaces. 
```cisco
R(config)#int fa0/0
R(config-if)#no shut
```

Configure sub interface for each vlan. Must provide a numer for sub interface id.
```cisco
R(config-if)#int fa0/0.10
R(config-subif)#ip add 192.168.10.1 255.255.255.0
R(config-subif)#encapsulation dot1Q 10

R(config-subif)#int fa0/0.20
R(config-subif)#ip add 192.168.20.1 255.255.255.0
R(config-subif)#encapsulation dot1Q 20
```

>[!example]- Verify sub interface configs
>![[Pasted image 20230321230913.png]]

>[!important] Encapsulation is required for sub interfaces

>[!tip] Give vlan id as the sub interface id

>[!example]- Try to ping PCs in different vlans
>![[Pasted image 20230321231113.png]]

