---
tags: networking packettracer practical cisco AI
author: methmal66
created: [[2023-03-20]]
modified: [[2023-03-21]]
---

![[Pasted image 20230320094656.png]]
![[vlan trunking.pkt]]

Configure interfaces. Then create VLANs as it is explained in [[Create VLANs]]. Finally, configure the trunk port
```cisco
S1(config)#int gi0/1
S1(config-if)#switchport mode trunk
S1(config-if)#switchport trunk allowed vlan 10,20
```

>[!tip]
>Use a port with higher bandwidth for the trunk port. That is why a Gigabit ethernet is used for the trunk port, while all other access ports are configured with Fast ethernet.

Optionally, you can config a native VLAN(VLAN whose traffic does not go trough the trunk port) as well. Default value is 1 as shown below
```cisco
S1(config-if)#switchport trunk native vlan 1
```

>[!note]- Encapsulation
>Most newer devices support `dot1q` encapsulation only. Therefor, encapsulation standards cannot be configured in those device. But older devices allow to use other standards as well. It can be configured by,
>```
>S1(config-if)#switchport trunk encapsulation dot1q
>```

Check switchport configs
>[!example]- S2#show int fa0/1 switchport
>![[Pasted image 20230320092856.png]]

>[!example]- S2#show int gi0/1 switchport
>![[Pasted image 20230320093011.png]]

Try to ping devices in the same vlan 
![[Pasted image 20230320100806.png|400]]