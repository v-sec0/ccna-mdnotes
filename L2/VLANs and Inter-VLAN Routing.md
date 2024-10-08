### Introduction
---

Virtual LANs (VLANs) allow for the segmentation of layer 2 networks. 

Some of the benefits of VLANs are:
1. Broadcast control
2. Segmentation
3. Security

To create a VLAN on a Cisco Switch:
```
SW1(config)#vlan <vlan_id>
```

To see all created VLANs:
```
SW1(config)#sh vlan
```

To name VLANS:
```
SW1(config-vlan)#name <name>
```

By default, interfaces configured to a particular VLAN are only allowed to received and send traffic to interfaces of the same VLAN. 
- Additionally, a port configured with a VLAN has to be an **access port.**

The only interface that is allowed to communicate across VLANs are **trunk ports.**

Trunk ports are ports that allow traffic from multiple VLANs. 

A port **cannot** be both an access port and a trunk port.


### Trunking
---

Trunking is the process in which a port is configured as a trunk and able to carry traffic from multiple VLANs.

Trunking allows for device from different VLANs to communicate with one another. 

>[!note]
>Typically, devices in different VLANs are configured with different L3 Network addresses. 
>This kept 