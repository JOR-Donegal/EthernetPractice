# VLANs

In the last walkthrough, you looked at the concept of Ethernet Switching.&#x20;

If an Ethernet switch acts like a single _broadcast domain_, we have one physical LAN. If we can segment that switch so that some ports are in one broadcast domain and some are in another, we can create logical LANs that are independent of the physical LAN. If we can then map a segment in one switch to segments in other switches, we have a flexible way to build an enterprise network where the physical and logical LANs can be completely independent.&#x20;

This is the concept of VLANs, and we will examine them in this session. We need to do a little bit of routing in this session. If it goes over your head, do not worry, we will revisit and explain later. Before we begin, a quick note on terminology.&#x20;

In Cisco terms, joining switches with connections which support VLANs in called _trunking_. Almost everyone else calls this _tagging_. Most vendors use the term trunking as the _link aggregation_ of two or more links to provide for extra bandwidth between switches; look up LAG, LACP or link aggregation to understand what this is about. Beware, these terminology differences can cause some confusion!&#x20;

To logically separate broadcast domains on a network, the concept of VLANs was introduced. These allowed us to separate out groups of ports on one switch and connect them to groups of ports on other switches in the network, all at layer 2. Each VLAN looks like an independent Ethernet network but it can span the physical area. VLANs decouple physical network topology from logical network topology.&#x20;

Reasonably secure, VLANs have been the basis for enterprise network design. However, to get a VLAN on one switch to talk to a VLAN on another switch, we need a trunked/tagged connection between the switches. A tagged connection carries the packets for multiple VLANs over a default VLAN (normally VLAN 1). Each tagged packet has a VLAN ID based on the IEEE802.1q standard. Ethernet did not have any spare fields in its header so the IEEE802.1q standard modified the Ethernet frame for tagging.&#x20;

Only tagged links between switches use these modified Ethernet frames, although some servers can also interpret them. The standard supports 4,096 VLANs. A _native VLAN_ is the untagged VLAN on an 802.1q trunked switch port. The native VLAN and management VLAN could be the same, but it is better security practice that they are not. In fact, it is best practice to make the native VLAN reserved and otherwise unused.&#x20;

Briefly research this and try to explain why this might be the case. If a switch receives untagged frames on a tagged switch port, they are assumed to be part of the VLAN that is designated on the switch port as the native VLAN. Frames which egress a switch port on the native VLAN are not tagged.

<figure><img src="../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

In a data centre environment, we may use more complex versions of tagging. Do an internet search on the term “Q-in-Q” and understand how you might use it. Demonstrate that you understand this term. 
