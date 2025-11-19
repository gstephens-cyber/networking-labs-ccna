# Lab 02 – Basic Static Routing

## Objective

Configure static routes between two routers to allow end-to-end connectivity across three networks.

## Topology

- Router R1  
- Router R2  
- Switch SW1 (connected to R1)  
- Switch SW2 (connected to R2)  
- PC-A (LAN behind R1)  
- PC-B (LAN behind R2)

## IP Addressing

| Device | Interface | IP Address      | Description |
|--------|-----------|-----------------|-------------|
| R1     | G0/0      | 10.0.0.1/30     | Link to R2 |
| R2     | G0/0      | 10.0.0.2/30     | Link to R1 |
| R1     | G0/1      | 192.168.10.1/24 | LAN 1 |
| R2     | G0/1      | 192.168.20.1/24 | LAN 2 |
| PC-A   | NIC       | 192.168.10.10   | Host in LAN 1 |
| PC-B   | NIC       | 192.168.20.10   | Host in LAN 2 |

## Static Routes

On R1:
