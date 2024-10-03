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

**Designated Router (DR):** In a multi-access network, the DR is elected to reduce formed adjacencies and to publicized received routing information to and from connected routers within the same broadcast domain or link. Election are won based on priority level (default is 1). If there is a tie, the router with the highest router ID wins.

**Backup Designated Router (BDR):** The BDR acts as a hot standby for the DR. It receives everything the DR receives but does not send LSAs unless the DR is down. 

**Hello protocol:** Packets that enable dynamic neighbor discovery and maintain neighbor relationships. Addressed to multicast address **224.0.0.5**.

**Neighborship database:** A database containing information about all OSPF routers for which Hello packets have been seen. Router ID, and state are maintained in this database. 

**Topological database:** A database that contains information about all Link State Advertisements received and places the information into Dijkstra's algorithm to compute the shortest path to every network.

**Link State Advertisement:** A OSPF data packet containing link-state and routing information that shared among OSPF routers. 

**OSPF Area:** A OSPF area is a grouping of contiguous networks and routers. Routers within an area share an Area ID on the interface configured for that area. A router can be apart of multiple areas so each interface will have the Area ID of the area it's configured to connect to.

**Broadcast (multi-access):** A broadcast/multi-access network allows multiple devices to connect to or access the same network, enabling a broadcast ability so a single packet can be delivered to multiple endpoints. 

**Nonbroadcast multi-access:** A nonbroadcast multi-access networks like Frame Relay, X.25, and Asynchronous Transfer Mode (ATM) allows for multi-access without the broadcast ability.










