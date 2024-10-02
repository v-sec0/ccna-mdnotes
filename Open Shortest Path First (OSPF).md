**Compared to RIPv2:**

| Characteristic                | **OSPF**                | RIPv2                  |
| ----------------------------- | ----------------------- | ---------------------- |
| Classless support             | **Yes**                 | Yes                    |
| VLSM/CIDR support             | **Yes**                 | Yes                    |
| Auto-summarization            | **No**                  | Yes                    |
| Manual summarization          | **Yes**                 | Yes                    |
| Route propagation             | **Multicast on change** | Multicast periodically |
| Path metric                   | **Bandwidth**           | Hops                   |
| Hop count limit               | **None**                | 15                     |
| Convergence                   | **Fast**                | Slow                   |
| Hierarchal network requirment | **Yes (Areas)**         | No (Flat only)         |
| Updates                       | **Event triggered**     | Periodic               |
| Route computation             | **Dijkstra**            | Bellman-Ford           |

A hierarchal design allows larger internetworks to be segmented into smaller internetworks. 

**This brings the following advantages:**
- Decreased routing overhead
- Decreased convergence time
- Isolates network instability

**Area 0** is the backbone of OSPF and every OSPF network must have an area 0. The routers that connect other networks to area 0 inside an autonomous system are referred to as:
**Area Border Routers.**
- *Autonomous system* refers to a collection of networks that share common administration and routing strategy.

Multiple autonomous systems can be connected together. The router that connects these ASs together is called an **Autonomous System Boundary Router (ASBR).**

## OSPF Terminology

**Link:** A network or router interface assigned to any given network. When an interface is added to the OSPF process it's considered to be a link. 

**Router ID:** The name of a router in the OSPF process. This is usually derived from the highest loopback IP on the router, but if that's not available, the highest interface IP address is used. 

**Neighbor:** Two or more routers that have an interface on a common network, such as two routers connected on a P2P serial link. In order for two routers to become neighbors they need to have the same settings for the following: 
1. Area ID
2. Stub Area Flag
3. Authentication password
4. Hello and Dead intervals

**Adjacency:** A relationship between two OSPF routers that permits the exchange of updates. OSPF is picky about sharing updates -- only shares information with neighbors with established adjacency. In multi-access connections, routers form adjacencies with the DR and BDR. 

**Designated Router (DR):** In a multi-access network, the DR is elected to reduced formed adjacencies and to publicized received routing information to and from connected routers within the same broadcast domain








