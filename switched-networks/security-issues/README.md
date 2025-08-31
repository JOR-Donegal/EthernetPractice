# Security Issues

We can attack a switch by flooding the MAC address table (CISCO call this the CAM table for Content Addressable Memory). Once the MAC address table is full, most switches go back to flooding (remember how bridges and switches work?).

Switches possess a finite hardware learning table to store the source addresses of all received packets, when this table becomes full, the traffic that is directed to addresses that cannot be learned anymore will be permanently flooded. This is called a MAC Flooding Attack.

On a Cisco switch, there are various permutations of the show mac-address-table command which allow you to view the current entries. To simulate an attack, do an Internet search and understand the macof tool included in the DSniff toolset.

The ARP protocol is an old technology and has no security built into it. Consequently, anyone can claim to be the owner of any IP address within a specific subnet. ARP poisoning or ARP spoofing attacks are an effective way to fool end stations or routers into learning counterfeited device identities. This allows a malicious user to pose as intermediary and perform a Man-In-the-Middle (MitM) attack

We can generally protect against these kinds of attack by using Port Security. This function traps a violation on a port and takes an action to mitigate against it. Do some background reading on the Port Security commands and make sure you understand them.
