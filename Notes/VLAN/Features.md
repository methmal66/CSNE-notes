---
tags: networking AI vlan 
author: methmal66
created: [[2023-03-21]]
modified: [[2023-03-21]]
---
- Users attached to the same shared segment, share the bandwidth of that segment.
- All users can be  reassigned from their default management VLAN (VLAN 1)
- The [[Frame]] headers are encapsulated or modified to reflect a VLAN ID before the frame is sent over the link between [[Switch]]es. They are changed back to the original format before being forwarded to the destination (802.1Q Frame tagging).
