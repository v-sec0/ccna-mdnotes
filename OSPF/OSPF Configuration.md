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
```
R1#sh ip ospf database
```

**Shows information about all OSPF interfaces on a router or a specific one:**
```
R1#sh ip ospf int <interface>
```

**Shows information about neighbors and formed adjacencies:**
```
R1#sh ip ospf neighbor
```

**Shows information about routing protocols being used on a router:**
```
R1#sh ip protocols
```