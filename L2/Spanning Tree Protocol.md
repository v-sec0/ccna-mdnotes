### Introduction
---
**Spanning Tree Protocol** is a layer 2 protocol that prevents broadcast storms and other network issues caused by redundant links. 

It works by assigning a switch to be the **root bridge** and building the L2 routes around that root bridge.

### Bridges and Switches
---
The root bridge is decided by the switch with the lowest, and therefore, **the best bridge ID.** 

A bridge ID is what STP uses **to keep track of the switches in the network.**
- It's a combination of the bridge priority (default is 32,768), and the base MAC address. 
- The bridge ID is usually transfer to neighboring switches inside a **Bridge Protocol Data Unit (BPDU).**
- A BDPU can contain multiple Bridge ID information for multiple switches

``` mermaid
flowchart LR
	A[Switch A] --BDPU (A)--> B[Switch B] --BDPU (A,B)--> C[Switch C]
```


### Ports
---
##### Types of Ports

The port that is decided to have the best route to the root bridge is called the **root port.**
- The best port is decided based upon the **port cost**, the lower the better. 
- Port cost is considered when there are multiple links between two switches.
- The **path cost** is the accumulative sum of the port cost of a given path to the root bridge.
- **THERE CAN ONLY BE ONE!**

A **designated port** are ports that carry traffic away from the root bridge to various segments.
- On each segment there is **at least one** designated port that brings traffic from the root bridge. 
- A switch will have one root port to the root bridge, but have a designated port(s) if it connects to other segments to forward traffic to them from the root bridge.

A **non-designated port** are ports that are put into blocking or discard mode after the root port and designated port(s) are decided.

A **blocking port** is a port that listens for BDPUs but won't forward frames.

A **forwarding port** is a port that forwards frames; will be either the root port or designated port.

An **alternative port** is a port that's on a switch that connect to a LAN segment with two or more switches where one of the other switches is assigned as a designated route and connects to the other.
- A similar concept is a **blocking port** which is a backup for the alternative port.

##### Port States

A **blocked port** is a port that is configured to receive BDPUs but not forward any traffic. 
- Helps prevent looped paths

A **disabled port** is a port that is essentially non-operational and does not participate in STP

A **forwarding port** is a port sends and received all data on the bridged port

A **listening port** is a port that listens for BDPUs to make sure no loops occur on the network before passing data frames.
- A port in the listening state prepares to forward data frames without populating the MAC address table. 

A **learning port** is a port that listens to BDPUs and learns all the path in a switched network



