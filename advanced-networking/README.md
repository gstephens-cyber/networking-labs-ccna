# Advanced Networking Labs

## Overview

This section contains **advanced networking labs** designed to demonstrate enterprise-level routing, security, and infrastructure concepts beyond basic CCNA fundamentals.  

Each lab is built with a focus on:
- Real-world network design
- Correct protocol behavior
- Structured troubleshooting
- Professional documentation suitable for a public technical portfolio

All labs are implemented using **Cisco Packet Tracer**, with explicit documentation where simulator limitations affect full feature implementation.

---

## Lab Objectives

The Advanced Networking labs emphasize:

- Multi-area routing design and verification
- Firewall and security architecture
- VPN design methodology
- Enterprise addressing and segmentation
- Protocol validation using industry-standard CLI commands
- Clear, reproducible technical documentation

Where full protocol operation is not possible due to tool constraints, labs are documented as **design and configuration deliverables**, reflecting real-world engineering workflows.

---

## Labs Included

### OSPF Multi-Area Routing

**Objective:**  
Design and implement a multi-area OSPF network with a backbone area and multiple non-backbone areas, demonstrating proper ABR behavior and inter-area route propagation.

**Key Concepts:**
- OSPF backbone (Area 0) design
- Area Border Routers (ABRs)
- Inter-area routing (O IA routes)
- Structured IP addressing
- OSPF neighbor and route verification
- Enterprise-grade troubleshooting methodology

📁 **Lab Files:**  
`advanced-networking/ospf-multi-area-routing/`

🔗 **Lab Documentation:**  
[View Lab →](./ospf-multi-area-routing)

---

### Site-to-Site IPsec VPN (ASA-Based)

**Objective:**  
Design and configure a site-to-site IPsec VPN connecting a Headquarters (HQ) LAN and a Branch LAN across an untrusted network using Cisco ASA firewalls.

**Key Concepts:**
- IPsec VPN architecture
- IKEv1 Phase 1 configuration
- IPsec Phase 2 (transform sets and crypto maps)
- Crypto ACLs (interesting traffic)
- ASA firewall interface and security-level design
- Real-world troubleshooting and constraint documentation

**Notes:**  
Cisco Packet Tracer’s ASA implementation does not support NAT functionality required for IPsec NAT exemption. As a result, Security Associations (SAs) cannot form despite correct Phase 1 and Phase 2 configuration.  

This lab is therefore presented as a **design and configuration deliverable**, with explicit evidence of simulator limitations and expected real-device behavior.

📁 **Lab Files:**  
`advanced-networking/site-to-site-ipsec-vpn/`

🔗 **Lab Documentation:**  
[View Lab →](./site-to-site-ipsec-vpn)

---

## Tooling and Constraints

All labs in this section are built using **Cisco Packet Tracer**.  
Where Packet Tracer does not fully implement enterprise features (such as ASA NAT behavior for IPsec), limitations are:

- Explicitly identified
- Technically justified
- Documented with CLI evidence

This approach mirrors real-world engineering practice, where tooling constraints must be recognized and communicated clearly.

---

## Skills Demonstrated Across This Section

- Enterprise routing design
- Advanced OSPF configuration and validation
- Firewall interface and security-level modeling
- VPN design methodology
- Protocol troubleshooting and verification
- Technical documentation and portfolio presentation
- Clear communication of design constraints and assumptions

---

## Notes

These labs prioritize **correct architecture and methodology** over simulated “success states.”  
All configurations and verification steps reflect how the technologies behave on real Cisco devices, even when full simulation is not possible.
