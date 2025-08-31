# Configuring Access Ports

On Switch22 and 23, we should have VLANs as per the server (Switch1). Do a **show vlan** command to verify that you are configured correctly and that you have received the information relating to VLANs from VTP.

On Switch22, try to create a new VLAN called “Marketing” as VLAN 20.&#x20;

Can you do so?&#x20;

Why not?

Do a show run and document the existing configuration of ports gi1/0-3 and gi2/0-3.

On all three switches,&#x20;

* Configure ports gi1/0-3 in the VLAN Clients&#x20;
* Configure ports gi2/0-3 in the VLAN Servers

```
en
conf t
int range gi1/0-3
 description Clients
 switchport access vlan 5
 exit
int range gi2/0-3
 description Servers
 switchport access vlan 6
 exit 
exit
```

## Testing

Now do a **show run** and verify that all has worked as expected.&#x20;

Move PC1 and PC2 to port gi1/0 on their respective switches. &#x20;

Change the IP address of PC1 and 2 to something appropriate for VLAN 5 do a ping test between them.
