# 🧩 Enterprise VLAN Segmentation

## Overview
This lab demonstrates an **enterprise-grade VLAN segmentation architecture** using Cisco Packet Tracer and Cisco IOS Layer-3 switching.  
It implements department-based VLANs, centralized DHCP with relay, inter-VLAN routing via SVIs, and a dedicated management VLAN — mirroring real-world enterprise LAN design.

This is a **hands-on, troubleshooting-driven lab**, not a theory exercise.

---

## Objectives
- Design and implement multi-VLAN segmentation
- Configure 802.1Q trunking with native VLAN hygiene
- Implement Layer-3 switching using SVIs
- Enable inter-VLAN routing
- Deploy centralized DHCP with relay (`ip helper-address`)
- Separate management traffic using a dedicated MGMT VLAN
- Validate end-to-end connectivity and routing

---

## Network Architecture

### VLAN Design
| VLAN | Name | Subnet | Gateway |
|----|----|----|----|
| 10 | SALES | 10.10.10.0/24 | 10.10.10.1 |
| 20 | IT | 10.20.20.0/24 | 10.20.20.1 |
| 30 | HR | 10.30.30.0/24 | 10.30.30.1 |
| 99 | MGMT | 10.99.99.0/24 | 10.99.99.1 |

---

## Devices Used
- **1× Cisco 3650-24PS** (Layer-3 Core Switch)
- **2× Cisco 2960-24TT** (Access Switches)
- **1× Server-PT** (Centralized DHCP Server)
- **3× PC-PT** (SALES, IT, HR)

---

## Key Technologies & Concepts
- VLAN segmentation (Layer 2)
- 802.1Q trunking
- Native VLAN mismatch mitigation
- Layer-3 SVIs
- Inter-VLAN routing
- DHCP relay (`ip helper-address`)
- Centralized DHCP services
- Enterprise access / core design principles

---

## Lab Structure

Enterprise-VLAN-Segmentation/
├── configs/ # Saved CLI configurations
├── screenshots/ # Step-by-step verification screenshots
├── topology/ # Packet Tracer (.pkt) file
└── notes/ # Troubleshooting notes and observations

---

## Verification & Validation
- VLAN membership verified on access switches
- Trunking validated on core and access switches
- SVIs confirmed up/up on core switch
- DHCP leases successfully issued per VLAN
- Inter-VLAN connectivity validated via ICMP
- Routing table confirms all connected networks

---

## Skills Demonstrated
- Enterprise LAN design
- Layer-3 switching and routing
- DHCP troubleshooting and relay configuration
- VLAN hygiene and management plane separation
- Methodical troubleshooting under failure conditions
- Professional documentation for portfolio presentation

---

## Alignment
This lab aligns with:
- **NAIT Advanced Networking**
- **Network+ objectives**
- **SOC / Blue-Team foundational networking**
- **Canadian Armed Forces (CAF) Cyber Operator baseline skills**

---

## Notes
This lab intentionally included troubleshooting scenarios (DHCP failure due to missing SVIs and management VLAN configuration) to reflect real operational environments where misconfigurations must be identified and corrected methodically.

---

## Status
**Completed — validated end-to-end**
