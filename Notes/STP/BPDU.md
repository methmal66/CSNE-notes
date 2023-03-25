---
aliases:
 - Bridge Protocol Data Unit
 - Bridge PDU
tags:
 - AI
 - networking
 - stp
author: methmal66
---

A type of message used in [[STP]] to communicate between network [[Switch]]es to determine the best path for network traffic.

BPDU messages are sent out periodically by the [[Root bridge]], and each switch in the network forwards the message to its neighboring switches. When a switch receives a BPDU message, it analyzes the information in the message to determine which switch in the network is the root bridge, which switch has the best path to the root bridge, and which ports on the switch should be blocked to prevent network loops.