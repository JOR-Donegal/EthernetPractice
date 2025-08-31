# Build

In GNS3, open the previous _VLANNetworks_ project and save it as _LoopAvoidance_.&#x20;

Start your devices and open terminal windows to each.

In a large enterprise it would be normal to have a switch hierarchy and to multi-home connections. For example, our Switch2 might have 24 ports and could have up to twenty-four layer 2 switches hanging off it and could route locally (as it is a layer 3 switch). This would be a normal configuration for a wiring closet and in ATU Letterkenny, the communications room PR2248 which serves the old building is configured just like that. A forty-eight port L2/L3 switch could act as a core switch for forty-eight separate L2 switches, each with forty-eight ports for clients, already enough for over 2,000 nodes! There are different ways this is done; sometimes it is in layers, sometimes we stack switches and sometimes we use chassis switches with multiple blades.&#x20;

We call the layer where clients connect the _Access Layer_ and this is normally layer 2 only.&#x20;

Where we aggregate all our client connections, we call that the _Aggregation Layer_. There is an unwritten rule in network design; VLANs don’t span beyond the wiring closet. The Aggregation layer should be L2/L3 and we will be routing above this layer.&#x20;

Finally, we might uplink from the aggregation layer to the _Network Core_, which will be layer 3 only.&#x20;

In ATU Letterkenny all links from the Aggregation Layer to the Core are redundant and all links between Core switches are redundant.&#x20;

Once there are more than wiring closets/switches, we need to make other decisions. Should the topology be

* A star where all nodes connect back to a single central node
* A mesh, where some nodes are connected across the ring
* A full mesh, where every node connects to every other node&#x20;

In every case, there are design considerations which are determined by the site, costs, and required availability.

Back to our current design!&#x20;

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

The current network design is fine and might be used on a LAN for an SME or school. However, we would always design such a network as a ring for redundancy.&#x20;

If Switch21 goes down, we lose the entire network, unnecessarily. The client wants a connection between Switch22 and Switch23. We need to implement loop detection and avoidance, spanning tree.
