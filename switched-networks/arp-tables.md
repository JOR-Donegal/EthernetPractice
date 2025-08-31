# ARP Tables

We know all about layer 2 addresses, MAC addresses. At layer 3, we use IP addresses.

But almost all data communications applications use the layer 3 address, even where computers are on the same subnet! Somehow, devices need to be able to identify what the layer 3 address is, for any layer 2 device on their subnet.

The table which holds this information is the ARP table. Both switches and computers have ARP tables, which are populated and aged in a similar way to MAC address tables.

1. On PC1
   1. Try pinging every device on the network
   2. Immediately, type the command **arp** (arp -a on a real physical computer) then record and explain the result.
2. On Switch21
   1. Try pinging every device on the network
   2. Immediately, type the command **show arp** then record and explain the result.
