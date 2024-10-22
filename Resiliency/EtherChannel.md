### Introduction
---
Since modern networks have multiple links between devices, it's smart to find ways to take advantage of those connections that otherwise get disabled by [[Spanning Tree Operation|Spanning Tree]].

**EtherChanneling** in the process of using multiple physical links and bundling them together into one logical link.
- If three 1 Gbps links were connected they would result in one 3 Gbps logical link

EtherChannel will load balance uplinks. 
- Packets from the same flow always use the same interface (They are not round robin)
### Types of EtherChannel Protocols
---
There are two types of EtherChannel protocols:
1. Link Aggregation Control Protocol (LACP)
2. Port Aggregation Protocol (PAgP)

 **LACP - Preferred**
- Open standard
- Switches on both sides negotiate the port channel creation and maintenance

**PAgP**
- Cisco proprietary
- Switches on both sides negotiate the port channel creation and maintenance

**Static Etherchannel** is a method of EtherChannel configuration that is done manually. No protocol automatically negotiates and all settings must be manually done and match on both sides.

**Everything must match on both sides!**

### Commands
---
>[!tip]
>In order for the channel is become bundled some criteria must be met:
>1. If any changes are made to the physical links, they must all be made to match. To avoid this confusion it is best to leave the physical interfaces alone and do all configuration on the port channel interface.

1. `int port-channel <channel-id>` is used to create an interface for the port channel. From there, the interface can be configured as you would a physical interface
2. `channel-group <channel-id> mode <auto/desirable (PAgP) | passive/active (LACP)>` is used on the physical interfaces to add them to the etherchannel. Depending on which negotiation protocol is being used, different settings are required for the mode.
	1. **For PAgP**, the interfaces connecting to each other must either be auto/desirable or both desirable. Otherwise, the etherchannel will not come up. 
	2. **For LACP**, the interfaces connecting to each other must either be active/passive or both active. Otherwise the etherchannel will not come up.
3. `channel-group <channel-id> mode on` is used to statically  on
