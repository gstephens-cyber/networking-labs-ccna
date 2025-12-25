# Advanced Networking Labs

This section contains advanced, enterprise-focused networking labs designed to demonstrate real-world routing, switching, and network security concepts.  
Each lab is fully documented with configuration evidence, verification outputs, and professional technical write-ups suitable for academic review and portfolio presentation.

All labs are built and validated using **Cisco Packet Tracer**, following industry best practices for hierarchical design, security, and troubleshooting.

---

## Completed Labs

### OSPF Multi-Area Routing
**Status:** Completed and verified

This lab demonstrates the design and implementation of a hierarchical OSPF network using multiple areas.  
It includes an Area 0 backbone, multiple non-backbone areas, Area Border Routers (ABRs), and full inter-area route verification.

**Concepts demonstrated:**
- OSPF backbone and non-backbone areas
- Area Border Router (ABR) design
- Passive-interface best practices
- Inter-area route propagation
- OSPF neighbor and routing table verification

**Lab files:**  
- [OSPF Multi-Area Routing](./ospf-multi-area-routing/)

---

## In Progress Labs

### Site-to-Site IPSec VPN
**Status:** In progress

This lab demonstrates a secure site-to-site IPSec VPN between two remote networks across an untrusted WAN.  
It focuses on encrypted inter-site communication using IKE Phase 1 and Phase 2, crypto maps, and traffic verification.

**Planned concepts:**
- Site-to-site IPSec VPN design
- ISAKMP (IKE Phase 1) configuration
- IPSec transform sets (Phase 2)
- Crypto map application
- Encrypted traffic verification

**Lab files:**  
- [Site-to-Site IPSec VPN](./site-to-site-ipsec-vpn/)

---

## Planned Labs

The following labs are planned to further expand enterprise networking and security coverage:

- Advanced NAT & PAT
- OSPF Route Redistribution
- BGP Fundamentals
- Secure DMZ Architecture
- Inter-VLAN Routing with ACL Enforcement
- High Availability (HSRP / VRRP)

---

## Tools & Environment
- Cisco Packet Tracer
- CLI-based router and switch configuration
- Structured IP addressing
- Professional troubleshooting methodology

---

## Documentation Standard
Each lab includes:
- A dedicated folder per lab
- A fully formatted `README.md`
- Step-by-step configuration screenshots
- Verification and validation outputs
- Clear separation between design, configuration, and proof

This structure ensures consistency, readability, and long-term maintainability across all labs.

---

## Status
Active development — labs are added and verified continuously.
