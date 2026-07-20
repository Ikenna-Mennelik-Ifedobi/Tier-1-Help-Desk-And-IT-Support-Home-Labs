# 🎫 Support Ticket ID: #INC-22481-GPO

This document serves as the official IT support ticket resolution record for processing an inbound user account lockout assistance request and executing administrative domain restoration protocols.

---

## 📊 Ticket Overview
* **Category:** New device administration
* **Priority:** Standard
* **Status:** Resolved

---

## 📊 Ticket Details

| Field | Ticket Information Details |
| :--- | :--- |
| **Ticket Reference** | #INC-22481-GPO |
| **Assignment Group** | Tier 1 Endpoint Support |
| **Priority / Impact** | Medium / Individual |
| **Target Domain** | `lab.local` |
| **Infrastructure IP** | `10.0.0.220` (Domain Controller / ADUC) |
| **Operation Type** | Inbound Support Intake, Account Lockout Removal, and Credential Renewal |

---

## 📋 Impacted Employee Profile Details

| Property Field | User Profile Specification Data |
| :--- | :--- |
| **Name of Employee** | Marcus Vance |
| **Organizational Unit Path** | `lab.local/Employees/Marketing` |
| **Department / Job Title** | Marketing / Creative Director |
| **Manager Name** | Sarah Jenkins |
| **Virtual Machine Hostname** | MKT-VM-CLIENT11 |

---

## 🔍 Issue Reported
User Marcus Vance (Creative Director, Marketing Division) contacted the Tier 1 Help Desk via telephone on **July 14, 2026**. The user stated that they could not log into their assigned corporate Windows 11 virtual machine (`MKT-VM-CLIENT11`) after typing an incorrect credential string 3 consecutive times. The endpoint successfully blocked authentication access and displayed an account lockout alert box. The user requested immediate technical support to restore access to their workspace.

---

## 🛠️ Actions Taken
1. **Completed Inbound Identity Verification:** Authenticated the remote caller by cross-checking corporate employee ID metrics and department fields to ensure request legitimacy.

2. **Configured Pre-Requisite Lab Policy (Internal Staging):** Verified that the domain infrastructure was enforcing the lockout rule via an initialized `gpupdate /force` update sequence.

3. **Located Target Record in ADUC Console:** Logged into the directory management platform, browsed to nested container `lab.local/Employees/Marketing`, and opened Marcus Vance's database sheet.

4. **Verified Lockout Status Flag:** Confirmed that the Active Directory account flag was reading as locked out due to the consecutive password failures generated at the client system.

5. **Cleared Account Restraints:** Manually removed the security lockout condition by selecting the **Unlock account** checkbox within the Account properties tab and hitting Apply.

6. **Executed Security Password Reset:** Opened the administrative reset dialogue window, assigned a complex temporary corporate entry string, and configured the profile to force a mandatory personal password rotation upon the next network connection handshake.

7. **Monitored Initial User Login:** Instructed the user to log back in at the Windows 11 terminal using the new temporary password, verifying that the OS successfully forced Marcus to choose a new, private password structure.

---

## 🏁 Outcome
The user assistance request, account status unlock, and temporary credential renewal actions were completed successfully. Marcus Vance successfully authenticated past the client terminal interface.

---

## Active Directory Compliance Audit Summary
* **Marcus Vance Account Status:** Unlocked / Enabled / Restored
* **Credential Standing:** Temporary string applied (Forced change on logon successfully cleared by user)
* **Workstation Status:** Desktop space operational on asset `MKT-VM-CLIENT11`

---

## 🔒 Ticket Closure Note
The user intake call, directory lockout removal, and credential resets were successfully executed and logged on July 14, 2026. The employee confirmed complete restoration of work processes and successfully established a unique private password string at the client terminal prompt. This support instance is officially marked as resolved and closed.

***

**Documented By:** Ikenna Mennelik Ifedobi  
**Role:** Tier 1 Help Desk Technician  
**Date:** July 14, 2026  
