# Creating a ring

Add a link between Switch22 and Switch23 as shown.

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

Run the command **show spanning-tree** on each and try to figure out

* Switches
  * What protocol is in use?
  * Which switch is root?
  * What is its address?
  * What is its priority?
* Links
  * What is the topology?
  * What links are forwarding, what are blocked?

On old switches when we add the third link to make a ring, we will see orange lights……no connectivity……we broke the network!

If you leave everything to sit for a little while, one of the links will come back. This is original _Spanning Tree Protocol_ (STP) and it is switched on by default. It may sit for 30-45 seconds as it figures things out or converges. In GNS3, the IOSvL2 switch defaults to _Rapid Spanning Tree Protocol_ (RSTP) and you do not see the time delay.

On older switches, note that only one side of a link goes orange. Traffic continues to get to the far end of each link, where it is blocked. That way the switch with the blocked link knows it has a good link for future use.

Convergence only occurs when all links are either blocked or forwarding. Note that no data will transition the network while switches are converging. A topology change could result in a network outage.

From c. 2022 I have been using IOSvL2 switches for these exercises, you should see Per VLAN Spanning Tree (PVST), which is Cisco proprietary and default. I use this or Multiple Spanning Tree when I'm building networks.

When I check, I see that Switch21 is root on all VLANs

<figure><img src="../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

&#x20;Automatic selection of the root switch is based on priority and MAC address. But if priority is left as default, this means that the lowest MAC address switch will become root. On most networks, that means the oldest, nastiest, most disreputable switch in a corner of a boiler house!

We always manually select which switches will be root. On some networks, it is evident which switch should be root. Probably, the most powerful, newest, most centrally located, best connected switch. On our simple network, any of the switches could be root.

Because PVST works at layer 2 and each VLAN is like a separate layer 2 broadcast domain, you can have a separate root bridge for every VLAN.

## Selecting a root switch

&#x20;I want to set Switch22 as the primary, so on Switch22 I type&#x20;

```
spanning-tree vlan 1-4090 root primary
```

&#x20;A **show run** command shows a new line with a low priority value.

A **show spanning-tree** command shows Switch22 is now primary root.

I want to set Switch23 as the secondary, so on Switch23 I type&#x20;

```
spanning-tree vlan 1-4090 root secondary
```

&#x20;A **show run** command shows a new line with a low priority value.

A **show spanning-tree** command shows Switch23 is now secondary root.
