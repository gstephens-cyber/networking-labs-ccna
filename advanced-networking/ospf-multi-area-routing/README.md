# OSPF Multi-Area Routing

## Overview
This lab demonstrates the design, configuration, and verification of **OSPF Multi-Area Routing** using an enterprise-style hierarchical topology.  
The network is segmented into a **backbone area (Area 0)** and **multiple non-backbone areas**, interconnected through **Area Border Routers (ABRs)** to improve scalability, routing efficiency, and fault isolation.

All configuration and verification were performed using **Cisco Packet Tracer**, following professional networking and documentation practices suitable for academic submission and portfolio presentation.

---

## Objectives
- Design a hierarchical OSPF topology using multiple areas
- Configure **Area 0** as the OSPF backbone
- Implement **Area Border Routers (ABRs)**
- Advertise inter-area routes using OSPF
- Apply `passive-interface` best practices
- Verify OSPF adjacencies, routing tables, and end-to-end connectivity

---

## Network Topology

### OSPF Area Design
- **Area 0 (Backbone)**
  - R1-CORE
  - R4-BACKUP
- **Area 10 (Branch A)**
  - R2-ABR-A
  - PC-A
- **Area 20 (Branch B)**
  - R3-ABR-B
  - PC-B

The backbone area provides transit connectivity between all non-backbone areas, ensuring OSPF scalability and compliance with hierarchical routing design principles.

---

## IP Addressing Scheme

### Backbone Links (Area 0)
| Link | Network | Device | IP Address |
|---|---|---|---|
| R2 ↔ R1 | 10.0.0.0/30 | R2-ABR-A | 10.0.0.1 |
|         |             | R1-CORE  | 10.0.0.2 |
| R1 ↔ R4 | 10.0.0.4/30 | R1-CORE  | 10.0.0.5 |
|         |             | R4-BACKUP | 10.0.0.6 |
| R4 ↔ R3 | 10.0.0.8/30 | R4-BACKUP | 10.0.0.9 |
|         |             | R3-ABR-B | 10.0.0.10 |

---

### LAN Networks
| Area | Network | Gateway | Host |
|---|---|---|---|
| Area 10 | 10.10.10.0/24 | 10.10.10.1 | PC-A (10.10.10.10) |
| Area 20 | 10.20.20.0/24 | 10.20.20.1 | PC-B (10.20.20.10) |

---

## OSPF Configuration Summary

### General OSPF Design Choices
- **OSPF Process ID:** 1
- **Explicit Router IDs** configured on all routers
- **`passive-interface default`** applied to prevent unnecessary adjacencies
- Only backbone links explicitly enabled for OSPF neighbor formation
- LAN interfaces remain passive for security and stability

---

### Area Assignments
- **Area 0:** All inter-router backbone links
- **Area 10:** Branch A LAN (R2-ABR-A)
- **Area 20:** Branch B LAN (R3-ABR-B)

---

## Verification & Validation

### OSPF Neighbor Adjacencies
All routers successfully formed OSPF adjacencies in **FULL** state:
- R1-CORE ↔ R2-ABR-A
- R1-CORE ↔ R4-BACKUP
- R4-BACKUP ↔ R3-ABR-B

Verification performed using:
```text
show ip ospf neighbor
Routing Table Verification
Inter-area routes were successfully learned across the backbone and non-backbone areas.

Verified on R1-CORE using:

text
Copy code
show ip route ospf
Observed routes included:

10.10.10.0/24 (O IA)

10.20.20.0/24 (O IA)

End-to-End Connectivity
Successful end-to-end connectivity was confirmed between branch hosts.

Verification performed from PC-A:

text
Copy code
ping 10.20.20.10
Initial packet loss observed during ARP resolution is expected behavior in Packet Tracer. Subsequent ICMP replies were successful with 0% loss.

Files Included
OSPF_multi-area.pkt – Complete Packet Tracer lab file

screenshots/ – Step-by-step configuration and verification evidence

README.md – Lab documentation

Skills Demonstrated
Enterprise OSPF multi-area design

Backbone and ABR implementation

Structured IP addressing

OSPF neighbor and route verification

Troubleshooting OSPF adjacencies

Professional technical documentation

Notes
This lab emphasizes real-world OSPF troubleshooting and validation techniques.
Special attention was given to interface state verification, passive-interface behavior, and deterministic router identification — all critical skills in production networks.

