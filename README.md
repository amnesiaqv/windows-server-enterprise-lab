# 🏢 Enterprise Active Directory Lab

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
| Domain Name             | corp.local    |
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

# 🏛️ Infrastructure Design

The laboratory environment simulates a centralized Windows Server infrastructure commonly found in small and medium-sized enterprises (SMEs). The deployment focuses on identity management, network services, centralized administration, and secure file sharing.

A single Windows Server 2025 virtual machine acts as the core infrastructure server and hosts multiple critical services. Two Windows 11 Pro virtual machines are joined to the Active Directory domain and function as managed client workstations.

The entire environment is isolated within an Oracle VirtualBox internal network, allowing enterprise technologies to be tested without requiring physical hardware or impacting the host operating system.

---

## Infrastructure Components

| Hostname | Operating System    | Role                                      |
| -------- | ------------------- | ----------------------------------------- |
| DC01     | Windows Server 2025 | Domain Controller, DNS, DHCP, File Server |
| CLIENT01 | Windows 11 Pro      | Domain Workstation                        |
| CLIENT02 | Windows 11 Pro      | Domain Workstation                        |

---

# 🖧 Network Architecture

```text
                    Oracle VirtualBox
                   Internal Network
                          │
        ┌─────────────────┼─────────────────┐
        │                 │                 │
        │                 │                 │
      DC01            CLIENT01         CLIENT02
        │
        ├── Active Directory
        ├── DNS
        ├── DHCP
        ├── File Services
        └── Group Policy
```

---

## IP Addressing

| Device            | Address                         |
| ----------------- | ------------------------------- |
| Domain Controller | 192.168.10.10                   |
| DNS Server        | 192.168.10.10                   |
| DHCP Server       | 192.168.10.10                   |
| Default Gateway   | 192.168.10.1                    |
| DHCP Scope        | 192.168.10.100 - 192.168.10.200 |

Clients automatically receive:

* IP Address
* Subnet Mask
* Default Gateway
* Preferred DNS Server
* Lease Time

using the DHCP service running on the Domain Controller.

---

# 🏢 Active Directory Structure

The Active Directory environment was organized using Organizational Units (OUs) to simplify administration and Group Policy deployment.

```text
Domain
│
└── Company
    │
    ├── Users
    │     ├── IT
    │     ├── HR
    │     └── Finance
    │
    ├── Groups
    │
    ├── Computers
    │
    └── Servers
```

This structure follows common enterprise administration practices by separating users, computers, and administrative objects into dedicated Organizational Units.

---

# 👥 User and Group Management

User accounts were created inside their respective Organizational Units and assigned to security groups according to their department.

Security groups are used to manage permissions instead of assigning permissions directly to users. This approach simplifies administration and follows Microsoft's recommended access control model.

Example departmental groups include:

| Group   | Purpose            |
| ------- | ------------------ |
| IT      | IT Department      |
| HR      | Human Resources    |
| Finance | Finance Department |

---

# 🔑 Authentication

Both Windows 11 clients were successfully joined to the Active Directory domain.

Domain authentication provides centralized identity management, allowing users to authenticate against the Domain Controller instead of maintaining separate local accounts on each workstation.

Benefits include:

* Centralized account management
* Single sign-on (SSO)
* Centralized password policies
* Group Policy enforcement
* Simplified administration

---

# 📸 Screenshots

The following screenshots should be added to the repository:

* Active Directory Users and Computers
* Organizational Units
* User Accounts
* Security Groups
* Domain Join
* Computer Objects

Example:

```markdown
![Active Directory](images/active-directory.png)

![Organizational Units](images/ou-structure.png)

![Domain Computers](images/domain-computers.png)
```

---

> The next section documents the deployment and validation of the DNS and DHCP infrastructure services.
