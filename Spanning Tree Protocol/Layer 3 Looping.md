### Introduction
---
To better understand why STP is needed, let's evaluate what Layer 3 uses to prevent loops. 

In a scenario in which there is potential for a L3 route loop. Packets have a TTL (Time-To-Live) that decreases as the packet passes through a router. 

Therefore, if a packet where to find itself in a loop, with a set TTL of 5 the packet would eventually get dropped after routing through 5 routers. 