---
description: VLAN Trunk Protocol
---

# VTP

We could manually create VLANs on all switches, however for a large network, this quickly becomes unmanageable. With CISCO equipment, we can use VTP to distribute VLAN information.

VTP only runs over trunks. First, check the current trunk status on Switch23.

```
show interface trunk
```

To configure VTP, we need to define a VTP domain name on Switch1. This configuration will not be visible in the running or saved configurations.

```
en
conf t
vtp mode server
 vtp domain DonegalSME
 vtp password DSME
 vtp version 3
 exit
exit
vtp primary vlan
```

I can check the status of VTP to confirm it functions on Switch23.

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

Also try the command

```
show vtp password
```

On the other two switches configure as shown

```
en
conf t
vtp mode client
 vtp domain DonegalSME
 vtp password DSME
 vtp version 3
exit
```

Now validate Switch21 and 22.

```
en
show vtp password
show vtp status
```

A final word on VTP; it is Cisco proprietary and tends to lead to lock-in. If you have a large infrastructure and everyone is used to VTP, they are reluctant to move from Cisco. This is a really bad idea and one of the things that keeps me from using proprietary protocols.

If you are not going to use VTP, set the VTP mode to _transparent_ to switch it off.
