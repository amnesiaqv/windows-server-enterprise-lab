# 🌍 Languages

- 🇬🇧 English (default)
- 🇷🇺 [Русский](docs/ru/04-dhcp.md)
- 🇺🇦 [Українська](docs/uk/04-dhcp.md)

# 📡 DHCP Server Configuration

## Overview

This document describes the deployment and configuration of the Dynamic Host Configuration Protocol (DHCP) service within the Enterprise Active Directory Lab.

The DHCP server automatically assigns IPv4 addresses, DNS settings, and other network parameters to domain-joined client computers, simplifying network administration and ensuring consistent configuration.

---

## DHCP Server Role

The DHCP Server role was installed on the Domain Controller (DC01).

| Parameter        | Value                          |
| ---------------- | ------------------------------ |
| DHCP Server      | DC01                           |
| Operating System | Windows Server 2025            |
| Authorization    | Authorized in Active Directory |
| Address Family   | IPv4                           |

The DHCP server was authorized in Active Directory before serving IP addresses to clients.

---

## DHCP Scope

A single IPv4 scope was configured for the internal laboratory network.

| Setting              | Value            |
| -------------------- | ---------------- |
| Scope Name           | Internal Network |
| Network              | 192.168.10.0/24  |
| Start Address        | 192.168.10.100   |
| End Address          | 192.168.10.200   |
| Subnet Mask          | 255.255.255.0    |
| Default Gateway      | N/A              |
| Preferred DNS Server | 192.168.10.10    |

The scope provides automatic address assignment for all Windows 11 client computers.

---

## DHCP Options

The following DHCP options were configured.

| Option                | Value            |
| --------------------- | ---------------- |
| DNS Server (006)      | 192.168.10.10    |
| DNS Domain Name (015) | KUZNIETSOV.local |

These options ensure that clients receive the required network settings during the DHCP lease process.

---

## Address Leases

After joining the domain and renewing their network configuration, both client computers successfully obtained IP addresses from the DHCP server.

| Computer | Address Source |
| -------- | -------------- |
| CLIENT01 | DHCP           |
| CLIENT02 | DHCP           |

The active leases are visible in the DHCP management console under **Address Leases**.

---

## DHCP Lease Process

Each client follows the standard DHCP process:

1. DHCP Discover
2. DHCP Offer
3. DHCP Request
4. DHCP Acknowledgement (ACK)

After the lease is granted, the client automatically receives:

* IPv4 Address
* Subnet Mask
* Preferred DNS Server
* DNS Suffix

---

## Validation

The DHCP deployment was validated using the following tests.

| Test                         | Expected Result | Status |
| ---------------------------- | --------------- | :----: |
| DHCP Server operational      | Passed          |    ✅   |
| DHCP Scope active            | Passed          |    ✅   |
| Server authorized            | Passed          |    ✅   |
| Clients receive IP addresses | Passed          |    ✅   |
| DHCP Options applied         | Passed          |    ✅   |
| Address leases visible       | Passed          |    ✅   |

---

## Verification Commands

The following commands were used during testing.

### Display Client Configuration

```cmd
ipconfig /all
```

### Renew DHCP Lease

```cmd
ipconfig /renew
```

### Release Current Lease

```cmd
ipconfig /release
```

---

## Screenshots

### DHCP Manager

![DHCP Manager](../images/dhcp/dhcp-manager.png)

---

### Address Leases

![DHCP Leases](../images/dhcp/dhcp-leases.png)

---

### Client IP Configuration

![IP Configuration](../images/testing/ipconfig.png)

---

## Summary

The DHCP Server successfully provides automatic IPv4 configuration for all Windows 11 domain clients.

Centralized address management reduces administrative effort, minimizes configuration errors, and ensures consistent network settings across the laboratory environment. All clients successfully received valid DHCP leases, DNS settings, and domain configuration from the authorized DHCP server.
