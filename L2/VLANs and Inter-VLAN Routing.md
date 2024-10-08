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

The only interface that is allowed to communicate across VLANs are **trunk ports.**

Trunk ports are ports that allow traffic from multiple VLANs. 

