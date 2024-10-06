In Layer 2 switching, we are focused on two devices: 
1. The switch
2. The bridge

### Introduction

While many people may refer to a switch as a bridge and vice versa, they essentially do the same task which make intelligent decisions based on the hardware address of the frames they receive. 

>[!note]
>A **switch** makes it's decisions based on the MAC filter table it builds and maintains using Application-Specific Integrated Circuits. A **bridge** uses software to build and maintain it's Content Addressable Memory (CAM) table.

Unlike a **hub** a **switch** does not flood **all** of it's traffic to every connected device. Instead, a switch relies on it's Media Access Control (MAC) filter table in order to make intelligent decisions about the destination of the traffic it receives. 

### Compared to L3

Layer 2 devices **are faster** than Layer 3 devices since they don't concern themselves with the Network layer header information. They only care about the hardware address so they can know whether to forward, flood, or drop the packet. The switching process is made even more efficient by the fact that it doesn't deal with the data contained within the packet; it's sole purpose to read the frame encapsulating the packet.

### Constructing the filter table

A switch builds it's MAC filter table by examining the source hardware address of every frame that is sent through it. 

If a frame is sent to a switch and it's address is not inside the 