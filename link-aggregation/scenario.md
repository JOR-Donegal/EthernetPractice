# Scenario

We are building a network for an SME or school. We have three buildings with different purposes, and we need to come up with a design and configuration.

| **Building** | **Purpose** | **Nodes** |
| ------------ | ----------- | --------- |
| 1            | Offices     | <48       |
| 2            | Warehouse   | <24       |
| 3            | Shop        | <24       |

Our business has some standard requirements for separate LANs. We need to segment our network so that we can support a range of business VLANs.

| **VLAN** | **Purpose**          | **IPv4**     | **Subnet** |
| -------- | -------------------- | ------------ | ---------- |
| 1        | ISP                  | 192.168.1.0  | /24        |
| 2        | Hosts                | 192.168.2.0  | /24        |
| 3        | Staff Radio          | 192.168.3.0  | /24        |
| 4        | Power Infrastructure | 192.168.4.0  | /24        |
| 5        | Clients              | 192.168.5.0  | /24        |
| 6        | Servers              | 192.168.6.0  | /24        |
| 7        | Telephony            | 192.168.7.0  | /24        |
| 8        | HVAC Infrastructure  | 192.168.8.0  | /24        |
| 9        | Storage              | 192.168.9.0  | /24        |
| 10       | NetMan               | 192.168.10.0 | /24        |
| 11       | Security Cameras     | 192.168.11.0 | /24        |
| 12       | OOBM                 | 192.168.12.0 | /24        |
| 13       | ClusterChat          | 192.168.13.0 | /24        |
| 14       | Loopbacks            | 192.168.14.0 | /24        |
| 15       | Routers              | 192.168.15.0 | /24        |
| 16       | Links                | 192.168.16.0 | /24        |

With the current design, we have loop detection and avoidance, with per VLAN spanning tree.&#x20;

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

However, the link from Switch22 to Switch23 is pegged, we need more bandwidth.
