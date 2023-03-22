---
tags: networking AI RS 
author: methmal66
created: [[2023-03-21]]
modified: [[2023-03-21]]
---
![[Pasted image 20230314090351.png|500]]
NAT-PT (Network Address Translation – Protocol Translation) enabled device can translate IPv4 packets into IPv6 packets and vice versa. A host with IPv4 address sends a request to an IPv6 enabled server on Internet that does not understand IPv4 address. In this scenario, the NAT-PT device can help them communicate. When the IPv4 host sends a request packet to the IPv6 server, the NAT-PT device/router strips down the IPv4 packet, removes IPv4 header, and adds IPv6 header and passes it through the Internet. When a response from the IPv6 server comes for the IPv4 host, the router does vice versa.