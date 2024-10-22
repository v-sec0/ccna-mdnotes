### Introduction
---
Since modern networks have multiple links between devices, it's smart to find ways to take advantage of those connections that otherwise get disabled by [[Spanning Tree Operation|Spanning Tree]].

**EtherChanneling** in the process of using multiple physical links and bundling them together into one logical link.
- If three 1 Gbps links were connected they would result in one 3 Gbps logical link

EtherChannel will load balance uplinks. 
- Packets from the same flow always use the same interface (They are not round robin)
### Terminology
---
EtherChannel is also known as:
1. Port Channel
2. LAG Link Aggregation
3. A link bundle

NIC teaming is also know as:
1. Bonding
2. NIC Aggregation 

### Commands
---
>[!tip]
>In order for the channel is become bundled some criteria must be met:
>1. If link is going to be a trunk, make sure the native VLAN, Allowed VLANs, and the trunk mode are the same for not just the individual physical interfaces, but the logical one as well. Otherwise, some links may refuse to be bundled.

1. `int port-channel <channel-id>` is used to create an interface for the port channel. From there, the interface can be configured as you would a physical interface
2. `channel-group <channel-id> mode <auto/desirable (PAgP) | passive/active (LACP)>` is used on the physical interfaces to add them to the etherchannel. Depending on which negotiation protocol is being used, different settings are required for the mode.
	1. **For PAgP**, the interfaces connecting to each other must either be auto/desirable or both desirable. Otherwise, the etherchannel will not come up. 
	2. **For LACP**, the interfaces connecting to each other must either be active/passive or both active. Otherwise the etherchannel will not come up.


d
