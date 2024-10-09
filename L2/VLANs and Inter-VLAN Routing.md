### Introduction
---
Virtual LANs (VLANs) allow for the segmentation of layer 2 networks. 

Some of the benefits of VLANs are:
1. Broadcast control
2. Segmentation
3. Security

**To create a VLAN on a Cisco Switch:**
```
SW1(config)#vlan <vlan_id>
```

**To see all created VLANs:**
```
SW1(config)#sh vlan
```

**To name VLANS:**
```
SW1(config-vlan)#name <name>
```

By default, a switch port configured to a particular VLAN are only allowed to received and send traffic to interfaces that are in their VLAN.

>[!tip]
>A switch port can only belong to one VLAN, if it's an access port; or all VLANs if it's a trunk port.

The only interface that is allowed to communicate across VLANs are **trunk ports.**

Trunk ports are ports that allow traffic from multiple VLANs. 

A port **cannot** be both an access port and a trunk port.


### Access Ports
---
Traffic received and sent by an access port is assumed to belong to the configured VLAN on that port.

VLAN information on the frame is removed before being sent to an device on an access port. 

Devices on an access port cannot communicate with devices outside of their VLAN unless the traffic is routed. 


### Trunk Ports 
---
Trunk ports are switch ports that are configured to support traffic from all VLANs or a select few of approved VLANs. 

Trunk ports allow for VLAN traffic to span across multiple switches in the network. 

>[!tip]
>Typically, devices in different VLANs are configured with different L3 Network addresses. 
>
>This kept their communication separated and avoids any confusion.


### 802.1q & ISL
---
802.1q or dot1Q is a standard developed by the IEEE for frame tagging. 

It allows for the insertion of VLAN information into frames and packets that travel across different devices. 

With 802.1Q a frame sent from a switch to a router will maintain it's VLAN information and allow the destination device to make informed decisions based on upon it's contents. 

Cisco has it's own proprietary standard for frame tagging called Inter-Switch Link (ISL). 

>[!tip]
>Cisco is phasing out support for ISL in favor of 802.1Q due to it's open nature

ISL works **by encapsulating frames with control information**, while dot1Q **inserts a field into a frame.**

### Inter-VLAN Routing
---
In order for VLANs to communicate with each other 1 of 3 scenarios are needed:
1. A router has several links connected to the switch (or switches) with dedicated links for each VLAN (and subnet).
	- With this option, the switch can set each link to **access mode.**
	- `Router# `
1. A router has one physical link with several sub-interfaces for each VLAN (and subnet).
	- With this option, the switch must set the interface connected to the router as a **trunk.**
2. A L3 Switch is configured with a Switched Virtual Interface
