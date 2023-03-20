---
tags: networking hardware AI 
aliases: Virtual LAN
---
Logical segmentation of a LAN into multiple broadcast domains reguardless of physical location or connection type. [[Packets]] are only switched between ports that are designated for the same VLAN.

# Features
- Users attached to the same shared segment, share the bandwidth of that segment.
- All users can be  reassigned from their default management VLAN (VLAN 1)
- The [[Frame]] headers are encapsulated or modified to reflect a VLAN ID before the frame is sent over the link between [[Switch]]es. They are changed back to the original format before being forwarded to the destination (802.1Q Frame tagging).

>[!faq]- Which devices share the same VLAN?
>All workstations and servers used by a particular workgroup

>[!faq]- When to use VLAN and when to buy a new switch?

>[!faq]- Why switches dont bridge any traffic between VLANs?
>Because it violates the integrity of the VLAN broadcast domain.

# Are created based on
Organization's
- Functions
- Project teams
- Applications

# Problems address by VLANs
- Network scalability
- Network security
- Network management

# Advantages
- Network admin can organize the LAN logically
- Network can be segmented without seperate hardware
- Offers more [[Bandwidth]] to users

# Configuring
There are two methods to configure VLANs
1. Static configuration
	- Network admin configure port-by-port
	- Each port is assigned with a specific VLAN
2. Dynamic configuration
	- Ports are able to dynamically work out their VLAN configuration
	- Uses a software DB of [[MAC address]] to VLAN mapping, which must be configured

>[!important] Practical lab
>Refer this page for more hands on experience [[Configuring VLANs]]

# Membership types
There are three basic VLAN memberships for determining and controlling how a packet gets assigned

## 1. Port driven
- User assigned by port association
- Requires no lookup if done in ASIC
- Easily adminstrated via GUIs
- Easily controllable accross network
- Miximizing security among VLANs
- [[Packets]] do not leak into other domain
![[Pasted image 20230318230436.png|400]]

## 2. [[MAC address]] driven
- User assigend bassed on MAC addresses
- Offers flexibility yet adds overhead
- Impacts performace, scalability and administration
- Offer similar process for higher layers
![[Pasted image 20230318231049.png]]

## 3. Network address/Protocol driven
![[Pasted image 20230318231837.png|400]]

# Best practices for creating VLANs
- The number of VLANs in a switch must be decided based on,
	- Traffic patterns
	- Type of application
	- Network management needs
	- Group commonality
- One-to-one correspondence between VLANs
- IP subnets
- Should not extend outside of the Layer 2 domain of the distribution switch


