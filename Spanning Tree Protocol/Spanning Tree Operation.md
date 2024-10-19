
### Things to Remember
---

| **Speed**    | Short Cost | Long Cost |
| ------------ | ---------- | --------- |
| **10 Mbps**  | 100        | 2,000,000 |
| **100 Mbps** | 19         | 200,000   |
| **1 Gbps**   | 4          | 20,000    |
| **10 Gbps**  | 2          | 2,000     |
| 20 Gbps      | 1          | 1,000     |
| 100 Gbps     | 1          | 200       |
| 1 Tbps       | 1          | 20        |
| 10 Tbps      | 1          | 2         |
The default bridge priority level on all devices running IEEE STP is **32,768.**

To see which mode the switch is in use `show spanning-tree pathcost method`.

The default cost is short mode, to change it use `spanning-tree pathcost method <long|short>`.

### Selecting the Root Bridge and Root Port
---
The root bridge is selected by the switch with the lowest (best) bridge ID.
- The bridge ID is calculated by combination of the priority level and the MAC address. 
- The priority level being represented by **2 bytes (16-bit)** and the MAC address, **6 bytes (48-bit).**
- Read the MAC address left to right to figure out which is the lowest. Only stop once you find a lower value.
Best practice is to artificially select a root bridge by lowering the bridge priority.
- This ensures the best paths are selected.

To calculate the link, the root bridge sends a BDPU with a cost of 0. When a switch receives it, it adds the cost of the interface it received the packet on to the BDPU. 
- If a switch received a BDPU on a Gigabit interface, it will add a cost of 4 (short) or 20,000 (long) to the BDPU. 


### Types of Spanning Tree Protocols
---
1. **IEEE 802.1d (CST)** is the original standard for STP and bridging. It's really slow, but is good for very little bridge resources. This is commonly referred to as **Common Spanning Tree.**
2. **Per-VLAN Spanning Tree (PSVT+)** is a Cisco proprietary standard for STP and **is the default**. It creates separate 802.1d instances for each VLAN. While it does create more efficiency, it does consume more resources that CST
3. **IEEE 802.1w (RSTP)** is a standard that enhanced the BDPUs exchange process, paving the way for a faster convergence time. While less resource intensive as PSVT+, it still uses more resources that CST. This is commonly referred to as **Rapid Spanning Tree Protocol.**
4. **IEEE 802.1s (MSTP)** was a Cisco proprietary standard before becoming an IEEE standard. It works the same as PVST but instead of having an CST instance for each VLAN, it allows VLANs with similar traffic patterns to use one CST instance. This is commonly referred to as **Multiple Spanning Tree.**
5. **RPVST+** is Cisco's version of RSTP that also uses PVST+ to create separate RSTP instances for each VLAN. It's the most optimal for speed and traffic flow, but is the most resource intensive.

### Commands to Know
---
1. `show cdp neighbors` shows information about connected devices and can be used to find the root bridge.
2. `show spanning-tree` shows information about the STP on the switch
3. `spanning-tree vlan <vlan_id> priority <0-61440>`sets the priority level of a switch for a particular VLAN. 
4. `spanning-tree vlan <vlan> root <primary/secondary>` sets the switch as either the primary or secondary root bridge.
5. `show spanning-tree summary` gives a comprehensive look at the status of STP for each VLAN on a switch
6. `spanning-tree mode <mst|pvst|rapid-pvst>` changes the mode of STP

### Common STP Failures
---
If a port that should be in blocking state changes to a forwarding state, many different issues can occur on a network. If there is broadcast traffic, all ports on a switch may be flooded with traffic causing: 
1. Slow speeds as the CPU is being overwhelmed with endless processes
2. Unusable MAC table as the same source address is coming from different ports
3. Complete network failure; switches may stop working due to high CPU usage. 
The best remedy for a troubled network is to remove all redundant links and connect them one at a time. This allows you to figure out which link is causing the issue. 

Another issue may arise from a port that's supposed to be forwarding changing to a blocking state. In this case, the segment that is blocked with lose connection, but traffic may persist for other areas of the network. 