---
tags: networking RS AI
---

   >[!faq]- Why v6 IPs are being used?
   >Because of the limitation of [[IPv4]]
   
# Imporvements 
- Increased address space
	Based on 128bit hierarchical addressing, which supports the expansion of new internet appliances.
- Improved packet handling
	- Simplified packet header makes packet processing efficient in the intermediate routers
		- No broadcasts
		- No checksums
	- Provides support for extensions and options for increased scalability/longevity
		- Extension headers
		- Flow labels
		- Performance and rate scalability
- Unnecessity of NAT
	- No shortage of addresses
	- Connections are end-to-end by default
- Integrated security
	- Support authentification and privacy
- Translation richness
- Improved routing tables
	- Structured hierarchy manages the routing table growth
- Serverless
	- No need for DHCP
	- Auto configuration
	- Auto reconfiguration

# Goals of new IP design
Cover the following,
- 10^15 endpoints
- 10^12 sites

# Representation
Originally, addresses are represented by 32 hexadecimal seperated by 4 hexadecimals (Hextets). 
>[!example]-
>- 2001:0DB8:0000:1111:0000:0000:0000:0200
>- fe80:0000:0000:0000:0123:4567:89ab:cdef

But these long form addresses can be reduced further using the below rules
>[!example]- Omitting leading zeros
>- 01AB -> AB
>- 09F0 -> 9F0
>- 0A00 -> A00
>- 00AB -> AB

>[!example]- Omitting all zero segments
>- 2001:0DB8:0000:1111:0000:0000:0000:0200 -> 2001:0DB8:0000:1111::0200
>- FE80:0000:0000:0000:0123:4567:89AB:CDEF -> FE80::0123:4567:89AB:CDEF
> >[!note]- Only one segment can be omitted
> >Because number of omitted zeros cannot be determined if there were multiple of them

###### Menu
- Types of addresses
	- Unicast
		- [[Loopback|Loopback]]
		- [[Unspecified|Unspecified]]
		- [[Link local|Link local]]
		- [[Unique local|Unique local]]
		- [[Global|Global]]
		- [[IPv4 compatible|IPv4 compatible]]
	 - Multicast
	 - Anycast
- IPv4 and IPv6 coexistence
	- [[Dual stack|Dual stack]]
	- [[Tunneling|Tunneling over IPv4]]
	- [[Translation|Translation]]
- Assigning addresses
	- Static config
	- [[SLAAC]]
	- DHCPv6
	- [[EUI-64 process|EUI-64 process]]
	- [[Randomly generated]]
- IPv6 header

>[!important] Lab
>Refer the below note to get a practical understanding
>[[Assign global IPv6 addresses]]


