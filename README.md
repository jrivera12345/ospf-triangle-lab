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
**What I changed:** set hello to 2 and dead to 120 on R2's G0/1 interface connected to R3
**What happened:** neighbor with R3 went from FULL to DOWN state. Thus, adjacency never formed
**How I diagnosed it:** I used commands show ip ospf neighbor which showed me that R3's neighbor ID of 10.0.3.1 was no longer neighbors with R2. And show ip ospf interface showed me that R2 and R3 has mismatched hello and dead intervals.
**Fix:** I changed R2's hello interval to 10 and dead to 40. After a couple seconds, a got a log message that said it went from LOADING to FULL.
**Takeaway:** hello and dead intervals must match on both ends of a link for an adjacency to form

## Key Commands Used
- show ip ospf neighbor
- show ip route ospf
- show ip ospf neighbor
- ip ospf hello-interval
- ip ospf dead-interval
