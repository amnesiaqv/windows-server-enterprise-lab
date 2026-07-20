# 🌍 Languages

- 🇬🇧 English (default)
- 🇷🇺 [Русский](docs/ru/06-group-policy.md)
- 🇺🇦 [Українська](docs/uk/06-group-policy.md)

# 🛡️ Group Policy Configuration

## Overview

This document describes the configuration and deployment of Group Policy Objects (GPOs) within the Enterprise Active Directory Lab.

Group Policy is one of the core management technologies in Microsoft Active Directory. It enables administrators to centrally configure operating system settings, enforce security policies, automate administrative tasks, and standardize user environments across all domain-joined computers.

---

## Group Policy Management

Group Policy Objects were created and managed using the **Group Policy Management Console (GPMC)**.

| Component               | Value                   |
| ----------------------- | ----------------------- |
| Management Tool         | Group Policy Management |
| Domain                  | KUZNIETSOV.local        |
| Domain Controller       | DC01                    |
| Client Operating System | Windows 11 Pro          |

The policies were linked to the appropriate Organizational Units (OUs) to ensure they were applied only to the intended users or computers.

---

## Implemented Group Policy Objects

The following Group Policy Objects were successfully configured within the laboratory environment.

| Group Policy          | Description                                                |
| --------------------- | ---------------------------------------------------------- |
| Set Wallpaper         | Configures a corporate desktop wallpaper for domain users  |
| Hide Local C: Drive   | Hides the local C: drive in File Explorer                  |
| Map Network Drives    | Automatically maps shared network drives at user logon     |
| Disable CMD           | Prevents users from launching the Command Prompt           |
| Disable Control Panel | Restricts access to the Control Panel and Windows Settings |
| Disable Registry Tools| Blocks access to the Windows Registry Editor               |
| Disable USB           | Prevents the use of removable USB storage devices          |
| Audit Policy          | Enables auditing of selected Windows security events       |
| Login Script          | Executes a logon script during user authentication         |

These policies demonstrate centralized administration, workstation hardening, and user environment management using Active Directory.

---

## Drive Mapping

Network drives were automatically mapped for domain users during the logon process.

Example network path:

```text
\\DC01\Public
```

The drive mapping provides users with immediate access to shared resources without requiring manual configuration.

---

## Logon Script

A logon script was deployed through Group Policy to automate user configuration.

Example logon script:

```bat
net use P: \\DC01\Public
```

The script automatically connects the shared network folder each time a domain user signs in.

---

## Administrative Purpose

The configured Group Policy Objects demonstrate common administrative, security, and configuration management practices used in enterprise Windows environments.

The implemented policies provide the following functionality:

* Standardized desktop appearance using a corporate wallpaper
* Protection of system resources by hiding the system drive
* Automatic mapping of shared network drives
* Restriction of administrative tools such as Command Prompt and Registry Editor
* Prevention of unauthorized system configuration changes
* Control over removable USB storage devices
* Collection of security events through Windows auditing
* Automated user configuration using a logon script

These policies improve security, simplify administration, and ensure consistent workstation configuration across the domain.

---

## Group Policy Processing

After joining the Active Directory domain and signing in with a domain account, Windows clients automatically receive the configured Group Policy Objects.

Policies are processed during:

* Computer startup
* User logon
* Background policy refresh
* Manual policy update using `gpupdate`

---

## Validation

The Group Policy deployment was successfully validated using the following tests.

| Test                          | Expected Result | Status |
| ----------------------------- | --------------- | :----: |
| GPOs linked successfully      | Passed          |    ✅   |
| Wallpaper applied             | Passed          |    ✅   |
| C: drive hidden               | Passed          |    ✅   |
| Network drive mapped          | Passed          |    ✅   |
| Command Prompt blocked        | Passed          |    ✅   |
| Control Panel disabled        | Passed          |    ✅   |
| Registry Editor blocked       | Passed          |    ✅   |
| USB storage restricted        | Passed          |    ✅   |
| Audit Policy enabled          | Passed          |    ✅   |
| Logon script executed         | Passed          |    ✅   |
| Policies applied successfully | Passed          |    ✅   |

---

## Verification Commands

### Force Group Policy Update

```cmd
gpupdate /force
```

### Display Applied Policies

```cmd
gpresult /r
```

---

## Screenshots

### Group Policy Management Console

![Group Policy Management](images/group-policy/gpo.png)

---

### GPResult Verification

![GPResult](images/testing/gpresult.png)

---

## Summary

The Group Policy implementation demonstrates centralized administration of Windows workstations within an Active Directory environment.

The deployed policies automate user configuration, improve endpoint security, restrict unauthorized administrative actions, and simplify access to shared resources.

This implementation reflects common enterprise administration practices used to standardize client computers, improve endpoint security, and simplify centralized management in Windows Server environments.
