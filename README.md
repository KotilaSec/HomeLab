# 🧠 KotilaSec Homelab – Dell PowerEdge R640

A fully self-contained SOC / Infrastructure lab running on a single Dell PowerEdge R640 server.
Built to replicate enterprise conditions for detection engineering, SIEM development, and blue-team exercises.

---

## 🖥️ Hardware Overview

| Component | Specification |
|------------|----------------|
| **Model** | Dell PowerEdge R640 (1U) |
| **CPU** | 2 × Intel Xeon Gold 6152 (22 cores / 44 threads each, 2.1 GHz base) |
| **Memory** | 4 × 64 GB DDR4 ECC = **256 GB total** |
| **Storage (Data)** | 10 × 960 GB SATA SSD → RAID-10 (~4.8 TB usable) |
| **Storage (Boot)** | 2 × 240 GB M.2 BOSS SSD (mirrored OS drive) |
| **RAID Controller** | Dell PERC H740P Mini |
| **Networking** | Intel X520 Dual 10 Gb SFP+ + Quad 1 Gb RJ-45 |
| **Power** | Dual 750 W Platinum PSUs |
| **Management** | iDRAC9 Enterprise |
| **Average Power Use** | ~250–350 W (≈ 6–8.5 kWh / day) |

---

## ⚙️ Host Configuration

| Feature | Details |
|----------|----------|
| **Hypervisor** | Microsoft Hyper-V (Server 2022 Core or Datacenter) |
| **Boot Drive** | BOSS M.2 Mirror |
| **Data Volume** | RAID-10 SSD Array (VHDX storage) |
| **Virtual Switches** | `MgmtSwitch`, `LabSwitch`, `ClientSwitch` (mapped to VLANs 10/20/30) |
| **Snapshots** | Short-term testing only (checkpoints disabled for production VMs) |

---
# 🌐 KotilaSec Homelab Network Topology

This network integrates enterprise-grade routing, segmentation, and monitoring through a **FortiGate 30G** firewall and an **Aruba 2930F** Layer 3 switch.  
The design mirrors a production-grade K-12 environment with VLAN segmentation, and Hyper-V virtualization on a Dell PowerEdge R640.

---

## 🧩 Network Hardware Overview

| Device | Model | Role | Key Features |
|--------|--------|------|---------------|
| **Firewall** | Fortinet FortiGate 30G | Edge Security Gateway | SSL VPN, Threat Feeds, IDS/IPS, VLAN trunking |
| **Core Switch** | Aruba 2930F (JL253A) | L3 Core Distribution | VLAN routing, ACLs, DHCP relay, tagged uplinks to FortiGate/R640 |
| **Server** | Dell PowerEdge R640 | Hyper-V Host | All VMs + SOC stack (MyDFIR Community Labs, Projects, challenges) |
| **Access Layer** | Aruba 2540 / 2530 (future) | Edge Connectivity | Wireless VLAN breakout, PoE for APs |


