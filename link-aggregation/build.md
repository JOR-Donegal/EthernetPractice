# Build

In GNS3, open the previous _LoopAvoidance_ project and save it as _LAGGroups_

Start your devices and open terminal windows to each.

Add a second link from Switch22 to Switch23

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

I use Gi3/2 on each switch.

Analyse this with Spanning Tree.&#x20;

We would expect to see one port blocked (this will be blocked on one side only).&#x20;

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

However, we do not have to organize our network that way. If both our links were rolled together as a single logical link, then there would only be a single link and no need for spanning tree.

Verify spanning-tree on all switches, but notice that VLAN2 is a bit different. Can you figure out why?

For each VLAN apart from VLAN 2, either Gi3/0 or Gi3/2 will be blocked.&#x20;
