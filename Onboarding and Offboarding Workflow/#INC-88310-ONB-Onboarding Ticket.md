# 🎫 Support Ticket ID: #INC-88310-ONB

This document serves as the official IT support ticket resolution record for executing an enterprise new hire identity provisioning and endpoint workspace deployment request.

---

## 📊 Ticket Overview
* **Category:** New device administration
* **Priority:** Standard
* **Status:** Resolved

---

## 📊 Ticket Details

| Field | Ticket Information Details |
| :--- | :--- |
| **Ticket Reference** | #INC-88310-ONB |
| **Assignment Group** | Tier 1 Endpoint Support |
| **Priority / Impact** | Medium / Individual |
| **Target Domain** | `lab.local` |
| **Infrastructure IP** | `10.0.0.220` (Domain Controller / ADUC) |
| **Operation Type** | Employee Identity Provisioning & Workspace Setup |

---

## 📋 Employee Onboarding Profile Details

| Provisioning Field | User Profile Specification Data |
| :--- | :--- |
| **Name of Employee** | Marcus Vance |
| **Department** | Corporate Finance |
| **Manager Name** | Robert Vance |
| **Start Date** | August 3, 2026 |
| **Required Apps** | Google Chrome, Microsoft Teams |
| **Hardware** | Dell Corporate Laptop (Asset Tag: WRK-W11-FIN05) |

---

## 🔍 Issue Reported
Human Resources has submitted an authorized onboarding request for a new employee, Marcus Vance, who is joining the Corporate Finance division on **August 3, 2026**. The Tier 1 Help Desk Technician must log the intake criteria, provision a new network user identity profile under the default Active Directory Users container, establish appropriate department group assignments, complete a secure workstation domain join, deploy required software packages, set up corporate email routing, and configure a persistent network file drive layout.

---

## 🛠️ Actions Taken
1. **Audited Inbound Ticket Parameters:** Logged and cross-checked the incoming HR payload data inside a localized **Notepad** template window box, mapping user parameters, hardware tags, and applications.

2. **Provisioned Directory Identity Account:** Created the user account profile `mvance` inside the default container path `lab.local/Users` using Active Directory Users and Computers (`dsa.msc`).

3. **Staged Department Security Group:** Provisioned a global security group named `Finance` under `lab.local/Users` and nested the new `mvance` account object directly into the membership registry tab.

4. **Executed Client Workstation Domain Join:** Adjusted the Windows 11 workstation DNS assignments manually to target the domain controller at `10.0.0.220` and securely joined the virtual machine to the `lab.local` namespace.

5. **Deployed Workplace Productivity Apps:** Completed the forced initial login password reset prompt on the client terminal and deployed **Google Chrome** and Microsoft Teams**
**.

6. **Configured Corporate Communication Access:** Initialized the Exchange ActiveSync mail utility framework to authenticate the corporate UPN (`mvance@lab.local`) and successfully synchronize user mailbox folders.

7. **Mounted Persistent Network Share Link:** Configured a secure server folder named `FinanceShare` on the server disk. Mapped the UNC path `\\10.0.0.220\FinanceShare` to the client machine as drive letter **`Z:`** with the persistent connection flag checked, and performed a user logoff/logon sequence to lock the mount.

8. **Issued Handover Summary Note:** Generated a day-one technical onboarding brief detailing device identity details and credential rules for delivery to the new employee.

---

## 🏁 Outcome
The multi-tier user identity provisioning, global group structure creation, client device domain join, software deployment, email envelope setup, and persistent drive mapping workflows were completed successfully.

---

## Active Directory Configuration Audit Summary
* **Account UPN:** `mvance@lab.local`
* **Account Status:** Active / Enabled (Initial forced password rotation completed)
* **Access Group Permissions:** Nested inside `Finance` group / Persistent `Z:` drive online and read-write verified.

---

## 🔒 Ticket Closure Note
All network identity configurations and endpoint desktop configurations have been successfully initialized and verified against primary domain databases on August 3, 2026. The new hire workspace channels are live, verified, and operational. This case file is officially closed.

***

**Documented By:** Ikenna Mennelik Ifedobi  
**Role:** Tier 1 Help Desk Technician  
**Date:** August 3, 2026  
