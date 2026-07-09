# 🎫 Support Ticket ID: #INC-88421-DSJ

This document serves as the official IT support ticket resolution record for joining an end-user asset to the corporate infrastructure.

## 📊 Ticket Overview
* **Category:** New device - Domain Join
* **Priority:** Standard
* **Status:** Resolved

## 📊 Ticket Details

| Field | Ticket Information Details |
| :--- | :--- |
| **Ticket Reference** | #INC-88421-DSJ |
| **Assignment Group** | Tier 1 Endpoint Support |
| **Priority / Impact** | Medium / Individual |
| **Target Domain** | `lab.local` |
| **Infrastructure IP** | `10.0.0.220` (Domain Controller / DNS) |
| **Asset Hostname** | *[Domain]* |

---

## 🔍 Issue Reported
A newly onboarded employee is unable to sign in to their corporate laptop using their company network credentials. The newly provisioned Windows 11 workstation is currently unmanaged and operating within a standalone Workgroup configuration. The device lacks connection to the centralized identity infrastructure, preventing corporate authentication and profile synchronization.

---

## 🛠️ Actions Taken
1. **Verified Physical/Wireless Connectivity:** Confirmed the client workstation was securely patched into the local office network subnet.
2. **Accessed Local Network Adapter Properties:** Opened Windows 11 Advanced Network Settings to modify the active primary interface properties.
3. **Assigned Static IPv4 DNS Settings:** Changed DNS assignment to Manual and configured Preferred DNS to `10.0.0.220` to point directly to the domain controller.
4. **Flushed Client DNS Cache:** Executed `ipconfig /flushdns` in Command Prompt to clear out stale cached name records.
5. **Executed Hostname Resolution Tests:** Ran `nslookup lab.local` to verify the internal DNS server correctly maps the domain.
6. **Executed ICMP Reachability Tests:** Ran `ping lab.local` to ensure stable, low-latency network communication with the domain controller.
7. **Initiated Windows System Properties:** Navigated to System About and opened the Advanced System Settings panel.
8. **Modified System Membership Settings:** Clicked the Computer Name Change button and changed membership from Workgroup to Domain.
9. **Targeted Corporate Infrastructure Path:** Entered the exact corporate domain name `lab.local` into the target field.
10. **Authenticated Domain Security Prompt:** Inputted authorized domain administrator credentials when intercepted by the Windows Security prompt.
11. **Acknowledged Success Greeting:** Validated the standard *"Welcome to the lab.local domain"* dialog alert box popup.
12. **Committed Machine System Reboot:** Closed out open windows and initiated a complete computer restart to initialize the active domain profile.

---

## 🏁 Outcome
The Windows 11 workstation successfully established a secure trust relationship with the `lab.local` network directory. Following the required system reboot, the user profile login screen was updated to accept external domain credentials.

### Initial User Authentication Check
1. At the Windows 11 startup lock screen, **Other user** was selected in the lower-left section.
2. The user successfully authenticated and initialized their profile using their corporate credentials:
   * **Format:** `username@lab.local` or `LAB\username`
   * **Password:** *[The User's Assigned Corporate Password]*

---

## 🔒 Ticket Closure Note
The asset is securely registered within Active Directory and fully joined to the network path. The user has successfully logged into the machine with their corporate account credentials, verifying that network authentication functions as expected. No further network routing errors or credential mismatches were noted. This request is marked as resolved and closed.

***

**Documented By:** Ikenna Mennelik Ifedobi  
**Role:** IT Support Technician  
**Date:** July 9, 2026  

