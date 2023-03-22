---
tags: networking AI 
author: methmal66
created: [[2023-03-21]]
modified: [[2023-03-21]]
---
- Servers the purpose of private addresses as in [[IPv4]] with added features
- Allocated address block is `fc00::/7`
- Consist of 3 parts in order
	1. Prefix (8bits) - `fc` or `fd`
	2. Global ID (40bits)
	3. Subnet ID (16bits)
	4. Interface ID (64bits)
![[Pasted image 20230312191914.png|500]]

>[!note]- Site Local addresses are deprecated
>- Corresponding to private addresses in [[IPv4]]
>- Allocated address block is `FEC0::/16`

