---
tags: networking hardware AI cisco 
aliases: VLAN Trunking Protocol
---
Cisco proprietary protocol to manage [[VLAN]]s accross the netwok from a central point of control. 

![[Pasted image 20230319224501.png]]

>[!important] Practical lab
>Refer this link for more practical hands-on understanding
>[[Configuring VTP]]

# Points to hightlight
- It shares VLAN information across multiple switches and maintains consistency throughout the network.
- Information will be passed only if switches are connected with fast Ethernet or higher ports.
- Ports which are connecting switches must be [[Trunk port]]s.
- VTP Domain must be the same.

# VTP modes
VTP can be configured in a switch in one of the below three modes
| Server mode                             | Client mode                                         | Transparent mode                                                 |
| --------------------------------------- | --------------------------------------------------- | ---------------------------------------------------------------- |
| Default mode, were all configs are made | All other switches recieving orders from the server | Pass the info recieved from the server into neighbouring swithes | 
| Create, Modifies and Delete VLANs       | Cannot add, modify and delete its VLAN configs      | Can Add, modify and delete VLAN configs                          |
| Synchronizes VLAN configs               | Synchronizes VLAN configs                           | Does not synchronize VLAN configs                                |
| Stores configs in NVRAM                 | Learns VLAN configs from server at the boot time    | Stores configs in NVRAM                                          |
| Sends and forwards advertisement        | Forwards advertisement                              | Forwards advertisement                                           |

>[!note]- Transparent mode
>Same as the server mode, except for the fact that it doesn’t synchronizes VLAN configurations

# VTP pruning
Optimizing the network bandwidth by restricting the flooded traffic to only those [[Trunk port]] that can reach all the active network devices. It reduces unnecessary flooded traffic, such as broadcast, multicast, and unicast packets.

![[Pasted image 20230319231233.png]]


