# Evading Security

Wherever we lock down ports using MAC address-based security, people invariably figure out how to bypass the security. If you know the MAC address of the device which is allowed, you change the MAC address on your laptop, and you are straight in!

&#x20;It is always worth configuring port security, but you should not lock things down to the point where the security causes disruption. The first configuration shown will prevent many forms of attack, without adding an administrative load.

Modern CISCO switches allow you to use _smartports_. You tell the switch the port connects to a PC; the switch figures out how to configure the port securely. On a production C3560 running IOS 12 the following secure configuration is default.

```
interface FastEthernet0/5
 description XXXXXXXXX
 switchport access vlan 5
 switchport mode access
 switchport port-security
 switchport port-security aging time 2
 switchport port-security violation restrict
 switchport port-security aging type inactivity
 macro description cisco-desktop

```

Make sure you understand all these commands, do some research if unclear.
