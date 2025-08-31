# Creating VLANs

There are many ways we can arrange VLANs and thier creation, I'm only going to focus on per-port VLANs.

If you have followed through all my previous notes, you know that there may be several places where things are kept in the file system. On an IOSvL2 device try the command

```
dir all-filesystems
```

For me, the startup-config and vlan.dat are in nvram:/

Now on Switch23 only, create all the VLANs shown in the [scenario](scenario.md), give them appropriate names but do not give them interfaces.

```
en
conf t
vlan 2
 name Hosts
 exit
vlan 3
 name StaffRadio
 exit
vlan 4
 name Power
 exit
vlan 5
 name Clients
 exit
vlan 6
 name Servers
 exit
vlan 7
 name Telephony
 exit
vlan 8
 name HVAC
 exit
vlan 9
 name Storage
 exit
vlan 11
 name Cameras
 exit
vlan 12
 name OOBM
 exit
vlan 13
 name Clusters
 exit
vlan 14
 name Loopbacks
 exit
vlan 15
 name Routers
 exit
exit
wr mem 
```

Use the command **sh vlan** to verify these have been created correctly on Switch23.
