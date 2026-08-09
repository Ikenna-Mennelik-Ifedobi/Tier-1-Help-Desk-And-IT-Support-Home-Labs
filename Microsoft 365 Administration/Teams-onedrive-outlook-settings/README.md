# Microsoft 365 Enterprise Architecture: Tenant-Wide Core Service Configurations Lab

## 🎯 Objective
To configure global enterprise collaboration policies by implementing centralized mailbox safety controls in Exchange, enforcing storage quota boundaries in OneDrive, and customizing meeting feature baselines within the Teams Admin Center.

---

## 📊 Environment & Administration Tools

| Governance Console | Target URL Panel Path | Organizational Control Scope |
| :--- | :--- | :--- |
| **Exchange Admin Center** | `://microsoft.com` | Manages mail flow routing, anti-spam policies, global address lists, and organizational malware filters. |
| **SharePoint Admin Center** | `://sharepoint.com` > Settings | Governs tenant-wide default storage limits, data sync states, and file retention parameters for OneDrive. |
| **Teams Admin Center** | `://microsoft.com` | Controls organization-wide meeting features, messaging policies, guest user access, and device registration. |

---

## 🚀 Standard Operating Procedures

### Part A: Managing Enterprise Mail Policies (Exchange/Outlook)
1. Log into the administrative web portal dashboard at `https://microsoft.com`.
2. Expand the left menu, select **Admin centers**, and click **Exchange**.
3. In the Exchange admin center left pane, navigate to **Mail flow** > **Rules**.
4. Review or create organization-wide transport rules (e.g., automatically appending a standardized disclaimer or warning banner to all inbound external emails).
5. Navigate to **Protection** > **Malware filter** to inspect the global inbound message inspection rules that drop malicious executable files before they hit end-user inboxes.

![Exchange Admin Center Mail Flow Dashboard Displaying Global Transport Rules](images/01-exchange-mail-flow.png)

---

### Part B: Enforcing Cloud Storage Thresholds (OneDrive)
1. Return to the primary browser control layout, browse to the **SharePoint Admin Center**, and select **Settings**.
2. Click on the **OneDrive storage limit** parameter block configuration row.
3. Review the default storage allocation metrics (set to maximum allowances by default).
4. Modify the tenant-wide default value field down to a lower tier configuration (e.g., restricting standard accounts to **1024 GB** to enforce data storage cost optimization compliance baselines) and click **Save**.

![SharePoint Admin Center Settings Window Modifying Global OneDrive Storage Quota Limits](images/02-sharepoint-onedrive-limits.png)

---

### Part C: Controlling Organization-Wide Collaboration Baselines (Microsoft Teams)
1. Open a new web browser tab, navigate directly to the **Microsoft Teams admin center** (`https://://microsoft.com`), and log in.
2. In the left navigation menu layout, expand the tree path and click **Meetings** > **Meeting policies**.
3. Select the **Global (Org-wide default)** policy configuration record row to edit the master runtime rules for all tenant employees.
4. Scroll down to the *Audio & video* security settings block layout, toggle the parameters for features like **"Allow IP video"** or screen sharing configurations to match company security standards, and click **Save**.

![Teams Admin Center Meeting Policies Screen Enforcing Org-Wide Video and Sharing Baseline Rules](images/03-teams-meeting-policies.png)

---

## 🔍 Verification & Auditing

### Enterprise Policy Propagation Check
1. Open an end-user session on a client machine endpoint, log into Outlook, and verify that test emails originating from external addresses correctly display the enforced corporate transport warning banner.
2. Open the user profile account workspace inside the OneDrive client app and inspect the storage space parameters to confirm the system partition ceiling accurately matches the newly configured 1024 GB database quota boundary.

![OneDrive Client Interface File Account Status Page Verifying Enforced Storage Limit Compliance](images/04-onedrive-client-quota-verify.png)

***

**Maintained By:** Ikenna Mennelik Ifedobi  
**Role:** Tier 1 Help Desk Technician  
**Date:** August 9, 2026  

