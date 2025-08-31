# Build

In lecture notes we have looked at the basic devices which can be used on an Ethernet network.

_Repeaters_ are a layer 1 device which can be used to extend the physical length of a network segment. We will rarely use them on a modern LAN but would use them in serial communications and in long distance fibre optic networks.

_Hubs_ are multi-port repeaters. They are also layer 1 devices. Every bit which will ingress to the hub will egress out every other port. The hub does not understand the data. A hub is really a multi-port repeater.

A _bridge_ is a layer 2 device. It learns the MAC address of every node and associates it with an interface. It does understand frames, at least the address fields. It holds this information in a MAC address table. After a period with no frames, these entries age and are deleted.

These exercises are all about the next device, the _network switch_. This is the fundamental building block of all modern LANs and the component it is most important for us to be competent with.

A switch is in many ways like a very configurable multi-port bridge. MAC addresses are stored in a table, confusingly called a CAM table (that is not a typo!). We can look at the MAC address table in any switch.

In GNS3, create a new project called **SwitchedNetworks**. Below is a _physical network diagram_. I show links and ports. For this to be fully usable, I need more information, but we will discuss that in later notes.

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

1. Add three IOSv switches and call them Switch21, 22, 23. I configure Switch21 as shown, configure the other two switches with appropriate names.

```
en
conf t
hostname Switch21
no logging console informational
no ip domain-lookup
exit
wr mem
```

* The **no logging** command turns off annoying messages at the console when you are trying to configure.
* Every time you make a mistake in a command, the switch will think you are trying to resolve a domain name. This is really annoying! The **no ip domain-lookup** command disables that.

2. Add two VPCS. I configure PC1 as shown, configure PC2 as 192.168.1.102/24

```
ip 192.168.1.101/24
```

3. This network is just an Ethernet, with two PCs. Test the network works from PC2 using&#x20;

```
PC2> ping 192.168.1.101
```

You should get replies. Try pinging PC2 from PC1 and make sure that also works.

4. On Switch21, type the command

```
sh mac address-table
```

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption><p>MAC address table for Switch21</p></figcaption></figure>

Remember, MAC addresses are unique, yours will always be different from mine. Now type the command

```
sh arp
```

The ARP protocol is how Ethernet finds an Ethernet MAC address if it only knows the IP address.

<figure><img src="../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

We can see that the MAC address at line 2 of the mac-address table corresponds to PC2 and that from the perspective of Switch21, we can find the MAC address out port gi3/2.

5. Go to Switch22 and find out what the mac-address is of its interface gi3/3, by which it connects to Switch21.

```
sh int gi3/3
```

<figure><img src="../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

Find its MAC address. For me it corresponds to the third line in the MAC address table for Switch21, and it implies that from Switch21, Switch22 is connected from port gi3/3.

## Commentary

The switches detect the mac address of the devices they are connected to. There are several ways they can do this; in most cases this will be due to a proprietary protocol called _Cisco Discovery Protocol_ (CDP). If frames are exchanged, these entries will be present.

We often use this as a diagnostic tool or to find where a problematic device is on the network. A switch learns MAC addresses from hosts which are active and transmitting. These addresses are kept for a while but if a host is switched off, they may time out. The standard aging time is 300 seconds, but you can normally set that. You might want to set that low on a guest or radio network and high on a stable network.

Some devices are very quiet and may only occasionally send packets. This may cause problems and the device will not be accessible. We occasionally see this with printers, and we may need to configure _stay-alive packets_.

Sometimes a port can show a carrier light and look like its running, but it may have a status of “err-disabled”. There are many reasons for this, do some research to understand why. You may have to hard reset the switch to clear this error. The command **show interface status** can be useful for identifying these problems.

## Exercise

Work your way around all five devices, figure out what the MAC address is on each interface and what it connects to.
