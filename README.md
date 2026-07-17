# cisco-packet-tracer-labs
A growing collection of Cisco Packet Tracer labs demonstrating practical CCNA networking concepts, including routing, switching, VLANs, DHCP, NAT, ACLs, and network troubleshooting.


# Cisco Packet Tracer - Default Routing Lab

## Overview

This project demonstrates the implementation of **Default Routing** using Cisco Packet Tracer.

The lab consists of two routers connected together, each serving a separate LAN. A default route is configured on both routers to allow communication between different networks.

---

## Topology

- 2 Cisco Routers
- 2 Cisco Switches
- 8 PCs (4 PCs per LAN)

Network Diagram:

![Topology](topology.png)

---

## IP Addressing

| Device | Interface | IP Address |
|---------|-----------|------------|
| R1 | G0/0 | 192.168.1.1/24 |
| R1 | G0/1 | 10.0.0.1/30 |
| R2 | G0/0 | 192.168.2.1/24 |
| R2 | G0/1 | 10.0.0.2/30 |

---

#IP Addressing

Router1
Interface	IP Address
G0/1	192.168.1.1/24
G0/0	10.0.0.1/30

Router2
Interface	IP Address
G0/1	192.168.2.1/24
G0/0	10.0.0.2/30

PCs on Switch1
PC	IP Address	Mask	Gateway
PC0	192.168.1.2	255.255.255.0	192.168.1.1
PC1	192.168.1.3	255.255.255.0	192.168.1.1
PC2	192.168.1.4	255.255.255.0	192.168.1.1
PC3	192.168.1.5	255.255.255.0	192.168.1.1

PCs on Switch2
PC	IP Address	Mask	Gateway
PC4	192.168.2.2	255.255.255.0	192.168.2.1
PC5	192.168.2.3	255.255.255.0	192.168.2.1
PC6	192.168.2.4	255.255.255.0	192.168.2.1
PC7	192.168.2.5	255.255.255.0	192.168.2.1

#Router1 Configuration

enable
configure terminal

interface g0/1
ip address 192.168.1.1 255.255.255.0
no shutdown
exit

interface g0/0
ip address 10.0.0.1 255.255.255.252
no shutdown
exit

ip route 192.168.2.0 255.255.255.0 10.0.0.2

end
write memory


#Router2 Configuration

enable
configure terminal

interface g0/1
ip address 192.168.2.1 255.255.255.0
no shutdown
exit

interface g0/0
ip address 10.0.0.2 255.255.255.252
no shutdown
exit

ip route 192.168.1.0 255.255.255.0 10.0.0.1

end
write memory

#Default Routing is a routing method in which a router forwards packets to a default gateway when it does not know the destination network.

Instead of storing routes for every network, the router uses a default route (0.0.0.0/0) to send all unknown traffic to the next-hop router.

Advantages:

Reduces the routing table size.
Simplifies router configuration.
Commonly used to forward traffic toward the Internet or an upstream router.
