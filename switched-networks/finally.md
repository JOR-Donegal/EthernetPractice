# Finally

On each VPCS, type **save \[return]** to save.

On each switch, type **wr mem** to save.

Copy the important parts of the final configuration to NotePad++ and save to your OneDrive. Mine looks like this for Switch21.

```
# Switch21

en
conf t

hostname Switch21
no logging console informational
no ip domain-lookup

int vlan 1
ip address 192.168.1.21 255.255.255.0
no shut

# Servers
int range gi0/1-3
 switchport mode access
 exit 

# Some clients
int range gi1/0-3
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security violation protect

# Some other clients
int range gi2/0-3                          
 switchport mode access
 switchport port-security maximum 3
 switchport port-security violation shutdown

exit
exit
wr mem
```

Turn off all devices (the big red square).

Go to **File**, **Export Portable Project** and use the file name **SwitchedNetworks**

Close down GNS3 and save the portable project file to your OneDrive.
