### Introduction
---
Dynamic Host Control Protocol is a protocol that simplifies the handling of IP addressing for medium to large networks. 

It allows one central server to supply IP address information for multiple host on a network. 

Some of the information included in a DHCP response includes:
1. Host IP
2. Gateway IP
3. DNS Server IP
4. TFTP Server IP
5. Subnet Mask.

A DHCP server can either be a dedicated server or a process running on a pre-existing server such as a router, or computer. 

### Commands
---
==Cisco Configuration==
 
To configure DHCP on a Cisco router, one must first start by defining which IPs will not participate in the DHCP pool process:

```
ip dhcp excluded-address <address> <address> <...> 
```

After that, a DHCP pool can be defined:

```
ip dhcp pool <pool-name>
```

Once that's defined, you will enter DHCP configuration mode and be able to define the network, default gateway, and DNS server:

```
network <address> <subnet>
default-router <address>
dns-server <address>
```

==Passing traffic over router==

In some situations, the DHCP server may be across a router, in that case the router must be configured to pass DHCP request traffic across the network to the server. 

```
int <interface-facing-endhost>
ip helper-address <ip-of-server>
```

This configuration must be done on the interface facing the end host that will be sending DHCP request. 

==Router Receiving IP via DHCP==

In some cases, the router may need to get an IP from the ISP. 

On the interface facing the server provider, the following command should be ran to enable DHCP:

```
int <int-facing-isp>
ip address dhcp
no shut
```

`show dhcp lease` can be used to display DHCP information.