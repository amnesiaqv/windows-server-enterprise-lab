# 🌍 Languages

- 🇬🇧 English (default)
- 🇷🇺 [Русский](../ru/03-dns.md)
- 🇺🇦 [Українська](../uk/03-dns.md)

# 🌐 DNS Server Configuration

## Overview

This document describes the deployment and configuration of the Domain Name System (DNS) service within the Enterprise Active Directory Lab.

The DNS server is integrated with Active Directory Domain Services (AD DS) and provides name resolution for all domain-joined computers. It enables clients to locate the Domain Controller and other network resources by hostname instead of IP address.

---

## DNS Server Role

The DNS Server role was installed on the Domain Controller (DC01) during the Active Directory deployment.

| Parameter        | Value                       |
| ---------------- | --------------------------- |
| DNS Server       | DC01                        |
| Operating System | Windows Server 2025         |
| DNS Zone Type    | Active Directory-Integrated |
| Domain Name      | KUZNIETSOV.local            |

he DNS service stores DNS records within Active Directory and replicates them automatically between Domain Controllers, providing secure and centralized name resolution.

---

## DNS Zone Configuration

A Forward Lookup Zone was automatically created during the installation of Active Directory.

| Zone             | Type                |
| ---------------- | ------------------- |
| KUZNIETSOV.local | Forward Lookup Zone |

The zone was automatically configured as an Active Directory-integrated zone during Domain Controller promotion.

---

## Host Records

The following host (A) records were successfully registered in the DNS zone.

| Hostname | Purpose            |
| -------- | ------------------ |
| DC01     | Domain Controller  |
| CLIENT01 | Domain Workstation |
| CLIENT02 | Domain Workstation |

Dynamic DNS updates allow client computers to automatically register and update their DNS records after joining the domain.

---

## DNS Resolution Process

The DNS service performs the following functions:

* Resolves hostnames to IP addresses
* Supports Active Directory authentication
* Locates Domain Controllers
* Enables communication between domain members
* Maintains dynamic DNS records

Without a properly configured DNS server, domain logon and many Active Directory services would not function correctly.

---

## Validation

The DNS configuration was verified using the following tests.

| Test                         | Expected Result | Status |
| ---------------------------- | --------------- | :----: |
| DNS Server operational       | Passed          |    ✅   |
| Forward Lookup Zone created  | Passed          |    ✅   |
| Host records available       | Passed          |    ✅   |
| Domain Controller resolution | Passed          |    ✅   |
| Client name resolution       | Passed          |    ✅   |
| Dynamic DNS registration     | Passed          |    ✅   |

---

## Verification Commands

The following commands were used to validate DNS functionality.

### Resolve the Domain Controller

```cmd
nslookup DC01
```

### Resolve Client Computers

```cmd
nslookup CLIENT01
```

```cmd
nslookup CLIENT02
```

### Verify Network Configuration

```cmd
ipconfig /all
```

The preferred DNS server on each client points to the Domain Controller.

---

## Screenshots

### DNS Manager

![DNS Manager](https://raw.githubusercontent.com/amnesiaqv/windows-server-enterprise-lab/main/images/dns/dns-manager.png)

---

### IP Configuration

![IP Configuration](https://raw.githubusercontent.com/amnesiaqv/windows-server-enterprise-lab/main/images/testing/ipconfig.png)

---

### DNS Resolution

![NSLookup](https://raw.githubusercontent.com/amnesiaqv/windows-server-enterprise-lab/main/images/testing/nslookup.png)

---

## Summary

The DNS Server was successfully integrated with Active Directory Domain Services and provides centralized name resolution for the laboratory environment.

Correct DNS configuration enables reliable Active Directory authentication, service discovery, client communication, and overall domain functionality.
