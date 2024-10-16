### Introduction
---
Access Control Lists (ACLs) are a collect of rules and test that evaluate network traffic in order to make decisions about whether to forward or drop a packet. 

There are two types of ACLs that are important:
1. Standard ACL
2. Extended ACL

### Standard ACL
---
A standard ACL is limited to only evaluating the **source IP address** of a packet, everything else is not evaluated. 

Since the standard ACL is limited to only evaluating the source IP address, it's advised to place these **as close to the destination as possible.** That way traffic that may originate from a variety of source addresses won't be denied. 

##### Configuration
For the configuration, standard access list use `1-99` and `1000-1999`.

```
access-list <1-99|1000-1999> <deny|allow> host <ip> <wildcard (optional)>
```

Once the rule is made, it needs to be applied to an interface:

```
ip access-group <access-list number> <out|in>
```

### Extended ACL
---
An extended ACL is able to use the source IP, destination IP, Network layer header, and Transport layer header as conditions for it's evaluation. 

Since the extended ACL is able to evaluate so much, it's advised to place these **as close to the source as possible.** That way traffic that would eventually get denied doesn't hog up precious bandwidth.

For the configuration, extended access list use `100-199` and `2000-2699`.