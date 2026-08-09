# Microsoft 365 Tenant Sharing Restrictions & OneDrive Permission Remediation Lab

## 🎯 Objective
To restrict tenant-wide external sharing settings within the SharePoint Admin Center, audit a specific user's OneDrive directory, remove unauthorized external access paths, and down-scope active internal rights to view-only status.

---

## 📊 Environment & Administration Tools

| Tool Panel | Target URL / Path | Operational Function |
| :--- | :--- | :--- |
| **Microsoft 365 Admin Center** | `://microsoft.com` | Primary dashboard used to locate active user files and cross-launch specialized admin centers. |
| **SharePoint Admin Center** | Admin Centers > SharePoint | Centralized management console used to enforce tenant-wide security and external data sharing limits. |
| **OneDrive for Business** | Active Users > OneDrive Properties | Managed storage workspace of a specific user account used to audit active folder access permissions. |

---

## 🚀 Standard Operating Procedures

### Part A: Enforcing Tenant-Wide Sharing Restrictions
1. Log into the administrative web portal dashboard at `https://://microsoft.com`.
2. Expand the left navigation menu, click **Admin centers**, and select **SharePoint**.
3. In the SharePoint admin center left pane, navigate to **Policies** > **Sharing**.
4. Review the organization-wide external sharing parameters (set to *Anyone* by default).
5. Drag the **OneDrive** slider control downward to change the permission level to **Only people in your organization** to completely block file leakage outside the company tenant, and click **Save**.

![SharePoint Admin Center Policies Sharing Panel Enforcing Tenant Wide External Restrictions](images/01-sharepoint-sharing-lockdown.png)

---

### Part B: Auditing and Remediating User OneDrive Permissions
1. Return to the primary **Microsoft 365 Admin Center** tab or dashboard window layout.
2. Navigate to **Users** > **Active users** and click on the target employee's account name to expand their properties flyout panel.
3. Switch to the **OneDrive** properties tab row and click the link for **Open** under *Get access to files*.

![Microsoft M365 Active Users Panel Accessing and Opening a Target User OneDrive Directory Link](images/02-admin-open-user-onedrive.png)

4. Inside the managed user's file layout, locate the specific shared target folder, right-click its name row, and select **Manage access**.
5. In the Manage Access right-hand panel view, locate the unauthorized external user entry row, click the options dropdown next to their profile, and click the **X** icon (or **Stop sharing**) to drop their access path instantly.
6. Locate the remaining internal user profiles, click their active permissions dropdown arrow row, change the setting parameter value from *Can edit* to **Can view**, and close the panel box.

![OneDrive Managed Directory Interface Revoking External Links and Downgrading Internal Access Fields](images/03-onedrive-remediation-complete.png)

---

## 🔍 Verification & Auditing

### Perimeter and Item Access Verification
1. Open an incognito browser window, log into the tenant dashboard, and attempt to share a local file layout object externally to verify that the option for *Anyone* is now greyed out and unselectable.
2. Re-open the targeted user folder's **Manage access** sheet grid inside the administrator session to confirm that the unauthorized external account record row is completely purged from the registry ledger.

![Office Shared Asset View Confirming Option for External Recipient Addresses is Deactivated](images/04-tenant-perimeter-verification.png)

***

**Maintained By:** Ikenna Mennelik Ifedobi  
**Role:** Tier 1 Help Desk Technician  
**Date:** August 9, 2026  

