---
tags: networking AI practical cisco packettracer vlan
author: methmal66
created: [[2023-03-21]]
modified: [[2023-03-21]]
---
![[Pasted image 20230322001711.png|500]]
![[multilayer inter vlan.pkt]]

[[Create VLANs]] int the layer 3 switch as normal and assign interfaces on PCs.

[[Create SVI VLAN interfaces]] for the above created VLANs

Finally, we have to enable routing as this is a layer 3 switch
```cisco
S(config)#ip routing
```

>[!example]- Try to ping PCs from different vlans
>![[Pasted image 20230322001643.png]]

```embed
title: 'Inter-VLAN Routing > Objectives | Cisco Press'
image: 'https://www.ciscopress.com/display/common/images/icons/save_16.gif'
description: '<p>In this sample chapter from <em> Switching, Routing, and Wireless Essentials Companion Guide</em> (CCNAv7) for Cisco Networking Academy students, you will learn how to troubleshoot common inter-VLAN configuration issues.</p>'
url: 'https://www.ciscopress.com/articles/article.asp?p=3089357&seqNum=6'
```

