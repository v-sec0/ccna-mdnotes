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

**Link**: A network or router interface assigned to any given network. When an interface is added to the OSPF process it's considered to be a link. 

**Router ID:** The name of a router in the OSPF process. This is usually derived from the highest loopback IP on the router, but if that's not available, the highest interface IP address is used. 

**Neighbor**






