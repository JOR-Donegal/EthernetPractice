# Static Entries

In some cases, you may want to configure a port to “know” a certain MAC address is connected. This is useful when you have devices which are used infrequently. For example, a printer in sleep mode. These static entries will be maintained between reboots. For me to specify that the printer with MAC address 0005.5E40.8403 is always on port gi1/1, I would type the command

```
mac address-table static 0005.5E40.8403 vlan 1 interface gi1/1
```

<figure><img src="../.gitbook/assets/image (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

We use this knowledge for systems administration and for security.
