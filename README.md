# 🏢 Windows Server Enterprice Lab

> A production-inspired Windows Server 2025 infrastructure built in Oracle VirtualBox.

![Windows Server](https://img.shields.io/badge/Windows_Server-2025-0078D6?style=for-the-badge\&logo=windows)
![Active Directory](https://img.shields.io/badge/Active_Directory-AD_DS-blue?style=for-the-badge)
![DNS](https://img.shields.io/badge/DNS-Configured-success?style=for-the-badge)
![DHCP](https://img.shields.io/badge/DHCP-Configured-success?style=for-the-badge)
![Group Policy](https://img.shields.io/badge/Group_Policy-Configured-success?style=for-the-badge)
![VirtualBox](https://img.shields.io/badge/Oracle_VirtualBox-Lab-orange?style=for-the-badge)

---

## 📖 Overview

This repository documents the deployment of a Windows Server 2025 enterprise laboratory environment designed to simulate a small corporate network.

The primary objective of the project was to gain practical experience with enterprise Windows infrastructure by deploying and configuring a centralized Active Directory environment from scratch.

The lab includes a fully operational domain controller, automatic network configuration through DHCP, internal DNS name resolution, centralized authentication using Active Directory, Group Policy management, file sharing with NTFS permissions, and Windows 11 domain clients.

Although this environment was created as a learning project, every service was configured using practices commonly found in production environments.

---

## 🎯 Project Objectives

The following objectives were successfully completed during the implementation of the lab:

* Deploy Windows Server 2025 as a Domain Controller
* Configure Active Directory Domain Services (AD DS)
* Deploy an integrated DNS Server
* Configure a DHCP Server with automatic address assignment
* Join Windows 11 clients to the domain
* Create Organizational Units (OU)
* Create users and security groups
* Configure shared folders
* Apply NTFS permissions
* Configure Group Policy Objects (GPO)
* Map network drives automatically
* Validate communication between all virtual machines

---

# 🖥️ Lab Environment

| Component               | Value               |
| ----------------------- | ------------------- |
| Hypervisor              | Oracle VirtualBox   |
| Server Operating System | Windows Server 2025 |
| Client Operating System | Windows 11 Pro      |
| Domain Name             | KUZNIETSOV.local    |
| Domain Controller       | DC01                |
| Virtual Network         | Internal Network    |
| Number of Servers       | 1                   |
| Number of Clients       | 2                   |

---

# 🏗️ Infrastructure Architecture

The infrastructure consists of one Windows Server virtual machine acting as the Domain Controller and two Windows 11 client computers joined to the Active Directory domain.

The Domain Controller hosts several critical enterprise services:

* Active Directory Domain Services
* DNS Server
* DHCP Server
* File Server
* Group Policy Management

Both Windows 11 clients receive network configuration automatically from the DHCP server and authenticate against Active Directory.

---

# 🌐 Network Topology

```text
                           VirtualBox Internal Network
                                      │
        ┌─────────────────────────────┼─────────────────────────────┐
        │                             │                             │
        │                             │                             │
      DC01                        CLIENT01                     CLIENT02
Windows Server 2025             Windows 11                  Windows 11
Domain Controller               Domain Joined               Domain Joined
DNS Server                      DHCP Client                 DHCP Client
DHCP Server
File Server
```

> **TODO:** Replace this diagram with `images/topology.png` after creating a visual network diagram.

---

# 📡 Network Configuration

| Device            | Address                         |
| ----------------- | ------------------------------- |
| Domain Controller | 192.168.10.10                   |
| DNS Server        | 192.168.10.10                   |
| DHCP Server       | 192.168.10.10                   |
| Gateway           | 192.168.10.1                    |
| DHCP Scope        | 192.168.10.100 – 192.168.10.200 |

---

# ⚙️ Technologies

| Technology                       | Purpose                          |
| -------------------------------- | -------------------------------- |
| Windows Server 2025              | Domain Services                  |
| Windows 11 Pro                   | Client Operating System          |
| Active Directory Domain Services | Centralized Authentication       |
| DNS                              | Name Resolution                  |
| DHCP                             | Automatic IP Configuration       |
| File Server                      | Centralized Storage              |
| NTFS Permissions                 | Access Control                   |
| Group Policy                     | Centralized Administration       |
| PowerShell                       | Administration & Troubleshooting |
| Oracle VirtualBox                | Virtualization Platform          |

---

# ✨ Key Features

* Centralized user authentication
* Enterprise DNS infrastructure
* Automatic IP address assignment
* Group Policy administration
* Shared network folders
* NTFS permission management
* Organizational Units
* Security Groups
* Automatic drive mapping
* Login script support
* Windows 11 domain integration

---

# 📁 Repository Structure

```text
windows-server-enterprise-lab/
│
├── README.md
├── LICENSE
├── .gitignore
│
├── docs/
│   ├── 01-network-topology.md
│   ├── 02-active-directory.md
│   ├── 03-dns.md
│   ├── 04-dhcp.md
│   ├── 05-file-server.md
│   ├── 06-group-policy.md
│   └── 07-testing.md
│
├── images/
│
└── scripts/
    └── login.bat
```

---

# 📌 Documentation

Detailed configuration guides are available in the `docs` directory.

| Document               | Description                         |
| ---------------------- | ----------------------------------- |
| 01-network-topology.md | Network design and IP addressing    |
| 02-active-directory.md | Active Directory deployment         |
| 03-dns.md              | DNS configuration                   |
| 04-dhcp.md             | DHCP configuration                  |
| 05-file-server.md      | Shared folders and NTFS permissions |
| 06-group-policy.md     | Group Policy configuration          |
| 07-testing.md          | Validation and testing procedures   |

---

> Continue reading to learn how each infrastructure service was configured and validated.
