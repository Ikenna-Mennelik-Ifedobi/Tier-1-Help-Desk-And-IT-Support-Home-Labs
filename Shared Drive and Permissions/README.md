# Windows Server Infrastructure: File Share Deployment and Access Control Remediation

## 🎯 Objective
To provision a secure departmental network file share, isolate access via overlapping Share and NTFS permissions, and resolve an unauthorized access-denied restriction block for an unmapped user account by updating security group memberships and refreshing client session tokens.

---

## 🏢 Business Scenario
**File Share Access Incident (Date: July 31, 2026):** The Finance department contacts the IT Help Desk regarding an operational requirements change that requires a new restricted data storage repository on the network. Concurrently, an inbound support ticket is escalated detailing an end-user connection failure to a corporate file resource. As the Tier 1 Help Desk Technician on duty, you must fulfill the active infrastructure request and clear the technical roadblocks preventing standard employee productivity.

---

## 📊 Environment & Management Tools

| Infrastructure Component | Management Tool / Resource | Operational Function |
| :--- | :--- | :--- |
| **Domain Controller (`10.0.0.220`)** | File and Storage Services | Centralized host where network folder repositories are created and shared across the local area network. |
| **Help Desk Workstation** | Active Directory Users and Computers (`dsa.msc`) | Console used to manage departmental security groups and audit user account memberships. |
| **Access Control Lists (ACL)** | Share & NTFS Permissions | Overlapping security layers used to enforce the Principle of Least Privilege (PoLP) on file systems. |
| **Target Endpoint** | Windows 11 Client Workstation (VM) | The managed virtual machine endpoint used to map network drives and perform interactive user access tests. |

---



**Maintained By:** Ikenna Mennelik Ifedobi  
**Role:** Tier 1 Help Desk Technician  
