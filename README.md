# Redundant Three-Tier Enterprise Network
Project simulates Three-Tier architecture with Dual ISP failover (with Internet access via GNS3 NAT), using Cisco devices (Routers, switches) and VPCS representing computers only to test connectivity.

Designed to explore LAN architecture, redundancy and multilayer switching beyond the CCNA level.

> The IP range `203.0.113.x`, `198.51.100.x` follows RFC 5737 designated only as TEST-NET-2 documentation.

## Topology
![Topology of project.](topology_of_project.png)

# Network Devices
| **Name**             | **Description**                                                                                          | **Rest**                     |
|----------------------|----------------------------------------------------------------------------------------------------------|------------------------------|
|    AccessSwitch-0    | Access layer, primary switch for VLAN 10,11,100                                                          | Default Gateway: 192.168.1.1 |
|    AccessSwitch-1    | Access layer, primary switch for VLAN 12,13                                                              | Default Gateway: 192.168.1.1 |
| DistributionSwitch-0 | Distribution layer, Inter-VLAN routing, primary gateway for VLAN 10,11,100 and VLAN 12,13 backup gateway |   Loopback address: 1.1.1.1  |
| DistributionSwitch-1 | Distribution layer, Inter-VLAN routing, VLAN 10,11,100 primary gateway and VLAN 12,13 backup gateway     |   Loopback address: 2.2.2.2  |
|     CoreSwitch-0     | Core layer, primary multilayer switch to outside network, fast forwarding (LACP) with CoreSwitch-1       |   Loopback address: 3.3.3.3  |
|     CoreSwitch-1     | Core layer, backup multilayer switch to outside network, fast forwarding (LACP) with CoreSwitch-0        |   Loopback address: 4.4.4.4  |
|     EdgeRouter-0     | Edge layer, primary path to Internet via ISP-0, NAT forwarder and failover                               |   Loopback address: 5.5.5.5  |
|     EdgeRouter-1     | Edge layer, backup path to Internet via ISP-1, NAT forwarder and failover                                |   Loopback address: 6.6.6.6  |
|         ISP-0        | WAN, Primary routing service to Internet                                                                 |               -              |
|         ISP-1        | WAN, Backup routing service to Internet                                                                  |               -              |
<br>

# All features with details
Here is the list of all technology and protocols that have been used in the the project.

> [!WARNING]
> Urgent info that needs immediate user attention to avoid problems.
