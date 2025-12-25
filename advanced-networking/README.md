# Advanced Networking Labs

## Overview

This section contains **advanced Packet Tracer networking labs** focused on enterprise network design, segmentation, routing, and security.  
These labs go beyond basic CCNA concepts and emphasize **real-world topology design, protocol behavior, and professional documentation**.

Each lab includes:
- A defined objective
- Structured topology and addressing
- Step-by-step configuration
- Verification and troubleshooting
- Screenshots and a complete Packet Tracer lab file

Where Packet Tracer imposes technical limitations, those constraints are **explicitly documented** rather than hidden.

---

## Labs (In Implementation Order)

### DMZ Firewall Design

**Objective:**  
Design and implement a DMZ architecture that separates public-facing services from the internal network using firewall security zones.

**Key Concepts:**
- DMZ topology and traffic flow
- Firewall inside / outside / DMZ segmentation
- Access control enforcement
- NAT concepts for public services
- Enterprise security zoning

📁 **Lab Folder:**  
`advanced-networking/DMZ-Firewall-Design/`

🔗 **Documentation:**  
[View Lab →](./DMZ-Firewall-Design)

---

### Enterprise VLAN Segmentation

**Objective:**  
Implement enterprise VLAN segmentation to logically separate network traffic and improve security and manageability.

**Key Concepts:**
- VLAN creation and naming
- Access vs trunk ports
- Layer 2 segmentation
- Inter-VLAN traffic considerations
- Structured switch configuration

📁 **Lab Folder:**  
`advanced-networking/Enterprise-VLAN-Segmentation/`

🔗 **Documentation:**  
[View Lab →](./Enterprise-VLAN-Segmentation)

---

### OSPF Multi-Area Routing

**Objective:**  
Design and configure a multi-area OSPF network with a backbone area and multiple non-backbone areas, demonstrating proper ABR behavior and inter-area routing.

**Key Concepts:**
- OSPF Area 0 backbone design
- Area Border Routers (ABRs)
- Inter-area route propagation (O IA)
- OSPF neighbor formation
- Routing table verification

📁 **Lab Folder:**  
`advanced-networking/ospf-multi-area-routing/`

🔗 **Documentation:**  
[View Lab →](./ospf-multi-area-routing)

---

### Site-to-Site IPsec VPN (ASA-Based)

**Objective:**  
Design and configure a site-to-site IPsec VPN connecting a Headquarters (HQ) LAN and a Branch LAN across an untrusted network using Cisco ASA firewalls.

**Key Concepts:**
- IPsec site-to-site architecture
- IKEv1 Phase 1 configuration
- IPsec Phase 2 (transform sets and crypto maps)
- Crypto ACLs (interesting traffic)
- ASA interface and security-level design

**Notes:**  
Cisco Packet Tracer’s ASA implementation does **not support NAT functionality**, which is required for IPsec NAT exemption.  
As a result, Security Associations (SAs) cannot form despite correct Phase 1 and Phase 2 configuration.

This lab is documented as a **design and configuration deliverable**, with CLI evidence of simulator limitations.

📁 **Lab Folder:**  
`advanced-networking/site-to-site-ipsec-vpn/`

🔗 **Documentation:**  
[View Lab →](./site-to-site-ipsec-vpn)

---

## Skills Demonstrated Across These Labs

- Enterprise network segmentation
- Firewall and DMZ design
- VLAN implementation
- Multi-area OSPF routing
- VPN design methodology
- Protocol verification and troubleshooting
- Professional technical documentation

---

## Notes

These labs prioritize **correct design, configuration methodology, and verification** over simulated “success states.”  
All configurations reflect how these technologies behave on real Cisco devices, with limitations clearly identified where Packet Tracer falls short.
