---
tags: networking AI 
alias: Stateless Address Autoconfiguration (SLAAC)
author: methmal66
created: [[2023-03-21]]
modified: [[2023-03-21]]
---
- No seperate DHCPv6 [[Router]] is needed
- Obtain prefix, prefix length and default gateway from an IPv6 router
- Rely on ICMPv6  Router Advertisement (RA) messages

>[!faq]- How RA messages are being send
> Routers send ICMPv6 RA messages using the link-local address as the source IPv6 address

