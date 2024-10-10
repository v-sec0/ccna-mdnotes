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
The port that is decided to have the best route to the root bridge is called the **root port.**
- The best port is decided based upon the **port cost**, the lower the better. 
- Port cost is considered when there are multiple links between two switches.
- The **path cost** is the accumulative sum of the port cost of a given path to the root bridge.
- **THERE CAN ONLY BE ONE!**







