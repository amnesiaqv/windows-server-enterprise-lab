# 🌍 Languages

- 🇬🇧 English (default)
- 🇷🇺 [Русский](https://raw.githubusercontent.com/amnesiaqv/windows-server-enterprise-lab/main/docs/ru/01-network-topology.md)
- 🇺🇦 [Українська](https://raw.githubusercontent.com/amnesiaqv/windows-server-enterprise-lab/main/docs/uk/01-network-topology.md)

# 🌐 Network Topology

## Overview

This document describes the network architecture implemented for the **Enterprise Active Directory Lab**. The environment simulates a small enterprise infrastructure where a single Windows Server provides centralized network services to multiple domain-joined client computers.

The entire laboratory was deployed using **Oracle VirtualBox** and isolated within an **Internal Network**, allowing all virtual machines to communicate without exposing services to the host network.

---

## Network Diagram

![Network Topology](https://raw.githubusercontent.com/amnesiaqv/windows-server-enterprise-lab/main/images/infrastructure/topology.png)

---

## Infrastructure Components

| Hostname | Operating System    | Primary Role       |
| -------- | ------------------- | ------------------ |
| DC01     | Windows Server 2025 | Domain Controller (DC)  |
| CLIENT01 | Windows 11 Pro      | Domain Workstation |
| CLIENT02 | Windows 11 Pro      | Domain Workstation |

The Domain Controller hosts all core infrastructure services required for the laboratory:

* Active Directory Domain Services (AD DS)
* DNS Server
* DHCP Server
* File Server
* Group Policy Management

The client computers are joined to the Active Directory domain and receive centralized configuration from the server.

---

## Network Configuration

| Parameter            | Value                           |
| -------------------- | ------------------------------- |
| Hypervisor           | Oracle VirtualBox               |
| Network Type         | Internal Network                |
| Domain               | KUZNIETSOV.local                |
| Domain Controller    | DC01                            |
| Server Address       | 192.168.10.10                   |
| DHCP Scope           | 192.168.10.100 – 192.168.10.200 |
| Default Gateway      | N/A                             |
| Preferred DNS Server | 192.168.10.10                   |

Clients obtain their IPv4 configuration automatically from the DHCP service running on the Domain Controller.

---

## Network Services

### Active Directory

Provides centralized authentication, authorization, and directory services for all domain-joined computers and users.

---

### DNS

The DNS server resolves hostnames within the Active Directory domain and stores integrated DNS records for domain services and client computers.

---

### DHCP

The DHCP server automatically assigns IPv4 addresses, DNS settings, and other network parameters to client workstations, eliminating the need for manual configuration.

---

### File Services

The Domain Controller hosts shared folders protected by NTFS and Share permissions. Access is controlled using Active Directory security groups.

---

### Group Policy

Group Policy Objects (GPOs) are applied to domain users and computers to centrally manage operating system settings and automate administrative tasks.

---

## Network Validation

The following tests were performed to verify proper operation of the network.

| Test                            | Expected Result                          | Status |
| ------------------------------- | ---------------------------------------- | :----: |
| Domain Join                     | Client successfully joined to the domain |    ✅   |
| DHCP Lease                      | Client receives IP automatically         |    ✅   |
| DNS Resolution                  | Hostnames resolve correctly              |    ✅   |
| ICMP Connectivity               | Clients communicate with the server      |    ✅   |
| Active Directory Authentication | Domain logon succeeds                    |    ✅   |
| Group Policy Processing         | Policies applied successfully            |    ✅   |
| Shared Folder Access            | Network shares accessible                |    ✅   |

---

## Verification Commands

The following commands were used during deployment and testing.

### Display IP Configuration

```cmd
ipconfig /all
```

### Test Connectivity

```cmd
ping DC01
```

### Verify DNS Resolution

```cmd
nslookup DC01
```

### Verify Applied Group Policies

```cmd
gpresult /r
```

---

## Validation Screenshots

### Network Configuration

![IP Configuration](https://raw.githubusercontent.com/amnesiaqv/windows-server-enterprise-lab/main/images/testing/ipconfig.png)

---

### Connectivity Test

![Ping Test](https://raw.githubusercontent.com/amnesiaqv/windows-server-enterprise-lab/main/images/testing/ping.png)

---

### DNS Resolution

![NSLookup](https://raw.githubusercontent.com/amnesiaqv/windows-server-enterprise-lab/main/images/testing/nslookup.png)

---

### Group Policy Processing

![GPResult](https://raw.githubusercontent.com/amnesiaqv/windows-server-enterprise-lab/main/images/testing/gpresult.png)

---

## Summary

The network topology successfully provides a centralized Windows Server infrastructure supporting authentication, DNS name resolution, DHCP address allocation, Group Policy management, and secure file sharing.

The environment closely reflects the architecture commonly deployed in small and medium-sized enterprise networks and serves as a practical platform for learning Windows Server administration, enterprise networking, and Active Directory management using industry-standard Microsoft technologies.
