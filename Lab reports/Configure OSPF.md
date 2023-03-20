---
tags: networking practical packettracer cisco AI 
---
![[Pasted image 20230315213405.png]]
![[ospf.pkt]]

```embed
title: '8.2.1 Packet Tracer - Configure OSPFv2 in a Single Area (Answers)'
image: 'https://itexamanswers.net/wp-content/uploads/2021/02/8.2.1-2021-07-13_154023.jpg'
description: '8.2.1 Packet Tracer - Configure OSPFv2 in a Single Area Exam Answers - CCNP ENCOR v8 Instructor version completed pdf file free download 2020-2021'
url: 'https://itexamanswers.net/8-2-1-packet-tracer-configure-ospfv2-in-a-single-area-answers.html'
```

# Setup interfaces
| Device | Interface | Address       | Mask            | Default GW |
| ------ | --------- | ------------- | --------------- | ---------- |
| R1(PT)     | Gi0/0     | 172.16.1.1    | 255.255.255.0   | N/A        |
| ""     | Se1/0     | 172.16.3.1    | 255.255.255.252 | N/A        |
| "      | Se2/0     | 192.168.10.5  | 255.255.255.252 | N/A        |
| R2(PT)     | Gi0/0     | 172.16.2.1    | 255.255.255.0   | N/A        |
| "      | Se1/0     | 172.16.3.2    | 255.255.255.252 | N/A        |
| "      | Se2/0     | 192.168.10.9  | 255.255.255.252 | N/A        |
| R3(PT)     | Gi0/0     | 192.168.1.1   | 255.255.255.0   | N/A        |
| "      | Se1/0     | 192.168.10.6  | 255.255.255.252 | N/A        |
| "      | Se2/0     | 192.168.10.10 | 255.255.255.252 | N/A        |
| PC1    | NIC       | 172.16.1.2    | 255.255.255.0   | 172.16.1.1 |
| PC2    | NIC       | 172.16.2.2    | 255.255.255.0   | 172.16.2.1 |       
| PC3    | NIC       | 192.168.1.2   | 255.255.255.0   | 192.168.1.1| 


# Setup OSPF
```cisco
R1(config)#router ospf 10
R1(config-router)#router-id 1.1.1.1
R1(config-router)#network 172.16.1.0 0.0.0.255 area 0
R1(config-router)#network 172.16.3.0 0.0.0.3 area 0
R1(config-router)#network 192.168.10.4 0.0.0.3 area 0
R1(config-router)#passive-interface gi0/0
```

```cisco
R2(config)#router ospf 10
R2(config-router)#router-id 2.2.2.2
R2(config-router)#network 172.16.2.0 0.0.0.255 area 0
R2(config-router)#network 172.16.3.0 0.0.0.3 area 0
R2(config-router)#network 192.168.10.8 0.0.0.3 area 0
R2(config-router)#passive-interface gi0/0
```

```cisco
R3(config)#router ospf 10
R3(config-router)#router-id 3.3.3.3
R3(config-router)#network 192.168.1.0 0.0.0.255 area 0
R3(config-router)#network 192.168.10.8 0.0.0.3 area 0
R3(config-router)#network 192.168.10.4 255.255.255.252 area 0
R3(config-router)#passive-interface gi0/0
```

>[!faq]- Why we have set a router id?
>The router ID is an identification number for uniquely identifying each OSPF router in the network. You need to specify so that it does not overlap among multiple routers.

>[!faq]- Why we have set a passive interface?
>Disables routing announcements on an interface. OSPF routing updates will not be shared over that interface. But it will still listen to OSPF routes. We can save the router bandwith by doing this.

>[!faq]- Why we have set an area?
>An OSPF network can be divided into sub-domains called areas. An area is a logical collection of OSPF networks, routers, and links that have the same area identification. A router within an area must maintain a topological database for the area to which it belongs. The router does not have detailed information about network topology outside of its area, which thereby reduces the size of its database. We have used a single area. That is why every network is connected to `area 0`.

# Verify OSPF routing is operational
Non directly connected networks should be displayed in the routing table as ospf routes
![[Pasted image 20230315210840.png]]

![[Pasted image 20230315211234.png]]

![[Pasted image 20230315211426.png]]

# Verify the PC connectivity
PC1
![[Pasted image 20230315212902.png]]

PC2
![[Pasted image 20230315212539.png]]

PC3
![[Pasted image 20230315213207.png]]