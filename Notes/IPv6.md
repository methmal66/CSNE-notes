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

# IPv6 representation
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

# Types of addresses
## Unicast
![[Pasted image 20230312175611.png|400]]

### Loopback
- The address used to send packets back to their host. 
- Only address is `::1/128`, which is corressponding 127.0.0.0/8 range in [[IPv4]]
- Cannot be assigned to a physical address

### Unspecified 
- Address is used as the source address when a unique address has not yet been configured. 
- Also used as the default route in routing
- `::/128` is corresponding to 0.0.0.0/8 in [[IPv4]]
- Cannot be assingned to a physical interface
- Only used as a source address
>[!faq]- Why there are sepertate linklocal/global/site local addresses?

>[!note]- The only one unspecified address is `::` = `0:0:0:0:0:0:0:0`

### Link Local
- The addresses used to communicate on local network segments. 
- Confined to a single link
- Routers do not forward packet with these addresses. 
- Has `FE80::/10` address block, which is corresponing to `169:254:0.0/16` in [[IPv4]]
- Every IPv6-enabled network interfaces required to have
![[Pasted image 20230312194207.png]]

### Unique local
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

### Global addresses
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

### [[IPv4]] Compatible
- Assigned to devices that handle both [[IPv4]] and IPv6
- Consist of two parts, which are in order
	1. 96bit zeros
	2. 32bit [[IPv4]] address
![[Pasted image 20230312193433.png]]


## Multicast
![[Pasted image 20230312205557.png|400]]

## Anycast
![[Pasted image 20230312205704.png|400]]

>[!note] Anycast is a one-to-nearest association

>[!note] There are no broadcast addresses in IPv6

# IPv6 header


# IP v4 an v6 coexistence
## Dual stack
Both [[IPv4]] and IPv6 address assign to each interface. Once all the devices have implemented IPv6, the IPv4 part of the network will be depreciated. This method is common for businesses looking to slowly convert their existing devices from IPv4 to IPv6.

## Tunneling over IPv4
![[Pasted image 20230314090302.png|500]]
Encapsulate IPv6 packets into IPv4 packets and send through a [[IPv4]] network. There are two methods for tunelling
1. Mannual tunnels
2. GRE(Generic Routing Encapsulation) tunnels

## Translation 
![[Pasted image 20230314090351.png|500]]
NAT-PT (Network Address Translation – Protocol Translation) enabled device can translate IPv4 packets into IPv6 packets and vice versa. A host with IPv4 address sends a request to an IPv6 enabled server on Internet that does not understand IPv4 address. In this scenario, the NAT-PT device can help them communicate. When the IPv4 host sends a request packet to the IPv6 server, the NAT-PT device/router strips down the IPv4 packet, removes IPv4 header, and adds IPv6 header and passes it through the Internet. When a response from the IPv6 server comes for the IPv4 host, the router does vice versa.

# Assigning IPv6 addresses
>[!important] Lab
>Refer the below note to get a practical understanding
>[[Assign global IPv6 addresses]]

## Assigning global addresses
### Static configuration
Simillar to how [[IPv4]] addresses were assigned

### Stateless Address Autoconfiguration (SLAAC) is used
- No seperate DHCPv6 [[Router]] is needed
- Obtain prefix, prefix length and default gateway from an IPv6 router
- Rely on ICMPv6  Router Advertisement (RA) messages
>[!faq]- How RA messages are being send
> Routers send ICMPv6 RA messages using the link-local address as the source IPv6 address

### DHCPv6

## Assigning link local addresses
### EUI-64 process
1. Client's 48-bit Ethernet MAC address is devided into two equal parts
2. `FFFE` is inserted in between them
3. Reverse the 7th bit
![[Pasted image 20230312204624.png]]

>[!note] Default link local addresses of routers are generated from this method

>[!note]- This method is deprecated in PC's due to Randomly generated method

### Randomly generated
- Generated ID is depend upon the [[Operating System]]
- Beginning with Windows Vista, Windows uses a randomly generated Interface ID



