# Security Issues

At the moment, some ports have not been configured and by default they sit in VLAN1. They remain a security risk!

Check what ports are currently in VLAN1, it will be the same on all switches.

<figure><img src="../../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure>

## Discard and Shutdown

Create a discard VLAN. We will never route to or from the discard VLAN and we can only create VLANs on Switch23.

```
en
conf  t
vlan 1000
 name Discard
exit
exit
wr mem
```

Ports gi0/0, gi0/2 and gi0/3 are access ports not in use.&#x20;

Put them into VLAN 1000 and shut them down.

```
en
conf t
int gi0/0
 description Shutdown
 switchport access vlan 1000
 shutdown
exit

int range gi0/2-3
 description Shutdown
 switchport access vlan 1000
 shutdown
exit
wr mem
```

## Native Ports

In the introduction, I discussed native ports.&#x20;

Go into configuration mode and create **vlan 999.**

```
en
conf t
vlan 999
 name Native
exit
exit
wr mem
```

In [Configuration Management and Tagging ](broken-reference)we configured gi3/0-3 as trunk ports.&#x20;

Now we need to set their native VLANs.

```
en
conf t
int range gi3/0-3
 switchport trunk native vlan 999
 exit
exit
wr mem 
```

## Testing

Move PC1 and PC2 to port gi0/2 on their respective switches. Verify that the ports are disabled.
