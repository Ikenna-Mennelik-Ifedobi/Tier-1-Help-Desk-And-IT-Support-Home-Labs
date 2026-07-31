# 🎫 Support Ticket ID: #INC-66194-SEC

This document serves as the official IT support ticket resolution record for deploying a secure network file repository, mapping share links, and validating access permissions against security group boundaries.

---

## 📊 Ticket Overview
* **Category:** New device administration
* **Priority:** Standard
* **Status:** Resolved

---

## 📊 Ticket Details

| Field | Ticket Information Details |
| :--- | :--- |
| **Ticket Reference** | #INC-66194-SEC |
| **Assignment Group** | Tier 1 Endpoint Support |
| **Priority / Impact** | Medium / Individual |
| **Target Domain** | `lab.local` |
| **Infrastructure IP** | `10.0.0.220` (Domain Controller / File Share Server) |
| **Client Workstation** | WRK-W11-SHARE05 |

---

## 📋 File Share Security Authorization Log

| User Profile Checked | Active Security Group Member | Network Drive Mapping Status | Observed Folder Access Behavior |
| :--- | :--- | :--- | :--- |
| **Sarah Jenkins** | `Finance-Dept-GG` (Yes) | Mapped Successfully (**`Z:`**) | **SUCCESS** (Persistent access functional across reboots) |
| **Marcus Vance** | None (Initial Check: No) | Connection Rejected | **FAILED** (Blocked by automated Access Denied prompt) |
| **Marcus Vance** | `Finance-Dept-GG` (Post-Fix: Yes)| Connected Cleanly (`\\10.0.0.220\`) | **SUCCESS** (Full access restored following user logoff/logon) |

---

## 🔍 Issue Reported
The Finance department contacts the IT Help Desk regarding an operational requirements change that requires a new restricted data storage repository on the network. Concurrently, an inbound support ticket is escalated detailing an end-user connection failure to a corporate file resource. As the Tier 1 Help Desk Technician on duty, you must fulfill the active infrastructure request and clear the technical roadblocks preventing standard employee productivity.

---

## 🛠️ Actions Taken
1. **Staged Active Directory Security Group:** Initialized the Active Directory Users and Computers console (`dsa.msc`), navigated to the `lab.local/Employees` OU, and created a new global security group named `Finance-Dept-GG`.

2. **Provisioned Initial Group Nesting:** Queried the directory ledger for user account Sarah Jenkins and successfully appended her profile to the new `Finance-Dept-GG` object.

3. **Provisioned Server-Side Storage Folder:** Connected to the core domain architecture at `10.0.0.220` and initialized a storage directory named `Finance_Data` inside the `C:\` partition volume.

4. **Configured Advanced Network Share Parameters:** Adjusted folder sharing settings to set baseline Share properties to Change/Read parameters for the network path.

5. **Enforced Restricted NTFS Access Control Lists:** Disabled inheritance controls on the hosting file system directory layer and purged generic user privileges from the registry ledger.

6. **Appended Scoped Security Group Permissions:** Granted explicit full Modify, Write, and Read access rights targeting the departmental group `Finance-Dept-GG`.

7. **Mapped Persistent Network Resource to Client:** Logged into workstation asset `WRK-W11-SHARE05` using an authorized profile, mapped the repository as drive letter **`Z:`**, and explicitly flagged the **"Reconnect at sign-in"** parameter to guarantee link persistence.

8. **Executed Baseline Environment Initialization:** Instructed the authorized user to perform a complete system logoff and logon cycle to safely commit the persistent drive parameter to the local shell environment.

9. **Executed Positive Access Control Testing:** Verified the authorized user could successfully create, edit, and append file changes to document clean read/write synchronization.

10. **Executed Negative Access Control Validation:** Swapped terminal profiles to an unapproved user account lacking the proper group assignment parameters, and documented the resulting operating system access-denied block.

11. **Resolved Unauthorized Access via Security Group Expansion:** Logged into the directory management dashboard, opened the properties panel for `Finance-Dept-GG`, and added the restricted user account object directly into the group membership directory ledger.

12. **Forced Client Kerberos Token Refresh:** Instructed the end-user to execute a full system logoff and logon cycle on workstation `WRK-W11-SHARE05` to clear out their current session context and pull down an updated security token populated with the new security group SID from the domain controller.

13. **Validated Final Resolution Success:** Re-tested folder navigation using the newly updated user profile, confirming seamless access to all directory files with zero errors generated.

---

## 🏁 Outcome
The network share provisioning, NTFS file system security clamping, persistent client network drive allocation mapping, dual-user boundary testing sweeps, and administrative access resolution steps were completed successfully.

---

## Storage Architecture Security Audit Summary
* **Access Control Status:** Active Enforcement verified (Group membership mandatory for path navigation).
* **Drive Persistence:** Confirmed active ("Reconnect at sign-in" rule verified).
* **Endpoint Status:** Workstation asset successfully communicating with backend storage nodes under strict compliance limits.

---

## 🔒 Ticket Closure Note
The network folder share infrastructure deployment, NTFS permissions mapping adjustments, persistent drive mappings, and final group-level access resolutions were completed and audited successfully on July 31, 2026. Data boundaries are operational, verified, and locked against unapproved penetration paths. This support case request sheet is officially marked as resolved and closed.

***

**Documented By:** Ikenna Mennelik Ifedobi  
**Role:** Tier 1 Help Desk Technician  
**Date:** July 31, 2026  
