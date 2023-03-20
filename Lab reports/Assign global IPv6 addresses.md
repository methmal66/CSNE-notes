---
tags: AI practical networking packettracer cisco 
---

# Assign static addresses
![[Pasted image 20230314082255.png|500]]

![[CSNE notes/Attachments/static ipv6.pkt]]
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

Lets check if the configs are ok. It will display the following output
![[Pasted image 20230313062501.png|600]]

Set static ipv6 address in PC
![[Pasted image 20230314082125.png]]
>[!note]- Link local address
>Following output has two types of addresses. Second is the one we configured, global address. First is the link local address, which is automatically assigned by default.

# Assign auto (SLAAC) addresses
>[!note]- SLAAC
>Stateless Address Autoconfiguration

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
![[Untitled.png]]

Enable ipv6 routing, so this router can be identified as a default gateway
```cisco
R(config)#ipv6 unicast-routing
```

Enable ipv6 auto config in PC
![[Pasted image 20230314080714.png]]
# Recive addresses using DHCPv6
