### Introduction
---
**Dynamic Trunk Protocol (DTP)** allows two switches to auto-negotiate a trunk connection. 
- The process is Cisco proprietary
- It is highly recommended to use manual configuration.
**VLAN Trunking Protocol (VTP)** allows you to add, edit, or delete VLANs on switches configured as VTP servers and have other switches configured as VTP clients synchronize their VLAN database with them.
- Still have to perform VLAN configuration on a port level.

>[!warning]
>VTP can delete VLANs if a switch is introduced with a higher VLAN database revision number

### Commands for DTP
---
1. `switchport mode dynamic auto` will form a trunk if the other switch port is set to **trunk** or **desirable.** (default on newer switches)
2. `switchport mode dynamic desirable` will form a trunk if the other switch port is set to **trunk** or **auto.**
3. `switchport nonnegotiate` will disable DTP.

### Commands for VTP
---
1. `vtp mode <client|server|transparent>` will set the switch to either a client, a server, or a pass-through.
2. `vtp version <1|2>` sets the VTP version
3. `vtp domain <domain-name>` sets the VTP domain name.