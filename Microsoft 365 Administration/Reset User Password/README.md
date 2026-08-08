# Microsoft 365 Credential Management Lab

## 🎯 Objective
To securely reset a cloud user's password and configure mandatory credential rotation upon their next system logon.

---

## 📊 Environment & Administration Tools

| Tool Panel | Target URL | Operational Function |
| :--- | :--- | :--- |
| **Microsoft 365 Admin Center** | `://microsoft.com` | Web dashboard used to manage active identities, modify account security flags, and clear credentials. |

---

## 🚀 Standard Operating Procedures

### Part A: Administrative Password Reset
1. Log into the administrative web portal dashboard at `https://://microsoft.com`.
2. Expand the left navigation menu and click **Users** > **Active users**.
3. Locate the target employee profile name (**Marcus Vance**) from the directory listing and hover over their row.
4. Click the **Reset password** key icon shortcut that appears next to their name (or click the account name and select **Reset password** from the top action bar).

![Microsoft 365 Active Users Grid Launching the Reset Password Action Prompt](images/01-m365-password-reset-click.png)

5. In the password reset properties flyout panel, configure the following deployment settings:
   * Select **Automatically create a password** to let the system generate a secure, compliant temporary string.
   * Check the strict security box for **"Require this user to change their password when they first sign in"**.
   * Check the box for **"Email the sign-in info to me"** to securely deliver the temporary string to your administrative inbox.
6. Click the master **Reset password** button at the bottom of the pane.

![Microsoft 365 Password Configuration Flyout Pane Selecting Reset Parameters](images/02-m365-password-reset-save.png)

---

## 🔍 Verification & Auditing

### Credential Reset State Verification
1. Review the confirmation panel that appears on the right side of the screen once the task completes.
2. Verify that the interface explicitly displays a **"Password reset"** success heading and outlines the auto-generated temporary password string. This confirms that the old account hash has been successfully overwritten in the cloud database.

![Microsoft 365 Admin Center Confirmation Dialogue Disclosing Temporary Password Details](images/03-m365-password-reset-confirm.png)

***

**Documented By:** Ikenna Mennelik Ifedobi  
**Role:** Tier 1 Help Desk Technician  

