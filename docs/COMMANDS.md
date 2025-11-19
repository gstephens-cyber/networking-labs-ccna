# Networking Command Reference

Quick reference for common Cisco IOS and networking commands used throughout the labs.

---

## VLANs

```bash
show vlan brief
show interfaces <int> switchport
switchport mode access
switchport access vlan <id>
switchport mode trunk

## Router-on-a-Stick

```bash
interface g0/0.<vlan>
 encapsulation dot1Q <vlan>
 ip address <gateway> <mask>
no shutdown

show ip interface brief
show running-config
show interfaces status
show vlan brief

ping <ip>
tracert <ip>
