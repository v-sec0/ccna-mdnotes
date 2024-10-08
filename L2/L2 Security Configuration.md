To enable switch port security for a Cisco switch, the following command needs to be ran first:
```
SW1(config-if)#switchport port-security
```

Once this command is ran, the interface is now configured with port security. 

By default, the switch is to only allow **one secure MAC address** and to **shutdown** when any violation is detected. 

To change this, the following commands can be issued:

**Setting a number of allowed secure MAC addresses:**
```
SW1(config-if)#switchport port-security maximum <number>
```

**Setting a specific MAC address:**
```
SW1(config-if)#switchport port-security mac-address <mac-address> or <sticky>
```

>[!tip]
>Using the **sticky** keyword, the port will automatically derive a secure MAC address from whatever device is connected to the interface. It will only collect the maximum of allowed secure MAC addresses.

**Setting a violation rule**
```
SW1(config-if)#switchport port-security violation <rule>
```

The rules are as follows:
1. Protect = drop frames received
2. Restrict = drop received frames and send an SNMP trap.
3. Shutdown = disable interface and send an SNMP trap