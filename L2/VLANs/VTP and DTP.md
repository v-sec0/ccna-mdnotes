### Introduction
---
**Dynamic Trunk Protocol (DTP)** allows two switches to auto-negotiate a trunk connection. 
- The process is Cisco proprietary
- It is highly recommended to use manual configuration.

### Commands for DTP
---
1. `switchport mode dynamic auto` will form a trunk if the other switch port is set to **trunk** or **desirable.**
2. `switchport mode dynamic desirable` will form a trunk if the other switch port is set to **trunk** or ****