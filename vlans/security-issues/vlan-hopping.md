# VLAN Hopping

The primary issues we deal with on VLAN security relate to VLAN hopping, where an intruder manages to get packets from one VLAN to another.&#x20;

Consider the case where we connect everything using defaults. Everything will be on VLAN1 and everything will work fine. Suppose we then make a server LAN as VLAN100. A hacker on a port on VLAN1 cannot get to a server on VLAN100 except via a router or firewall?&#x20;

Wrong!&#x20;

As VLAN1 is the default VLAN and the native VLAN, any tagged packets seen will be treated as if they came from another switch! For the hacker to access the server they just have to tag the packet as VLAN100 and the switch will do what it is supposed to! Tagging attacks are malicious schemes that allow a user on a VLAN to get unauthorized access to another VLAN.&#x20;

There are a few variations on this attack, but we normally call it Double Tagging.
