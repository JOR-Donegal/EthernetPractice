# Crude Load Balancing

You can't do load balancing with spanning tree!&#x20;

Or can you?

On all VLANs, Switch22 is root, is I do a show spanning-tree, all VLANs are forwarding.

On all VLANs, Switch23 is secondary, it also shows all VLANs forwarding.

If I do a show spanning-tree on all three switches, I will see one link which is not in use, for me it is 3/2 showing as blocked on each VLAN. On a mesh network, multiple links may not be used. We could mitigate that by planning our spanning-tree such that each VLAN is handled in a specific way. One way to do this would be to have different switches acting as root for different VLANs.

See if you can figure out how to do this. Make each switch the root for a VLAN and you should see every link coming up.&#x20;

I used the command shown on Switch21.

```
spanning-tree vlan 2 root primary
```

After a little while learning, if I do a **show spanning-tree**, I can see VLAN2 is forwarding on gi3/2.

If I check the other switches, I show that on Switch23, gi3/0 is now blocking. All my links are in use. By spreading the root primary around multiple switches, I can keep all links in use and get a certain amount of manual load balancing.

When you are building a network, plan a strategy for assigning root bridge such that it is balanced across all switches AND all links are used in a balanced manner. 
