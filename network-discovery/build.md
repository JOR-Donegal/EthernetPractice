# Build

In GNS3, open the previous _LAGGroups_ project and save it as _Discovery_

It is easy to lose track of any network environment! With even a handful of devices and interconnections, it can be really difficult to lose track of what connection goes where. Site documentation is best known for being inaccurate and incomplete. And if it’s not, it soon will be!

This problem is exacerbated when using multi-homed hosts and this is the case in every virtualisation environment. Consider a VMware or hyper V server. Two management interfaces, two interfaces with trunking, two interfaces for storage, and maybe some more. If we colour-coded the patch leads, maybe we can track what we connected. However, if were doing remote management, that colour coding serves no purpose.

The oldest crudest and most reliable way of tracking interfaces around the network, is to find the MAC address of the underlying interface and then look at the ARP/MAC address table of the switch. If there has been any traffic, we can figure out what network interface card (NIC) is connected to what interface.

A little bit easier is to use a network discovery protocol. These protocols allow us to figure out what is connected to where.
