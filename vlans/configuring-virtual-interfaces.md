# Configuring Virtual Interfaces

We now know how to create VLANs. Sometimes it is useful for the switch’s CPU to be accessible from a VLAN. This is the case when we want to manage the switch. For the switch to be visible to a VLAN, we need to create an interface.

Type the command&#x20;

```
show vlan
```

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

We will see later in the course that we have ordinary switches which we refer to as L2 switches. We also have switches which can act like routers; we call these L2/L3 switches or multi-layer switches.

On most L2 switches, we only configure a single IP address in a single VLAN for management.

On L2/L3 switches, we can configure an interface in every VLAN, so that the switch can act like a LAN router.

Make sure you clearly understand the difference between configuring a VLAN and configuring the interface into a VLAN before you move on.
