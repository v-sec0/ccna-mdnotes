### Enabling OSPF on a Router
```
Router# conf t
Router(config)# router opsf <process_id>
Router(config-router)# network <network-address> <wildcard_mask> <area_id>
```

### Checking OSPF Configuration

**Shows configuration information for each OSPF process**
```
Router# show ip ospf
```
