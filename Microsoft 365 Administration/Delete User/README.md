# Microsoft 365 User De-provisioning Lab

## 🎯 Objective
To enforce an immediate sign-in block on a cloud user account, verify access restriction, and delete the account object from the active directory.

---

## 📊 Environment & Administration Tools

| Tool Panel | Target URL | Operational Function |
| :--- | :--- | :--- |
| **Microsoft 365 Admin Center** | `://microsoft.com` | Web dashboard used to manage sign-in states, delete profiles, and re-allocate software seats. |

---

## 🚀 Standard Operating Procedures

### Part A: Enforcing the Sign-In Block
1. Log into the administrative web portal dashboard at `https://://microsoft.com`.
2. Expand the left navigation menu and click **Users** > **Active users**.
3. Click on the target employee profile name (**Marcus Vance**) from the directory listing to open their account properties flyout panel.
4. Click the **Block sign-in** link item row located directly under their display name.

![Microsoft 365 Active Users Profile Panel Initializing the Block Sign In Action Link](images/01-m365-block-signin-click.png)

5. Check the box for **"Block this user from signing in"** and click **Save changes**.

![Microsoft 365 Sign In Restrictions Panel Committing the Account Access Block](images/02-m365-block-signin-save.png)

6. Close the flyout pane and return to the **Active users** menu. Look at the status indicators to confirm that the row item for Marcus Vance explicitly reads **"Sign-in blocked"**, verifying access has been successfully revoked.

![Microsoft 365 Active Users Grid View Confirming Enforced Sign In Blocked Status on Row](images/03-m365-block-signin-confirm.png)

---

### Part B: Cloud Account De-provisioning
1. While still in the **Active users** view, click the three vertical dots next to Marcus Vance's row and select **Delete user** from the options dropdown menu.
2. In the deletion properties panel, check the appropriate operational clean-up boxes:
   * Review and uncheck product license selections to free up subscription seat pools.
   * Configure email delegation or OneDrive file access handovers if requested.
3. Click the master **Delete user** button at the bottom of the page to commit the profile purge.

![Microsoft 365 Account Deletion Configuration Pane Finalizing Data Retention Options](images/04-m365-delete-user-confirm.png)

---

## 🔍 Verification & Auditing

### Deleted Object Lifecycle Verification
1. Navigate to **Users** > **Deleted users** within the left navigation panel menu layout.
2. Search for and locate user account entry **Marcus Vance**.
3. Verify that the identity object appears in this restricted ledger grid index, confirming that the account is securely staged in the 30-day corporate soft-delete retention window.

![Microsoft 365 Deleted Users System Ledger Confirming Successful Soft Delete Retention Standing](images/05-m365-deleted-users-verify.png)

***

**Maintained By:** Ikenna Mennelik Ifedobi  
**Role:** Tier 1 Help Desk Technician  
