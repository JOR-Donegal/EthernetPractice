# VLAN Pruning

Suppose we use VTP to propagate VLANs definitions throughout a network. A client access switch might have many VLANs trunked but only use a subset. Suppose I send a broadcast on VLAN2. Every switch in the network which has a trunk connection will receive this broadcast, even if the switch does not have any ports in VLAN2.&#x20;

To reduce network traffic, we can specify any VLAN as being eligible for _pruning_. If the switch has no active port in the VLAN, the VLAN can be pruned from the trunk connection, reducing network traffic, broadcasts etc.&#x20;

Examine and understand the command **switchport trunk pruning**. Is there anywhere on our network we could employ this command?
