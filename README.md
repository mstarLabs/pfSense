# pfSense Setup

This lab simulates a small business network environment using VirtualBox, pfSense, and multiple VLANs to isolate infrastructure, client, and server systems.

---

## Network Overview

**Virtualized Environment:**  
- All systems run in VirtualBox on a single host
- pfSense manages routing, DHCP, DNS forwarding, and inter-VLAN access

**Firewall:**
| VLAN | Subnet           | Purpose             |
|------|------------------|---------------------|
| 0    | 192.168.1.0/24   | Internal Network Firewal |

**VLANs:**
| VLAN | Subnet           | Purpose             |
|------|------------------|---------------------|
| 1    | 192.168.10.0/24  | Infrastructure + DC |
| 2    | 192.168.20.0/24  | Clients (Sales)       |
| 3    | 192.168.30.0/24  | Clients (HR) |
| 4    | 192.168.40.0/24  | File Server (HR) |

---

## Traffic Flow & Firewall Intent

<a href="https://github.com/mstarLabs/VM-Network-Architecture/blob/main/VM%20Network%20Architecture%20Diagram.png">Ref 1: VM Network Diagram</a>

![VM Network Architecture Diagram](https://github.com/user-attachments/assets/694e47a3-2b25-47b8-a0b6-89b67c6abddd)


-  pfSense enforces all inter-VLAN rules centrally
-  All VMs route external traffic through pfSense NAT
-  All clients get DNS/GPO from DC01 (192.168.10.5)
-  Win10 (VLAN 2) **cannot access** File Server
-  Win11 (VLAN 3) can access File Server (VLAN 4) on SMB/HTTPS

---

##  Skills Practiced

- Documentation and Diagramming
- Firewall Policy Planning
- Logical Topology Design
- Logical Network Mapping
- Network Segmentation Design
