
### Things to Remember

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

