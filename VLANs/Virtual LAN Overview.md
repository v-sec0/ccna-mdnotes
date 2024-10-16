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

End hosts **are not** VLAN aware.

`switchport mode access` is used to enabled access mode on an interface.
- `switchport access vlan <vlan>` is used to specify a VLAN for an interface.
### Trunk Ports 
---
Trunk ports are switch ports that are configured to support traffic from all VLANs or a select few of approved VLANs. 

Trunk ports allow for VLAN traffic to span across multiple switches in the network. 

>[!tip]
>Typically, devices in different VLANs are configured with different L3 Network addresses. 
>
>This kept their communication separated and avoids any confusion.

In some scenarios, such as virtualization, you may need to trunk VLANS down to the host. 

`switchport mode trunk` is used to set an interface to trunk.

Native VLAN is required to be set for all untagged traffic travelling over a trunk port. 
- In order for a trunk port to work, **both sides need to have the same native VLAN.**
>[!note]
>Typically, this would be set to the default VLAN 1, but there are known security-issues with using this VLAN so **it's recommended to be set to an unused VLAN.**

- `switchport trunk native vlan <vlan>` is used to set the native VLAN.

Trunk ports allow the ability to limit allowed VLANs over the port. **This increases security and increases performance by saving bandwidth.** 
- `switchport trunk allow vlans <vlan(s)>` is used to set allowed VLANs
### 802.1q & ISL
---
802.1q or dot1Q is a standard developed by the IEEE for frame tagging. 

It allows for the insertion of VLAN information into frames and packets that travel across different devices. 

With 802.1Q, a frame sent from a switch to a router will maintain it's VLAN information and allow the destination device to make informed decisions based on upon it's contents. 

Cisco had it's own proprietary standard for frame tagging called Inter-Switch Link (ISL). 

>[!tip]
>Cisco has phased out support for ISL in favor of 802.1Q due to it's open nature

ISL works **by encapsulating frames with control information**, while dot1Q **inserts a field into a frame.**

### Inter-VLAN Routing
---
In order for VLANs to communicate with each other 1 of 3 scenarios are needed:
1. A router has several links connected to the switch (or switches) with dedicated links for each VLAN (and subnet).
	1. With this option, the switch can set each link to **access mode.**
2. A router has one physical link with several sub-interfaces for each VLAN (and subnet).
	1. With this option, the switch must set the interface connected to the router as a **trunk.**
	2.  `encapsulation dot1Q <vlan>` needs to be set for all sub-interfaces.
	3.  `ip routing` also needs to be enabled.
3. A L3 Switch is configured with a **Switched Virtual Interface**
	1. `int vlan <vlan-id>` creates an interface for the VLAN and allows the configuration of a SVI. You would then configure an IP address for the interface. 
	2. `no switchport` is needed on any physical interface on the L3 Switch that you would like to add an IP address to. 
		1. 1. Once done, you can use `ip address` to add an IP
	3. At the global level, `ip routing` needs to be enabled for the switch to be able to route traffic. 
	4. Additionally, a default route needs to be configured for the switch to forward traffic outside of the internetwork to the internet.
		