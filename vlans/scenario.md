# Scenario

We are building a network for an SME or school. We have three buildings with different purposes, and we need to come up with a design and configuration.

| **Building** | **Purpose** | **Nodes** |
| ------------ | ----------- | --------- |
| 1            | Offices     | <48       |
| 2            | Warehouse   | <24       |
| 3            | Shop        | <24       |

Our business has some standard requirements for separate LANs. We need to segment our network so that we can support a range of business VLANs.

<table data-header-hidden><thead><tr><th width="134"></th><th></th><th width="165"></th><th></th></tr></thead><tbody><tr><td> <strong>VLAN</strong></td><td> <strong>Purpose</strong></td><td><strong>IPv4</strong></td><td><strong>Subnet</strong></td></tr><tr><td>1</td><td>ISP</td><td>192.168.1.0</td><td> /24</td></tr><tr><td>2</td><td>Hosts</td><td>192.168.2.0</td><td> /24</td></tr><tr><td>3</td><td>Staff Radio</td><td>192.168.3.0</td><td> /24</td></tr><tr><td>4</td><td>Power Infrastructure</td><td>192.168.4.0</td><td> /24</td></tr><tr><td>5</td><td>Clients</td><td>192.168.5.0</td><td> /24</td></tr><tr><td>6</td><td>Servers</td><td>192.168.6.0</td><td>/24</td></tr><tr><td>7</td><td>Telephony</td><td>192.168.7.0</td><td>/24</td></tr><tr><td>8</td><td>HVAC Infrastructure</td><td>192.168.8.0</td><td> /24</td></tr><tr><td>9</td><td>Storage</td><td>192.168.9.0</td><td> /24</td></tr><tr><td>10</td><td>NetMan</td><td>192.168.10.0</td><td> /24</td></tr><tr><td>11</td><td>Security Cameras</td><td>192.168.11.0</td><td> /24</td></tr><tr><td>12</td><td>OOBM</td><td>192.168.12.0</td><td>/24</td></tr><tr><td>13</td><td>ClusterChat</td><td>192.168.13.0</td><td> /24</td></tr><tr><td>14</td><td>Loopbacks</td><td>192.168.14.0</td><td> /24</td></tr><tr><td>15</td><td>Routers</td><td>192.168.15.0</td><td> /24</td></tr><tr><td>16</td><td>Links</td><td>192.168.16.0</td><td> /24</td></tr></tbody></table>

&#x20;
