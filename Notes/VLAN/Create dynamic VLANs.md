---
tags: networking AI p
author: methmal66
created: [[2023-03-21]]
modified: [[2023-03-21]]
---
- Ports are able to dynamically work out their VLAN configuration
- Uses a software DB of [[MAC address]] to VLAN mapping, which must be configured

We cannot communicate with above PCs unless there are IPs assigned with them. Rather than assigning IPs and config VLANs seperately, we can config the switch to create VLANs based on the network each PC belong to.