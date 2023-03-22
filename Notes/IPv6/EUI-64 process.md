---
tags: networking AI ipv6
author: methmal66
created: [[2023-03-21]]
modified: [[2023-03-21]]
---
1. Client's 48-bit Ethernet MAC address is devided into two equal parts
2. `FFFE` is inserted in between them
3. Reverse the 7th bit

![[Pasted image 20230312204624.png|500]]

>[!note] Default link local addresses of routers are generated from this method

>[!note]- This method is deprecated in PC's due to Randomly generated method
