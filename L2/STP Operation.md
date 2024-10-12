
### Things to Remember
---

| **Speed**    | Priority |
| ------------ | -------- |
| **10 Mbps**  | 100      |
| **100 Mbps** | 19       |
| **1 Gbps**   | 4        |
| **10 Gbps**  | 2        |
|              |          |
The default bridge priority level on all devices running IEEE STP is **32,768.**

### Selecting the Root Bridge and Root Port
---
The root bridge is selected by the switch with the lowest (best) bridge ID.
- The bridge ID is calculated by combination of the priority level and the MAC address. 
- The priority level being represented by **2 bytes (16-bit)** and the MAC address, **6 bytes (48-bit).**
- Read the MAC address left to right to figure out which is the lowest. Only stop once you find a lower value.
Best practice is to artificially select a root bridge by lowering the bridge priority.
- This ensures the best paths are selected.


### Types of Spanning Tree Protocols
---
1. **IEEE 802.1d (CST)** is the original standard for STP and bridging. It's really slow, but is good for very little bridge resources. This is commonly referred to as **Common Spanning Tree.**
2. **Per-VLAN Spanning Tree (PSVT+)** is a Cisco proprietary standard for STP and is the default. It creates separate 802.1d instances for each VLAN. While it does create more efficiency, it does consume more resources that CST
3. **802.1s (MST)** was a Cisco proprietary standard before becoming an IEEE standard. It works the same as PVST but instead of having an 802.1d instance for each VLAN, it allows VLAN