# INFO 2604 – Information Systems Security | Network Security Project

**University of the West Indies, St. Augustine**  
**Course:** INFO 2604 – Information Systems Security  
**Submitted:** April 2025

---

## Project Overview

This project involved designing and configuring a secure intranet in **Cisco Packet Tracer** consisting of three department networks — Physics, DCIT, and DMS — connected via a central packet-filter router acting as a firewall.

The goal was to implement strict access control policies between the networks using **Access Control Lists (ACLs)**, controlling traffic for FTP, ICMP, Telnet, SSH, and email services.

---

## Network Topology

| Network | Subnet | Devices |
|--------|--------|---------|
| Physics | 192.168.1.0/24 | PC1, PC2, Email Server |
| DCIT | 192.168.2.0/24 | Device A (PC1), Device B (PC2) |
| DMS | 192.168.3.0/24 | PC1, PC2, FTP Server |

All networks are connected to the intranet via FastEthernet connections through a central router/firewall.

---

## Access Control Policies Implemented

### Policy 1 — Network Setup
- Minimum 2 devices per subnetwork
- All networks connected via FastEthernet

### Policy 2 — Physics → DMS (FTP Only)
- Devices in the Physics network can communicate with the DMS network for **FTP services only**
- All other traffic (ICMP, Telnet, SSH) from Physics to DMS is blocked

### Policy 3 — DCIT Network Rules
- **Device A** can communicate with DMS for FTP and ICMP only
- **Device B** can access Telnet and SSH services on the router/firewall
- Device A cannot Telnet/SSH to the router
- Device B cannot access FTP services

### Policy 4 — DMS Email
- DMS devices can send and receive emails with the Physics network
- Email server configured and verified with successful send/receive

### Policy 5 — DMS ICMP Blocked
- ICMP traffic originating from DMS devices to other networks is blocked
- DMS devices can only ping internally (e.g. the email server)

---

## Screenshots

All policy verification screenshots are included in this repository:

| File | Description |
|------|-------------|
| `Policy 1.png` | Network topology with labelled devices and IP addresses |
| `Policy 2 (Physics PC_1 pings DCIT devices).png` | Physics → DCIT blocked |
| `Policy 2 (Physics PC_1 pings DMS devices).png` | Physics → DMS FTP only verified |
| `Policy 2 (Physics PC_2 pings DCIT devices).png` | Physics PC2 → DCIT blocked |
| `Policy 2 (Physics PC_2 pings DMS devices).png` | Physics PC2 → DMS FTP only verified |
| `Policy 3 (device A).png` | DCIT Device A — FTP & ICMP to DMS only |
| `Policy 3 (device B).png` | DCIT Device B — Telnet/SSH to router verified |
| `Policy 4 (DCIT device B composing email).png` | Email composition from DMS |
| `Policy 4 (email sent success message).png` | Email sent successfully |
| `Policy 4 (Physics PC_1 receive mail success).png` | Physics PC received email |
| `Policy 5 (DMS PC's can only ping to email server).png` | DMS ICMP blocked to other networks |

---

## Files

- `ISS_Project.pkt` — Cisco Packet Tracer project file (open to view full configuration)
- `Policy *.png` — Verification screenshots for each policy

---

## Tools & Technologies

- Cisco Packet Tracer
- Access Control Lists (ACLs)
- FTP, SSH, Telnet, ICMP, SMTP
- IPv4 Subnetting (192.168.x.0/24)
- FastEthernet routing
