# Etherchannel

Before we begin, every port we join to an Ether Channel must have the same configuration and we will not be able to change it afterwards.&#x20;

Enter configuration mode on Switch1 and select both gigabit interfaces by typing

```
int range gi3/0-2
```

&#x20;In a production network, you can bind up to 8 interfaces in an Ether Channel. We need to check to see what channel protocols are available. Type the command&#x20;

```
channel-protocol ?
```

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

There are two possible protocols available, an open standard (LACP) and a Cisco proprietary protocol. Set the protocol to PaGP.

```
channel-protocol pagp
```

Next type the command&#x20;

```
channel-group ?
```

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

You can configure up to 255 separate groups on these switches, all my older IOS12 switches supported 48. Type&#x20;

```
channel-group 1 mode ?
```

and review the available options.

<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

I select desirable and create the channel group, then I exit conf mode.&#x20;

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

I run the same commands on Switch23. Ping to make sure both switches can still see each other.&#x20;

Look at the new interface with the command&#x20;

```
sh int port-channel 1
```

and check it’s bandwidth to make sure it is a 20Gb/s interface.

<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

Type&#x20;

```
show etherchannel 
```

to review the global settings for the switch.

Also try&#x20;

```
show etherchannel 1 port-channel
```

The command&#x20;

```
show etherchannel summary
```

&#x20;is useful where you have many Etherchannels.

Before you go, check spanning-tree to see how it treats this interface.
