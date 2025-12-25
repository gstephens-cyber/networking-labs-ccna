# Site-to-Site IPsec VPN (ASA-Based)

## Overview

This lab demonstrates the design and configuration of a **site-to-site IPsec VPN** between two networks using Cisco ASA firewalls.  
The objective is to securely connect a Headquarters (HQ) LAN and a Branch LAN across an untrusted network using industry-standard IPsec concepts.

Due to **Packet Tracer ASA simulation limitations**, full tunnel establishment and Security Association (SA) formation cannot be completed.  
However, all required **enterprise-grade configuration steps** are implemented and verified where supported.

This lab is presented as a **design + configuration deliverable**, which reflects real-world network engineering workflows when tooling constraints exist.

---

## Topology

- **HQ LAN:** 192.168.10.0/24  
- **Branch LAN:** 192.168.20.0/24  
- **Untrusted WAN:** 203.0.113.0/30  

Devices used:
- Cisco ASA 5505 (HQ)
- Cisco ASA 5505 (Branch)
- Cisco 2960 switches
- End hosts on each LAN

---

## Configuration Summary

### Interesting Traffic (Crypto ACL)

Traffic between the HQ and Branch LANs is defined as “interesting traffic” and selected for encryption.

- HQ ASA:
  - Source: 192.168.10.0/24
  - Destination: 192.168.20.0/24

- Branch ASA:
  - Source: 192.168.20.0/24
  - Destination: 192.168.10.0/24

---

### IKEv1 Phase 1 (ISAKMP)

IKEv1 is used to authenticate peers and establish a secure control channel.

Parameters:
- Encryption: AES
- Hash: SHA
- Authentication: Pre-shared key
- Diffie-Hellman Group: 2
- Lifetime: 86400 seconds

IKEv1 is enabled on the **outside** interface of each ASA, with matching peer definitions and pre-shared keys.

---

### IPsec Phase 2

Phase 2 defines how user data is encrypted and transported.

- Transform set:
  - ESP-AES
  - ESP-SHA-HMAC
- Mode: Tunnel
- Crypto map applied to the outside interface
- Crypto ACL bound to the crypto map

---

## Verification Commands

The following commands are used to verify configuration and tunnel status on real ASA devices:

show access-list
show crypto ikev1 sa
show crypto ipsec sa
show run | include crypto map


In a full ASA implementation, encrypted traffic would generate active ISAKMP and IPsec Security Associations with increasing encapsulation counters.

---

## Packet Tracer Limitation

Cisco Packet Tracer’s ASA implementation does **not support NAT functionality**, which is required for IPsec NAT exemption.

Evidence:
- NAT commands (`nat`, `global`) are unavailable
- NAT exemption cannot be configured
- As a result, IPsec Security Associations cannot form

This limitation prevents tunnel establishment **despite correct Phase 1 and Phase 2 configuration**.

The lab is therefore documented as a **complete design and configuration exercise**, with explicit evidence of simulator constraints.

---

## Files Included

- `Site-to-Site-IPSec-VPN.pkt` — Packet Tracer lab file  
- `screenshots/` — Configuration and verification evidence  
- `README.md` — Lab documentation  

---

## Skills Demonstrated

- Site-to-site IPsec VPN design
- ASA firewall interface and security-level configuration
- Crypto ACL (interesting traffic) definition
- IKEv1 Phase 1 configuration
- IPsec Phase 2 configuration
- Crypto map implementation
- Technical troubleshooting and constraint documentation
- Professional GitHub-ready lab documentation

---

## Notes

This lab emphasizes **correct VPN architecture and configuration methodology**, even when full simulation is not possible.  
Explicit documentation of tool limitations reflects real-world engineering practice and decision-making.

