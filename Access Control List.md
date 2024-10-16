### Introduction
---
Access Control Lists (ACLs) are a collect of rules and test that evaluate network traffic in order to make decisions about whether to forward or drop a packet. 

There are two types of ACLs that are important:
1. Standard ACL
2. Extended ACL

### Standard ACL
---
A standard ACL is limited to only evaluating the **source IP address** of a packet, everything else is not evaluated. 

Since the standard ACL is limited to only evaluating the source IP address, it's advised to place these as close to the destination as possible. That way traffic that may originate from a variety of source addresses won't be denied. 

### Extended ACL
---
An extended ACL is able to use the source IP, destination IP, Network layer header, and Transport layer header as conditions for it's evaluation. 