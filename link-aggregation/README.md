# Link Aggregation

In a previous exercises you simulated taking the switch or router out of the box, getting the documentation, and doing the initial setup. After that you considered security issues with that switch or router before you put it on a live network; you looked at cracking and bypassing security. Then you looked at the concept of Ethernet Switching. You examined VLANs and in the last exercise, you looked at loop avoidance.&#x20;

Spanning tree allowed us to have multiple connections between switches providing improved availability. We got a little bit of benefit for load balancing VLANs, but it was crude and manual. Sometimes, we need to scale up the links between switches economically. Imagine if I have an infrastructure with 1 Gb/s ports. I need uplinks greater than 1Gb/s, do I replace the entire infrastructure?

For me, link aggregation was a kludge used to get a few more years out of an existing infrastructure. With Data Center design, that all changed. Most configurations I see from major vendors include some aspect of link aggregation for a particular purpose. Unfortunately, these all seem to be proprietary.

An alternative is to bond multiple links together and create link aggregation groups.
