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

>[!note]
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

>[!note]
>Typically, devices in different VLANs are configured with different L3 Network addresses. 
>
>This kept their communication separated and avoids any confusion.

