# 🎫 Support Ticket ID: #INC-33751-NET

This document serves as the official IT support ticket resolution record for isolating a localized name resolution failure from a general internet connectivity outage on a corporate endpoint.

---

## 📊 Ticket Overview
* **Category:** New device administration
* **Priority:** Standard
* **Status:** Resolved

---

## 📊 Ticket Details

| Field | Ticket Information Details |
| :--- | :--- |
| **Ticket Reference** | #INC-33751-NET |
| **Assignment Group** | Tier 1 Endpoint Support |
| **Priority / Impact** | Medium / Individual |
| **Target Domain** | `lab.local` |
| **Infrastructure IP** | `10.0.0.220` (Domain Controller / Active DNS Server) |
| **Client Workstation** | WRK-W11-DIAG01 |

---

## 📋 Network Connectivity Profile Details

| Diagnostic Step Metric | Observed Verification Data Outputs |
| :--- | :--- |
| **Initial Reported Symptom** | Complete loss of application connectivity and internal/external webpage loading capabilities. |
| **Baseline Browser Status** | Confirmed initial web browsing functionality was healthy and resolving domains cleanly. |
| **Domain Ping Test Result** | Failed immediately with error: `Ping request could not find host` |
| **Raw IP Ping Test Result** | Successful. Clean ICMP replies returned instantly from public backbone `8.8.8.8` |
| **Root Cause Assessment** | Isolated to a localized DNS misconfiguration; physical internet/WAN interface routing is fully functional. |

---

## 🔍 Issue Reported
A user contacted the Tier 1 Help Desk reporting that they cannot load any corporate websites or internal cloud applications, suspecting a complete internet outage on their Windows 11 workstation (`WRK-W11-DIAG01`). As a Tier 1 Help Desk Technician, you must systematically diagnose the failure to determine if the issue is a localized DNS name resolution failure or a general internet connectivity loss.

---

## 🛠️ Actions Taken
1. **Verified Initial Browser Baseline:** Staged an initial baseline connection test by successfully opening a web browser on endpoint `WRK-W11-DIAG01` and navigating to `google.com` to verify proper initial DNS lookup function.

2. **Simulated Environment Fault:** Accessed client adapter properties and changed the manual Preferred DNS box to an unreachable dummy IP address (`10.99.99.99`).

3. **Executed DNS Resolution Diagnostics:** Attempted to ping public names (`ping google.com`) from Command Prompt, which failed immediately due to the system's inability to resolve the domain string.

4. **Executed Routing Verification Diagnostics:** Bypassed the name server database layer by pinging a raw public IP footprint directly (`ping 8.8.8.8`). The command yielded clean replies, proving external gateway route parsing was active.

5. **Conducted Direct Infrastructure Query:** Ran `nslookup google.com` to confirm that the server lookup request successfully timed out against the unreachable dummy IP address, confirming a pure name translation fault.

6. **Restored Production Adapter Values:** Navigated back to the Windows 11 Advanced Network settings tray and re-pointed the manual Preferred DNS box to the operational local domain controller path at `10.0.0.220`.

7. **Purged Host Resolution Cache Data:** Ran the administrative system command `ipconfig /flushdns` to wipe clean any stale or corrupted diagnostic entries held by the resolver stack.

8. **Performed Post-Repair Quality Checks:** Re-executed `nslookup google.com` and verified that the client successfully mapped and established live webpage connections.

---

## 🏁 Outcome
The network adapter analysis, layer-3 routing verification, layer-7 DNS isolation tests, parameter adjustments, and cache purge tasks were completed successfully.

---

## Network Interface Audit Summary
* **Physical Link / Gateway Status:** Confirmed operational throughout the entire incident timeline.
* **DNS Resolution Target Status:** Corrected and locked at corporate primary (`10.0.0.220`).
* **Endpoint Status:** Web and domain application traffic fully functional.

---

## 🔒 Ticket Closure Note
The localized fault assessment, command-line route verification isolation, and client DNS target corrections were completed and audited successfully on July 21, 2026. The workstation has been confirmed as functional, stable, and re-synchronized with core infrastructure name servers. This incident ticket record is officially closed.

***

**Documented By:** Ikenna Mennelik Ifedobi  
**Role:** Tier 1 Help Desk Technician  
**Date:** July 21, 2026  

