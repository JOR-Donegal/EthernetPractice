---
description: Link Layer Discovery Protocol
---

# LLDP

When we are working with heterogeneous network with mixed manufacturers devices, it’s better to use an open standard. Link layer discovery protocol (LLDP) IEEE 802.1ab is also supported by Cisco devices. LLDP uses attributes with a type, length and value (TLV). TLVs are used to send information to neighbours with which they directly connect. Typical TLVs include:

* System name
* System description
* Management address

LLDP has more complex use cases. For example, an IP telephone can use it for VLAN assignment. Or an endpoint device can use it to define its power over ethernet (PoE) requirements. This is called _media endpoint discovery_ or LLDP-MED.

I have disabled CDP **(no cdp run**) and enabled LLDP (**lldp run**) on all switches.&#x20;

A quick test looks familiar.&#x20;

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

And again the detail option

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

## Exercise

On each switch, give the tagged interface a description.&#x20;

For example, on Switch22

```
int gi3/3
 description "To Switch21"
 exit
```

On Switch23

```
int gi3/3
 description "To Switch21"
 exit
```

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

Very useful, LLDP can read port descriptions.

Most Linux distros can support LLDP.
