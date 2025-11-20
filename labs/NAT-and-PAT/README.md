# NAT and PAT – Network Address Translation Lab  
**Packet Tracer 9.0.0.0810 – Beginner-Friendly A–Z Instructions**  
**Routers:** Cisco 1941  
**Switches:** Cisco 2960  
**End Devices:** PC-A, PC-B, Server-PT  

This lab demonstrates how to configure Network Address Translation (NAT) and Port Address Translation (PAT) on a Cisco router. The objective is to translate private LAN addresses into a public address using PAT overload. This simulates how real networks allow multiple internal hosts to share a single public IP address.

This version of the lab uses an “Internet Switch” instead of a Cloud device (because Packet Tracer 9.0 for macOS does not include the Ethernet cloud model).

---

# 🧱 Topology Overview

PC-A ----
\
PC-B ------ 2960-LAN-SW ---- NAT-Router (Cisco 1941) ---- Serial Link ---- ISP-Router (Cisco 1941)
|
2960 Internet-SW
|
Server-PT

yaml
Copy code

---

# 🧩 IP Addressing Scheme

## Inside LAN
- Network: **192.168.50.0/24**
- NAT Router G0/0: **192.168.50.1**
- PC-A: **192.168.50.10**
- PC-B: **192.168.50.20**
- Default Gateway: **192.168.50.1**
- DNS: **8.8.8.8**

## Router-to-Router Serial Link
- Network: **10.10.10.0/30**
- NAT Router Serial0/1/0: **10.10.10.1**
- ISP Router Serial0/1/0: **10.10.10.2**

## Internet Segment (Fake Internet)
- Network: **203.0.113.0/24**
- ISP Router G0/0: **203.0.113.1**
- Server-PT: **203.0.113.100**
- DNS: **8.8.8.8**

---

# 🧵 Cabling (Exact Ports)

### LAN Side
- PC-A FastEthernet0 → Switch Fa0/1  
- PC-B FastEthernet0 → Switch Fa0/2  
- Switch Fa0/24 → NAT Router GigabitEthernet0/0  

### WAN Side
- NAT Router Serial0/1/0 → ISP Router Serial0/1/0  
  (Serial DCE cable)  

### Internet Side
- ISP Router GigabitEthernet0/0 → Internet-SW Fa0/1  
- Server-PT FastEthernet0 → Internet-SW Fa0/2  

---

# 🔧 NAT Router Configuration (Cisco 1941)

enable
conf t

! Inside LAN
interface g0/0
ip address 192.168.50.1 255.255.255.0
ip nat inside
no shut
exit

! Serial link to ISP
interface s0/1/0
ip address 10.10.10.1 255.255.255.252
clock rate 64000
ip nat outside
no shut
exit

! Default route to ISP
ip route 0.0.0.0 0.0.0.0 10.10.10.2

! NAT ACL – match inside LAN
access-list 1 permit 192.168.50.0 0.0.0.255

! PAT (Overload) – use Serial interface as public IP
ip nat inside source list 1 interface s0/1/0 overload

end

yaml
Copy code

---

# 🌐 ISP Router Configuration (Cisco 1941)

enable
conf t

! Serial side facing NAT router
interface s0/1/0
ip address 10.10.10.2 255.255.255.252
no shut
exit

! Public-facing interface
interface g0/0
ip address 203.0.113.1 255.255.255.0
no shut
exit

! Route back to inside LAN
ip route 192.168.50.0 255.255.255.0 10.10.10.1

end

yaml
Copy code

---

# 💻 PC Configuration

### PC-A
IP Address: 192.168.50.10
Subnet Mask: 255.255.255.0
Gateway: 192.168.50.1
DNS: 8.8.8.8

shell
Copy code

### PC-B
IP Address: 192.168.50.20
Subnet Mask: 255.255.255.0
Gateway: 192.168.50.1
DNS: 8.8.8.8

yaml
Copy code

---

# 🖥 Server Configuration  
IP: 203.0.113.100
Mask: 255.255.255.0
Gateway: 203.0.113.1
DNS: 8.8.8.8

yaml
Copy code

---

# 🧪 Verification & Testing

### 1. Ping Server from NAT Router:
ping 203.0.113.100

shell
Copy code

### 2. Ping Server from PC-A:
ping 203.0.113.100

shell
Copy code

### 3. Ping Server from PC-B:
ping 203.0.113.100

shell
Copy code

### 4. Check NAT translations:
show ip nat translations

lua
Copy code

Expected example output:
Pro Inside Local Inside Global Outside Local Outside Global
icmp 192.168.50.10 10.10.10.1 203.0.113.100 203.0.113.100
icmp 192.168.50.20 10.10.10.1 203.0.113.100 203.0.113.100

yaml
Copy code

This confirms PAT overload is functioning.

---

# 📁 Files to Include in This Folder

NAT-and-PAT/
├── README.md
├── NAT-and-PAT.pkt (your Packet Tracer file)
└── screenshots/ (optional visuals)

yaml
Copy code

---

# ✔ Lab Completed

This lab covers:
- NAT inside/outside interfaces  
- PAT overload  
- Serial WAN links  
- Static routes  
- LAN-to-public communication  
- Hands-on router configuration  

This aligns with CCNA fundamentals and CAF (Canadian Armed Forces) cybersecurity network requirements.
