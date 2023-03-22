---
tags: AI practical networking packettracer cisco ipv6
author: methmal66
created: [[2023-03-22]]
modified: [[2023-03-22]]
---
![[Pasted image 20230314082255.png|500]]
![[static ipv6.pkt]]

> [!note]- Selecting routers
> Not all routers including PT-router support IPv6. You must select a router which supports. Othervise it will show invalid command error

```
R(config)#int gi0/0/1
R(config-if)#ipv6 add 2001:db8:acad:1::1/64
R(config-if)#no shutdown

R(config-if)#int gi0/0/0
R(config-if)#ipv6 add 2001:db8:acad:2::1/64
R(config-if)#no shutdown

R(config-if)#int se0/1/0
R(config-if)#ipv6 add 2001:db8:acad:3::1/64
R(config-if)#clock rate 56000
R(config-if)#no shut
```

Verify the interface configs
>[!example]- R#show ipv6 int b
>![[Pasted image 20230313062501.png|600]]

>[!note]- Link local address
>Following output has two types of addresses. Second is the one we configured, static address. First is the link local address, which is automatically assigned by default.

>[!example]- Set static address in PC
>![[Pasted image 20230314082125.png]]

