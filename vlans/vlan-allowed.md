# VLAN Allowed

One basic principle in security is that of giving the minimum rights to any entity which it requires to carry out its role. For security reasons, we will often restrict the VLANs which are allowed on any trunked networks.

&#x20;For example, whenever I am building an ME LAN with Internet connectivity, I will group the internal client LANs (for example, VLAN 50-80). Then I will group the server and service LANs (for example VLAN 2-32). I will also group the perimeter networks and DMZs (for example VLAN 100-200). On any trunk connections, I can specify which group of VLANs is allowed.

For example, in my client access switches, the command **switchport trunk allowed 50-80** will restrict the access switches to carrying client LAN traffic by default.

Similarly, when trunking to a perimeter device (like a firewall) only the VLANs required by that firewall will be permitted.

&#x20;Look up these commands and see if they will work; in the example LAN, identify the appropriate VLANs to allow and the necessary command.
