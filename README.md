# 🏢 IT Infrastructure Design for European Law Firm

A comprehensive, enterprise-grade network and infrastructure design project created by **Ysani Peña** for the **Network Administration** course. This semester-long project outlines a full IT architecture supporting security, redundancy, scalability, GDPR compliance, and efficient daily operations for a small European corporate law firm.

---

## 📐 Project Overview

- **Client:** A 30-employee law firm specializing in corporate legal services
- **Objectives:**
  - Design secure infrastructure for sensitive legal documents
  - Meet GDPR compliance for European clients
  - Implement robust backup and recovery strategies
  - Ensure reliable uptime with redundancy and failover systems
- **Constraints:** $100,000 budget, data encryption in transit and at rest, limited IT staffing

---

## 🧱 Network Topology

- **Primary Firewall:** Fortinet FortiGate 200F (NGFW) with High Availability (HA) Sync
- **Switching Infrastructure:** 3x UniFi Pro Max 48 PoE (Layer 3)
- **Controller:** UniFi Dream Machine Pro Max (HA Pair)
- **ISP Redundancy:**
  - Primary: BTNet (1 Gbps fiber)
  - Secondary: Starlink (Failover via HA sync)
- **Power Redundancy:**
  - CyberPower UPS for firewalls
  - UniFi USP-RPS for PoE switch backup
  - Generac Tri-Fuel Generator for full infrastructure

---

## 🌐 VLAN Design

| VLAN | Purpose            | Access Rules |
|------|--------------------|--------------|
| 10   | Legal Department   | Access to VLANs 40, 50 |
| 20   | Non-Legal Dept.    | Access to VLANs 40, 50, limited 60 |
| 30   | IT Department      | Full access to all VLANs |
| 40   | Servers & Printer  | Accessible by VLAN 10/20/50/60 with RBAC. VLAN 30(IT) = full access |
| 50   | Wi-Fi Access Points| Managed by VLAN 30 |
| 60   | Security Cameras   | Read-only access by VLAN 20 receptionist and full access by VLAN 30(IT) |

---

## 🖥️ Hardware Inventory

- **Workstations:** Lenovo ThinkPad X13 Gen 5 (Legal/Non-Legal/IT), Dell OptiPlex (Front Desk)
- **Servers:** 
  - 3x Dell PowerEdge R650 (Application/File/Main)
  - Lenovo ThinkSystem SR650 V2 (Backup)
- **Security:** 
  - 12x G5 Pro 4K Cameras (PoE)
  - UniFi NVR Pro with Seagate IRONWOLF Drives
- **Wi-Fi:** 
  - 4x UniFi U7 Pro APs (Wi-Fi 7)

---

## ☁️ Web Services

- **Microsoft 365 Business Premium**
  - Outlook, Teams, Exchange, OneDrive, Defender
- **Clio (Secure Client Portal)**
  - Encrypted document sharing, billing, e-signatures
- **DPOrganizer (GDPR Compliance)**
  - Data mapping, audit logs, RoPA reporting
- **Google Voice**
  - External VOIP solution for cost-effective communication

---

## 💾 Backup & Recovery Strategy

- **On-Site Backup:**
  - Lenovo SR650 with VEEAM Agent
  - Weekly full + daily incremental (AES-256 encryption)
- **Off-Site Backup:**
  - VEEAM Data Cloud Vault
  - 90-day retention for critical disaster recovery
- **Recovery Time Objectives (RTO):**
  - File/Main Server: 2 hrs
  - Network Configs: 2–3 hrs
  - Application Server: 4 hrs
  - NVR System: 4–6 hrs

---

## 🛡️ Security & Compliance

- **Firewalls:** FortiGate NGFWs with SSL inspection, threat protection
- **Encryption:** AES-256 for all backups and file storage, BitLocker enabled
- **MFA & Secure Email:** Microsoft Defender, SFTP, Outlook integration
- **Access Control:** Role-Based Access (RBAC) via VLAN and firewall rules
- **Redundancy:** HA firewall sync, dual ISPs, UPS, and generator failover

---

## 🧰 Helpdesk System

- **System Used:** osTicket (Demo & Workflow included)
- **Support Categories:** Hardware, Software, Network, Security, General
- **Escalation Levels:** Helpdesk → SysAdmin → IT Director
- **Response SLAs:**
  - SEV1: Immediate
  - SEV2: 1 hour
  - SEV3: Same day
- **Scripts:** Password Reset, Email Access Troubleshooting

---

## 📊 CMM-Based Infrastructure Assessment

| Domain                    | Maturity Level | Notes |
|--------------------------|----------------|-------|
| Network Architecture     | Level 4 (Managed) | Full VLAN segmentation and HA firewall |
| Backup & Disaster Recovery | Level 4 (Managed) | On/Off-site with encryption, defined schedule |
| Server Infrastructure    | Level 4 (Managed) | RAID, redundancy, could improve with failover clustering |
| Security Architecture    | Level 3 (Defined) | Add IDS/IPS and SIEM for higher maturity |
| Email & Collaboration    | Level 5 (Optimizing) | Cloud-native Microsoft 365 solution |
| Scalability Planning     | Level 4 (Managed) | Modular with upgrade paths |

---

## 📈 Improvements Made (IT Advisor Feedback)

- Added Starlink internet for failover
- Simplified Wi-Fi VLAN architecture
- Removed unnecessary dummy switch
- Configured Fortinet HA firewall sync

---

## 💰 Project Cost Summary

| Category                     | Cost         |
|-----------------------------|--------------|
| Hardware (Servers, Switches, Cameras) | $111,019.30 |
| Software/Cloud (Annually)   | $40,116.00/year |
| Power Backup Systems        | $1,834.00     |
| **Total Cost**              | **$152,969.39** |

---

## 📎 Files Included

- `MU_Network_Topology.png` – Detailed Network Topology diagram
- `MU_Backup_Overflow.png` - Detailed Backup Overflow diagram
- `IT-Infrastructure-for-European-Law-Firm.pdf` – Final presentation documentation

---

## 👤 Author

**Ysani Peña**  
Junior Computer Science Major  
Southern Adventist University

---

## 📝 License

This project was created for educational purposes and is intended for academic presentation only.
