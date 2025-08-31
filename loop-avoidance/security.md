# Security

If an attacker can control which switch packets flow through, they can capture packets from any node on the network. But how could you do that?

Imagine I put a rogue switch on the network and place it between two legitimate switches. As the switches exchange bridge protocol data units (BPDUs) to determine who is the root, the attacker gets to analyse the BPDUs and set the rogue bridge to a lower priority.

This simple act now leaves the attacker in control of the network at layer 2!

The attacker can now attempt to redirect flows through the network so that traffic of interest passes through the rogue switch. After this, it is a trivial matter to set a port up to mirror traffic and record voice or data exchanges.

## Guard Root

To mitigate against this type of attack, we can set ordinary access ports to disallow STP or BPDUs.

On Switch21, try the following command, this prevents the port from being changed to a root port.

```
int range gi0/0-3 
 spanning-tree guard root
```

We talked about BPDU Guard and BPDU Filtering earlier on. Remember this functionality when you consider STP Security!

There are a few other commands to check out, for example we can use a single line of command to make a switch the primary (or secondary) root for a VLAN. Can you find this command?

Although BPDUs span a network, they do not contain that much useful information. You cannot reconnoitre a complex network by sniffing BPDUs. You can determine the root bridge and the best path too it; not much else. Spanning tree is not a major problem from the perspective of information leakage. One of our graduates [looked at this](https://research.thea.ie/handle/20.500.12065/1199).
