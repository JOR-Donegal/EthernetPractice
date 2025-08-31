# Loop Avoidance

In previous exercises you simulated taking the switch or router out of the box, getting the documentation, and doing the initial setup. After that you considered security issues with that switch or router before you put it on a live network; you looked at cracking and bypassing security. Then you looked at the concept of Ethernet Switching. In the last exercise, you examined VLANs.&#x20;

In this session we are going to see why loops occur at layer 2 and why Ethernet has no protection against this. We are then going to implement and test the original protocol to prevent loops, Spanning Tree (STP). We will mention some of the more current protocols which understand VLANs or which are more efficient. We will also note the emerging loop avoidance protocols for data centre applications.

A good layer 2 design will have redundant paths for redundancy. If one switch goes down, there is always a way for packets to get around the network. However, this creates potential paths for loops.

Loops are rather unhealthy for our network!

Broadcast and Multicast packets can be propagated endlessly through the network and delivered multiple times. Multiple copies of the same frame can be received via multiple paths. Due to frames arriving from multiple paths, MAC address tables “thrash” and our switches CPU time goes through the roof…before the switches begin to crash!

To avoid all that we send packets around the network called bridge protocol data units (BPDUs) that allow switches to learn about the topology. The switches elect a root which maintains and provides a topology map of the network. This is spanning tree protocol or STP for short.

Although redundant links are good and spanning tree allows for redundancy with loop prevention, it is not fast. Traditional spanning tree might take 30 seconds or more to re-converge after a topology change. This is redundancy, it is not high availability; clients and applications will notice the outage.

We should plan our spanning tree early on, preferably when we have only one switch! If we do not designate a root, the switch with the lowest MAC address will be elected root by its peers. Switches also have an STP priority set to the default (32768) which we can adjust.

1. You need to review what equipment is on a network, read the technical notes for the equipment and figure out what level of interoperability will work for STP.
2. If you do not take active steps to select the root, then the root switch will be the one with the lowest number MAC address. It will probably default to oldest switch on the network. Not a good default!
3. Select a switch to be the root of the spanning tree. This switch should be the most centralized switch on the network. All data flow across the network is from the perspective of this switch. We will almost always select a core switch.
4. With STP, the key is for all the switches in the network to elect a root bridge that becomes the focal point in the network. All other decisions in the network, such as which port to block and which port to put in forwarding mode, are made from the perspective of this root bridge. After you select the switch, you need to adjust its bridge priority to ensure it becomes the root.
5. We also need to select a secondary root bridge. Everything gets reset now and again, the last thing you need is uncertainty, not knowing which switch will take over the root role. On most campus size networks, we make all the switches in the core secondary root.
6. As with everything else you do in networking, test as you go along and make no assumptions!

A final word. We are only touching on spanning tree. You should probably do some reading on Rapid Spanning Tree (RSTP) and Multiple Spanning Tree (MSTP) before finishing this practical. There are also two Cisco proprietary modes, per VLAN spanning tree (PVST) and per VLAN rapid spanning tree (PVRST) which you should understand. Cisco spanning tree is not standards compatible and you may have interoperability issues. Spanning tree is an old protocol. It fixes the problem of loop avoidance on networks, at the cost of leaving (half?) the very expensive links on a network unutilized. There are better and newer protocols, especially for data centre usage. You should do an internet search, read, and understand what TRILL and SPB are before you finish.

Before you begin, ensure you have read the accompanying theory notes on spanning tree.
