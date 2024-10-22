### Introduction
---
In a campus environment, there are usually three layers of switches that carry information from end host to the Internet. 
1. Access layer
2. Distribution layer
3. Core layer

##### Oversubscription
For the uplinks from the Access layer to Distribution layer, it's best to follow the 20:1 rule. If there are 20 PCs connected with 1Gbps NICs, 1 Gbps uplink is required to link the access layer to the distribution layer. 
- The recommendation is 4:1 from distribution to core layer
- For some switches there are multiple dedicated ports that are for uplinks. 
However, when 2 of these ports are used to connect to another switch, [[Spanning Tree Operation|Spanning Tree]] will block one of the links and decrease the overall bandwidth of a connection. The solution to this is [[EtherChannel]].