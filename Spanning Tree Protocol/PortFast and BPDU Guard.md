### Introduction
---
>[!warning]
>**If BDPU Guard is enabled**, do not plug in a switch or any other device that could cause a loop in the network. The interface will shutdown!

**PortFast and BDPU Guard** are methods that can help alleviate the risk of STP failures. 

**PortFast** is configured on interfaces connected to devices that **you are sure won't create loops if STP is disabled.** With PortFast, the interface won't spend the usual 50 seconds or more **coming up into forwarding mode while STP is converging.**
- PortFast allows the transition between blocking and forwarding to be instant. This prevents host from potentially being unable to receive DHCP information due to the slow convergence time of STP.
- `spanning-tree portfast` is used to configure an interface to use PortFast.

**BDPU Guard** is a secondary configuration for **interfaces with PortFast enabled.** Essentially, if an interface with PortFast enabled receives a BDPU, the interface is **placed into an error shutdown state preventing (guarding) against the attachment of a switch or hub that could create a loop.** 
- `spanning-tree portfast bdpuguard default` can be used globally to make it the default for interfaces with PortFast enabled. 
- `spanning-tree bdpuguard enabled` can be used to configure BDPU Guard for a specific interface.

>[!tip]
>Usually BDPU Guard is only configured on Access layer switches, where users and endpoints are connected.

