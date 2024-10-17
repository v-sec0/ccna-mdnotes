### Introduction
---
**Hot Standby Router Protocol** (HSRP) is a type of **First Hop Redundancy Protocol** that allows networks to be more resilient. 

It works by two routers agreeing on a Virtual IP (VIP) and virtual MAC address in order to handle traffic coming from end host. 

### Types of FHRPs
---
1. **Hot Standby Router Protocol** is Cisco proprietary and works by having one active router and one standby router to takeover if the active router goes down.
2. **Virtual Router Redundancy Protocol** is an open standard alternative to HSRP. It works in the same way HSRP works by having one active and one standby. The commands are quite similar; VRRP uses `vrrp` while HSRP uses `standby`.
3. **Gateway Load Balancing Protocol** is another Cisco proprietary protocol, however it differs from HSRP by using an active/active approach. The traffic being sent to the VIP is load balanced on the configured routers rather than being sent to one specific one. This is more complex and harder to configure than HSRP.

### Configuration
---
The configuration process for HSRP is actually quite simple. 

On the interface that is going to be used for HSRP, it must have it's own IP address for the physical interface in addition to the VIP. 

```
standby <instance> ip <ip_address>
```

The instance number is used by HSRP to identify the instance of HSRP. 

Multiple instances can be run on the same interface, but they have to be configured with different instance numbers.

In some situations, HSRP can be used to load balance:

1. The interface for both routers are configured with two instances that set each router as the active router for at least one instance. (Router A is active for instance 1, while Router B is active for instance 2).
2. Two separate interfaces are used with each router is active for it's specific interface. (Router A is active for instance 1 on G0/1, while Router B is active for instance 1 on G0/2)

### Election Process
---
By default the router with the highest priority is assigned as the active router (default priority is 100). 

If there is a tie, the router with the highest IP address on that interface is chosen. 

The default priority can be changed using:
``