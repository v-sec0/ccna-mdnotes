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

bSe

