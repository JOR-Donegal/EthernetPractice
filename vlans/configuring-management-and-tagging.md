# Configuring Management and Tagging

On each switch, create VLAN10 and give the switch an interface in VLAN10 with an IP address of 192.168.10.x where x is the switch number (e.g. 21, 22, 23). My example shows the configuration I used on Switch21

```
en
conf t
vlan 10
 name NetMan
 exit
int vlan 10 
 description "interface to NetMan"
 ip address 192.168.10.21 255.255.255.0
 no shut
exit
exit
wr mem
```

Access all three switches and configure the switch interconnecting ports as trunk ports. I will use all the gi3/x ports as trunks and I give an example below of how to do this. Depending on the switch and firmware version, some of these commands may be rejected.

```
en
conf t
int range gi3/0-3
 switchport trunk native vlan 999
 switchport trunk encapsulation dot1q
 switchport mode trunk               
 exit
exit
wr mem
```

## Testing

Do a ping test between switches, using their VLAN10 addresses. You may notice one or more pings timing out...why?

What is the default native VLAN?&#x20;

Why don’t we use VLAN1?
