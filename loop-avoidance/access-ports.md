# Access Ports

Where a port will NOT ever be used to connect to another switch and cannot possibly cause a loop, we could use port fast to speed up convergence.&#x20;

Go to Switch22 and set the PC1 port to **port fast**. My configuration is now

```
int gi0/1
 description Netman
 switchport access vlan 10
 switchport mode access
 negotiation auto
 spanning-tree portfast

```

If all the standard ports will be used for client PCs and servers, we can set port fast on all by using the range command. Do this on all three switches for all ports in the gi0/0,1,2,3, gi1/0,1,2,3 and g2/0,1,2,3 ranges. Hint, use the **range** command option.

But if someone connects a switch to two of these ports, instant loop, broken network, disaster!

To avoid this, if we are using port fast, we also use **BPDU Guard**. This command disables any **port fast** port if a BPDU is received. In a real network, always enable BPDU Guard or filtering or whatever similar functionality is available.

Again, use the range command. As a sample, my connection to PC1 is now

```
int gi0/1
 description Netman
 switchport access vlan 10
 switchport mode access
 negotiation auto
 spanning-tree portfast edge
 spanning-tree bpduguard enable
```

## Exercise

Go back to Switched Networks, Configuring Ports. You should have decided on some basic port security settings. If you add them to the settings above, you have a good basic template for any access port.

Using the range command, implement those secuirty settings.
