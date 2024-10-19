### Introduction
---
>[!tip]
>Root Guard and Loop Guard are mutually exclusive on ports. Both cannot be enabled on the same port.
>
>If they are both needed, they need to be enabled on the interface level and no globally.



On some Cisco switches there SFP port that allow for fiber connections to be ran from one device to another. In these fiber connections, there's a receiver link and a transmitter link. 

In some scenarios, one of the links can go down causing a unidirectional issue where the link is only able to receive or transmit. 
- This can cause issues for networks with STP, one side will stop receiving BDPUs and assume that the link between the Root Bridge and the switch it was connected to was lost. When that happens, that connection may transition to a forwarding state and began sending BDPUs and other traffic. This can lead to a one-way loop. 

There are two solutions to this issue:
1. Loop Guard
2. UDLD (Unidirectional Link Detection)

UDLD works by sending keep-alive messages in both directions and if one doesn't arrive, it assumes there has been an unidirectional link error.

### Loop Guard
---
A STP feature available in MST, PVST+, and RPVST+.

BDPUs are expected on Root and Blocking ports. When Loop Guard is enabled, when it detects that BDPUs are not being received, it sets the link into a loop-inconsistent state (blocking) until BDPUs are received once more.

Also protects against software failure that may prevent BDPUs from being sent on a port. 

It can be enabled globally or on an interface level:
- Global -> `spanning-tree loopguard default`
- Interface -> `spanning-tree guard loop`

Loop Guard can be enabled on Designated ports but it will take no action when no BDPU is received. 

