# 🛡️ DMZ Firewall Design (Cisco IOS + Packet Tracer)
Enterprise-grade DMZ design implementing NAT, ACL-based firewalling, and segmented network zones using Cisco IOS routers and switches in Packet Tracer.

This lab demonstrates:
- DMZ segmentation  
- ACL-based firewall logic  
- Static NAT for public web services  
- Inside/DMZ/Outside traffic control  
- Security-aligned perimeter routing  
- CAF-style defensive network operations  
- Security+ / Network+ aligned concepts  

---

## 📌 Topology Overview

**Zones**
- **Outside:** 203.0.113.0/30  
- **DMZ:** 10.10.10.0/24  
- **Inside:** 10.20.20.0/24  

**Devices**
- R1-EDGE — perimeter router + firewall  
- R2-ISP — simulated upstream provider  
- SW-DMZ — DMZ switch  
- SW-INSIDE — internal LAN switch  
- SRV-WEB — public web server  
- PC-INS1 / PC-INS2 — inside clients  
- PC-OUT — outside/Internet client  

📸 **Screenshot:** `01_topology_overview.png`

---

## 🧩 IP Addressing Summary

| Device / Interface | IP Address | Zone |
|--------------------|------------|------|
| R1-EDGE G0/0 | 203.0.113.2 /30 | Outside |
| R1-EDGE G0/1 | 10.10.10.1 /24 | DMZ |
| R1-EDGE G0/2 | 10.20.20.1 /24 | Inside |
| R2-ISP G0/0 | 203.0.113.1 /30 | Outside |
| R2-ISP G0/1 | 198.51.100.1 /24 | Internet |
| SRV-WEB | 10.10.10.10 | DMZ |
| PC-INS1 | 10.20.20.10 | Inside |
| PC-INS2 | 10.20.20.20 | Inside |
| PC-OUT | 198.51.100.10 | Outside |

---

## 🔐 Firewall Policy Summary

### **Outside → DMZ**
✔ Allowed: HTTP/HTTPS to public web server  
✔ Allowed: Established return traffic  
❌ Blocked: Unauthorized ICMP except echo-reply  
❌ Blocked: Attempts to Inside network  

### **DMZ → Inside**
❌ Blocked by policy  

### **DMZ → Internet**
✔ Allowed  

### **Inside → Internet**
✔ Allowed via NAT overload  

---

## 🧱 NAT Configuration Summary

### Static NAT (public web server)
203.0.113.2:80 --> 10.10.10.10:80
203.0.113.2:443 --> 10.10.10.10:443

shell
Copy code

### Dynamic PAT (Inside LAN)
ip nat inside source list 100 interface g0/0 overload

yaml
Copy code

📸 Screenshot: `09_r1_edge_nat_config.png`

---

## 🚧 ACL Summary

### ACL 100 — NAT source
permit ip 10.10.10.0 0.0.0.255 any
permit ip 10.20.20.0 0.0.0.255 any

shell
Copy code

### EDGE_OUTSIDE_IN — inbound firewall
permit tcp any any established
permit icmp any any echo-reply
deny ip any 10.10.10.0 0.0.0.255
deny ip any 10.20.20.0 0.0.0.255
permit ip any any

shell
Copy code

### DMZ_TO_INSIDE — DMZ segmentation
deny ip 10.10.10.0 0.0.0.255 10.20.20.0 0.0.0.255
permit ip 10.10.10.0 0.0.0.255 any

markdown
Copy code

📸 Screenshot: `18_r1_edge_acl_summary.png`

---

## 🧪 Verification Screenshots

### **1. Interface & IP Validation**
- `02_r2_isp_interface_summary.png`
- `03_r1_edge_interface_summary.png`

### **2. Host IP Configurations**
- `04_srv_web_ip_config.png`
- `05_pc_ins1_ip_config.png`
- `06_pc_ins2_ip_config.png`
- `07_pc_out_ip_config.png`

### **3. NAT Validation**
- `09_r1_edge_nat_config.png`
- `11_r1_edge_nat_translation.png`

### **4. Outside → DMZ Web Server (SUCCESS)**
📸 `12_outside_http_to_dmz_success.png`

### **5. Outside → Inside (BLOCKED)**
📸 `13_outside_attempts_blocked.png`

### **6. DMZ → Inside Blocked / DMZ → Internet Allowed**
📸 `14_dmz_to_inside_blocked_internet_allowed.png`

---

## 📄 Config Files (Saved in /configs)

- `r1-edge.txt`  
- `r2-isp.txt`  
- `sw-dmz.txt`  
- `sw-inside.txt`  
- `srv-web.txt`

These include:
- NAT  
- ACLs  
- Interfaces  
- Zone definitions  
- Routing  

---

## 🎓 Skills Demonstrated

- DMZ design & segmentation  
- NAT (Static and PAT)  
- Stateful firewall behavior (established traffic handling)  
- Security-aligned ACL logic  
- Perimeter router hardening  
- Inside/DMZ/Outside traffic control  
- Verification via packet testing & ACL hit counters  
- Professional documentation practices  
- CAF Cyber Operator foundational networking  

---

## 🗂 Future Migration (GNS3/EVE-NG)

This lab is designed so the *same configuration* can be ported to:
- Cisco IOSv  
- Cisco CSR1000v  
- FortiGate (later)  
- Palo Alto (later)  

Only interface names change.

---

## ✔ Status: Complete


