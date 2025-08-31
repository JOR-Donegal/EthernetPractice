# Configuring Ports

Before we start, a cool trick!&#x20;

If I want to configure ports 1 to 3 in a single command, I can use

```
int range gi0/1-3
 switchport mode access
 exit 

```

Ports can be used to connect switches together, Cisco calls these _trunk ports_, everyone else but Cisco calls this _tagging_. We will look at this in later sessions.&#x20;

A port which will be used for a normal node is called an _access port_, we configure most of our switch ports as access ports.

&#x20;To set port security, a typical configuration might be:

```
conf t
int range gi1/0-3
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security violation protect
exit
exit
```

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

_Sticky_ means that the port learns the first MAC address it sees and will show a violation if something else is connected to it.&#x20;

_Protect_ means that traffic from any other MAC address will be dropped. We could use a different configuration for other users.

Some other options on a different port range...

<pre><code>conf t
<strong>int range gi2/0-3                          
</strong> switchport mode access
 switchport port-security maximum 3
 switchport port-security violation shutdown
exit
exit
</code></pre>

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

Can you figure out what the commands I have used do?&#x20;

We can take security even further. You can specify the MAC address per port which is allowed. You might do this in a sensitive department, only allowing certain PCs to connect to pre-configured ports. However, this approach is an administrative nightmare and is not scalable.

Finally try the command

```
show port-security interface gi1/3
```

If a violation occurs, this is how you figure out what is wrong!
