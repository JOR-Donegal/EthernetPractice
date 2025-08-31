# Aging

If a node is not seen for a period of time, its entry is removed from the MAC address table. This is called _aging_. In real equipment, you can set the value in seconds, but it normally defaults to 300 seconds or 5 minutes.&#x20;

This value works fine in most networks and is a global command.

Try the command&#x20;

```
mac address-table aging-time 400
```

