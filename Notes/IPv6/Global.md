---
tags: networking AI 
author: methmal66
created: [[2023-03-21]]
modified: [[2023-03-21]]
---
- Corresponding to public addresses in [[IPv4]]. 
- Globally unique, internet routable addresses
- Consists of 3 parts in order
	1. Global routing prefix (48bits)
	2. Subnet ID (16bits)
	3. Interface ID (64bits)
- Global routing prefix or network portion is provided to customers by ISP
- RIR’s assign a /48 global routing prefix to customers
- Can be configured statically or dinamically
- `2001::/16` is the currently allocated global address block by IANA, they all start with `2001`
>[!example]- 
>- 2001:4860:4860::8888
>- 2001:0DB8:0000:1111::0200
>- 2001:db8:cafe:1:4bff:fe15:246f

![[Pasted image 20230312194545.png]]

![[Pasted image 20230312195550.png]]