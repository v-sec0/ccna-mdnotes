### Enabling OSPF on a Router

```
R1#conf t
R1(config)#router opsf <process_id>
R1(config-router)#network <network-address> <wildcard_mask> <area_id>
```

### Checking OSPF Configuration

**Shows configuration information for each OSPF process**
```
R1#show ip ospf
```

**Shows number of routes in the AS and the neighboring router's RID**
	Does not display all links in AS li
```
R1#sh ip ospf database
```

