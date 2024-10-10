### Introduction
---
**Spanning Tree Protocol** is a layer 2 protocol that prevents broadcast storms and other network issues caused by redundant links. 

It works by assigning a switch to be the **root bridge** and building the L2 routes around that root bridge.

The root bridge is decided by the switch with the lowest, and therefore, **the best bridge ID.** 

A bridge ID is what STP uses **to keep track of the switches in the network.**
- It's a combination of the bridge priority (default is 32,768), and the base MAC address. 
- The bridge ID is usually transfer to other switches inside a **Bridge Protocol Data Unit (BPDU).**

The port that is decided to have the best route to the root bridge is called the **root port.**
- The best port is decided based upon the **port cost**, the lower the better. 
- Port cost is considered when there are multiple links between two switches.
- The **path cost** is the accumulative sum of the port cost of each



