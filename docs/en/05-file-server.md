# 🌍 Languages

- 🇬🇧 English (default)
- 🇷🇺 [Русский](docs/ru/05-file-server.md)
- 🇺🇦 [Українська](docs/uk/05-file-server.md)

# 📁 File Server Configuration

## Overview

This document describes the configuration of the File Server role within the Enterprise Active Directory Lab.

The Domain Controller hosts centralized shared folders that are accessible to authorized domain users. Access to shared resources is controlled through a combination of Share Permissions, NTFS Permissions, and Active Directory security groups.

---

## File Server

The Windows Server 2025 Domain Controller also functions as the File Server for the laboratory environment.

| Parameter        | Value               |
| ---------------- | ------------------- |
| Server           | DC01                |
| Operating System | Windows Server 2025 |
| File System      | NTFS                |
| Access Method    | SMB File Sharing    |

Shared folders provide centralized storage for users connected to the Active Directory domain.

---

## Shared Folders

Several shared folders were created to simulate departmental resources.

| Share       | Purpose                   |
| ----------- | ------------------------- |
| Public      | Shared company data       |
| IT          | IT department files       |
| HR          | Human Resources documents |
| Finance     | Finance files             |

---

## Share Permissions

Share permissions control network-level access to shared folders, while NTFS permissions control access to files and folders on the local file system.

Permissions were assigned using Active Directory security groups rather than individual user accounts.

This approach simplifies administration and follows Microsoft's recommended best practices.

---

## NTFS Permissions

NTFS permissions provide file system security and control access to files and folders stored on the server.

NTFS permissions were assigned primarily to Active Directory security groups rather than individual user accounts, following Microsoft's recommended best practices for scalable access management.

Using security groups makes permission management more scalable and easier to maintain.

---

## Access Control

Access to shared resources follows the principle of least privilege.

Users are granted only the permissions required to perform their job responsibilities.

Examples include:

* Read
* Modify
* Full Control

The effective permissions depend on the combination of Share Permissions and NTFS Permissions.

---

## Drive Mapping

A network drive was automatically mapped for domain users through Group Policy or a logon script.

This allows users to access shared folders without manually creating network connections.

Example:

```text
\\DC01\Public
```

---

## Validation

The File Server configuration was validated using the following tests.

| Test                           | Expected Result | Status |
| ------------------------------ | --------------- | :----: |
| Shared folders created         | Passed          |    ✅   |
| Share Permissions configured   | Passed          |    ✅   |
| NTFS Permissions configured    | Passed          |    ✅   |
| Network drive accessible       | Passed          |    ✅   |
| Domain users can access shares | Passed          |    ✅   |

---

## Screenshots

### Shared Folders

![Shared Folders](images/file-server/file-server.png)

---

### NTFS Permissions

![NTFS Permissions](images/file-server/ntfs-permissions.png)

---

### Share Permissions

![Share Permissions](images/file-server/share-permissions.png)

---

### Mapped Network Drive

![Mapped Drive](images/client/mapped-drive.png)

---

## Summary

The File Server provides centralized storage for the Enterprise Active Directory Lab.

By combining SMB file sharing, NTFS permissions, Share Permissions, and Active Directory security groups, the environment demonstrates secure and scalable file access management commonly used in enterprise Windows infrastructures.
