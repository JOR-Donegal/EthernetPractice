---
description: Cisco Discovery Protocol
---

# CDP

Cisco discovery protocol (CDP) is enabled by default on most of Cisco’s switches and routers. Although it is proprietary, some other vendor’s such as VMware also implement it. Link layer discovery protocol (LLDP) is an open standards implementation that does more or less the same thing.

The command&#x20;

```
sh cdp neighbors
```

will give us an indication of what is connected and where.

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

Note that CDP is enabled by default. You should make a deliberate decision as to whether or not you want to accept that default.&#x20;

For more detail...

```
sh cdp neighbors detail
```

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

Although this is very useful, it leaks too much information. We might leave it on between core devices, but not to edge routers or firewalls. The command&#x20;

```
no cdp enable
```

&#x20;on an interface will disable CDP on that interface only.&#x20;

The command&#x20;

```
no cdp run
```

will disable CDP completely.
