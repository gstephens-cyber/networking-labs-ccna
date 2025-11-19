# Lab 02 – Basic Static Routing

## Objective

Build two separate networks and allow communication between them using static routing. This demonstrates point-to-point links, LAN segments, and manual route configuration on Cisco routers.

---

## Topology

Devices used:
- Router R1: Cisco 1941
- Router R2: Cisco 1941
- Switch SW1: Cisco 2960
- Switch SW2: Cisco 2960
- PC-A: PC-PT
- PC-B: PC-PT

Physical layout:

PC-A → SW1 → R1 → R2 → SW2 → PC-B

---

## IP Addressing

### R1 Interfaces:
- **G0/0 (LAN Left)**  
  `192.168.10.1 /24`
- **G0/1 (WAN link to R2)**  
  `10.0.0.1 /30`

### R2 Interfaces:
- **G0/0 (WAN link to R1)**  
  `10.0.0.2 /30`
- **G0/1 (LAN Right)**  
  `192.168.20.1 /24`

### PC-A:

IP: 192.168.10.10
Mask: 255.255.255.0
Gateway: 192.168.10.1

### PC-B:

IP: 192.168.20.10
Mask: 255.255.255.0
Gateway: 192.168.20.1
---

## Router Configuration

### R1

enable
configure terminal

interface g0/0
ip address 192.168.10.1 255.255.255.0
no shutdown
exit

interface g0/1
ip address 10.0.0.1 255.255.255.252
no shutdown
exit

### R2

enable
configure terminal

interface g0/0
ip address 10.0.0.2 255.255.255.252
no shutdown
exit

interface g0/1
ip address 192.168.20.1 255.255.255.0
no shutdown
exit

## Static Routes

### On R1:
ip route 192.168.20.0 255.255.255.0 10.0.0.2

### On R2:
ip route 192.168.10.0 255.255.255.0 10.0.0.1

## Verification Steps

From **PC-A**:
ping 192.168.20.10

css
Copy code

From **PC-B**:
ping 192.168.10.10

yaml
Copy code

Expected: Successful replies from both PCs.

