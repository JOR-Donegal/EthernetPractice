# Local Management

We always set at least one port in one switch per rack in the network management VLAN.&#x20;

Why might we do this?&#x20;

We will set a port on all three switches

```
en
conf t
interface gi0/1
 description Netman
 switchport access vlan 10
 switchport mode access 
 exit
exit
wr mem
```

## Testing

Move PC1 and PC2 to port gi0/1 on their respective switches. Change their IP addresses for one appropriate to VLAN 10 and do a ping test.

## Note

Most modern switches will have a dedicated management port and you cannot set a gateway. Why would this be and what problems would it solve?
