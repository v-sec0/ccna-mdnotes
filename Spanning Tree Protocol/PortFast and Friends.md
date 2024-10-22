### Introduction
---
>[!warning]
>**If BDPU Guard is enabled**, do not plug in a switch or any other device that could cause a loop in the network. The interface will shutdown!

**PortFast and BDPU Guard** are methods that can help alleviate the risk of STP failures. 

### PortFast
---
>[!tip]
>To view PortFast configuration use `show run | begin int`.


**PortFast** is configured on interfaces connected to devices that **you are sure won't create loops if STP is disabled.** With PortFast, the interface won't spend the usual 30 seconds or more **coming up into forwarding mode while STP is converging.**
- PortFast allows the transition between blocking and forwarding to be instant. This prevents host from potentially being unable to receive DHCP information due to the slow convergence time of STP.
- `spanning-tree portfast` is used to configure an interface to use PortFast.
- **On newer switches**, there is a PortFast Edge which loses it's edge status if it receives a BDPU, transitioning it to a normal STP port.


### BDPU Guard
---
>[!tip]
>Usually BDPU Guard is only configured on Access layer switches, where users and endpoints are connected.


**BDPU Guard** is a secondary configuration for **interfaces with PortFast enabled.** Essentially, if an interface with PortFast enabled receives a BDPU, the interface is **placed into an error shutdown state preventing (guarding) against the attachment of a switch or hub that could create a loop.** 
- `spanning-tree portfast bdpuguard default` can be used globally to make it the default for interfaces with PortFast enabled. 
- `spanning-tree bdpuguard enabled` can be used to configure BDPU Guard for a specific interface.
- `errdisable recovery cause bdpu`, `errdisable recovery interval <time>` can be used to automatically bring up ports that have been disabled by an error. This is ill-advised as the port may flap up and down if the error hasn't been resolved.

### Root Guard
---
**Root Guard** prevents a switch from unintentionally becoming a root bridge.
- `spanning-tree guard root` is used to enable Root Guard on an interface
- This is a defense against a threat actor plugging in a switch with a superior Bridge ID to get traffic forwarded to it.
- When a switch with a superior BDPU (false Root) attempts to become Root Bridge, an interface configured with Root Guard will ignore it and block the link, effectively causing the false Root Bridge to blackhole traffic.

### BDPU Filter
---
Similar to BDPU Guard in detecting unexpected BDPUs, but just filters them rather than shutting down the link.

Depending on where this is enabled, it will behave differently:
- In global configuration, BDPU filter will act like PortFast edge. When it receives a BDPU, it will remove PortFast and BDPU filter from the interface and treat it as a regular STP port. 
- In interface configuration, when a BDPU Filter enabled interface receives a BDPU, it will stop transmitting BDPU and ignore incoming ones, effectively disabling STP. 

It is generally **not** recommended to use BDPU Filter unless you have a single downstream connection to a legacy switch that is causing STP issues.
