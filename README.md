# ospf-triangle-lab

Three-router OSPF lab in Packet Tracer covering adjacency, failover,
and troubleshooting a hello/dead timer mismatch.

## Topology
<img width="1470" height="891" alt="ospf" src="https://github.com/user-attachments/assets/423d389c-8cab-4043-85c2-f11ce3f89879" />

## IP Plan

| Segment | Subnet |
|---|---|
| R1-R2 link | 10.0.0.0/30 |
| R2-R3 link | 10.0.0.4/30 |
| R1-R3 link | 10.0.0.8/30 |
| R1 LAN | 10.0.1.0/24 |
| R2 LAN | 10.0.2.0/24 |
| R3 LAN | 10.0.3.0/24 |

Routers use .1 on their LANs (PC gateways); PCs use .10.
OSPF process 1, area 0, all links and LANs advertised.

## What I Built
- Single-area OSPF (area 0) across three routers
- Verified neighbors, routing tables, and end-to-end pings
- Tested failover by shutting down a link

## Troubleshooting: Hello/Dead Timer Mismatch
