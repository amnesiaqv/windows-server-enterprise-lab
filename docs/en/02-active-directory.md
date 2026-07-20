# 🌍 Languages

- 🇬🇧 English (default)
- 🇷🇺 [Русский](docs/ru/02-active-directory.md)
- 🇺🇦 [Українська](docs/uk/02-active-directory.md)

# 🏛️ Active Directory Domain Services

### Overview

This document describes the deployment and configuration of **Active Directory Domain Services (AD DS)** within the Enterprise Active Directory Lab.

Active Directory serves as the central identity and access management platform for the laboratory environment. It provides centralized authentication, authorization, computer management, and Group Policy deployment for all domain-joined devices.

---

## Active Directory Deployment

The Active Directory Domain Services role was installed on the Windows Server 2025 virtual machine (**DC01**).

During deployment, the server was promoted to a Domain Controller, creating a new Active Directory forest and domain.

| Parameter               | Value               |
| ----------------------- | ------------------- |
| Domain Controller       | DC01                |
| Operating System        | Windows Server 2025 |
| Domain Name             | KUZNIETSOV.local    |
| Forest Functional Level | Windows Server 2025 (default)             |
| Domain Functional Level | Windows Server 2025 (default)             |

---

## Organizational Unit Structure

Organizational Units (OUs) were created to logically separate administrative objects and simplify management.

Example structure:

```text
KUZNIETSOV.local
│
└── Company
    ├── Users
    │   ├── IT
    │   ├── HR
    │   └── Finance
    │
    ├── Groups
    ├── Computers
    └── Servers
```

Separating resources into dedicated OUs makes it easier to delegate administration and apply Group Policy Objects to specific departments or object types.

---

## User Accounts

Domain user accounts were created for testing centralized authentication and access control.

Each user account was placed in the appropriate Organizational Unit and assigned to one or more security groups according to departmental requirements.

Example user attributes include:

* Username
* Display Name
* Department
* Password
* Group Membership

---

## Security Groups

Security groups were created to simplify permission management.

Instead of assigning permissions directly to individual users, permissions are granted to groups. Users receive access through group membership.

Typical departmental groups include:

* IT
* HR
* Finance

This approach follows Microsoft's recommended role-based access control (RBAC) practices.

---

## Domain Computers

Both Windows 11 workstations were successfully joined to the Active Directory domain.

| Computer |  Status  |
| -------- | :------: |
| CLIENT01 | ✅ Joined |
| CLIENT02 | ✅ Joined |

The computer accounts were automatically created in Active Directory and managed through Organizational Units and Group Policy.

---

## Authentication

Domain authentication is performed by the Domain Controller.

Benefits include:

* Centralized account management
* Single Sign-On (SSO)
* Password policy enforcement
* Kerberos-based authentication
* Centralized administration

Users no longer require separate local accounts on each workstation.

---

## Administrative Tools

The following Microsoft Management Consoles (MMCs) were used during deployment:

| Tool                                   | Purpose                      |
| -------------------------------------- | ---------------------------- |
| Active Directory Users and Computers   | User and computer management |
| Active Directory Administrative Center | Advanced administration      |
| Server Manager                         | Role management              |
| Group Policy Management                | Policy deployment            |

---

## Validation

The Active Directory deployment was validated using the following tests.

| Test                          | Expected Result | Status |
| ----------------------------- | --------------- | :----: |
| Domain Controller operational | Successful          |    ✅   |
| Domain created successfully   | Successful          |    ✅   |
| User authentication           | Successful          |    ✅   |
| Client joined to domain       | Successful          |    ✅   |
| Computer objects visible      | Successful          |    ✅   |
| Security groups created       | Successful          |    ✅   |

---

## Screenshots

### Active Directory Users and Computers

![Active Directory](images/active-directory/active-directory.png)

---

### Domain Users

![Users](images/active-directory/users.png)

---

### Security Groups

![Security Groups](images/active-directory/security-groups.png)

---

### Domain Joined Workstation

![Domain Joined](images/client/domain-joined.png)

---

## Summary

The Active Directory deployment provides centralized identity management for the laboratory environment.

Using Organizational Units, domain users, security groups, and domain-joined Windows 11 clients, the laboratory demonstrates enterprise identity management concepts and administrative practices commonly found in production Windows Server environments.
