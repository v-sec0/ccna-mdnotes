### Introduction
---
**PortFast and BDPU Guard** are methods that can help alleviate the risk of STP failures. 

PortFast is configured on interfaces connected to devices that **you are sure won't create loops if STP is disabled.** With PortFast, the interface won't spend the usual 50 seconds or more **coming up into forwarding mode while STP is converging.**
- PortFast allows the transition between blocking and forwarding to be instant. This prevents host from potentially being unable to receive DHCP information due to the slow convergence time of STP.