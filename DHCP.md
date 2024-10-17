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