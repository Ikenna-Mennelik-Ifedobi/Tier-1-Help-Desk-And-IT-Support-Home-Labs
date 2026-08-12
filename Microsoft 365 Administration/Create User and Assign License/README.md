# Microsoft 365 Cloud Administration Lab

This document outlines the operational steps to manage an enterprise Microsoft 365 tenant, provision user accounts, and assign cloud licenses.

## 🎯 Objective
To create a new cloud user and assign their productivity subscription license.

---

## 📊 Environment & Administration Tools

| Tool Panel | Target URL | Operational Function |
| :--- | :--- | :--- |
| **Microsoft 365 Admin Center** | `://microsoft.com` | Web dashboard used to add users and assign licenses. |

---

## 🚀 Standard Operating Procedures

### Part A: Cloud User Creation & License Assignment
1. Log into the administrative web portal dashboard at `https://://microsoft.com`.
2. Expand the left menu and click **Users** > **Active users**.
3. Click the **Add a user** button and input the employee profile details:
   * **First Name:** Marcus
   * **Last Name:** Vance
   * **Display Name:** Marcus Vance
   * **Username:** `mvance`

![Microsoft 365 Admin Center User Creation Wizard Screen](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/5f76aa003c8bf2dc03ec626f01ecf08d496db221/Microsoft%20365%20Administration/Create%20User%20and%20Assign%20License/Screenshots/User_Creation.png)

4. Create a temporary password and check the box for **"Require this user to change their password when they first sign in"**. Click Next.
5. In the Product Licenses step, check the box to assign a **Microsoft 365 Business Standard** license to this account. Click Next and click Finish.

![Microsoft 365 Product Licensing Grid Assigning Business Standard Subscription to User](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/5f76aa003c8bf2dc03ec626f01ecf08d496db221/Microsoft%20365%20Administration/Create%20User%20and%20Assign%20License/Screenshots/Assign_License.png)

6. Confirm the user appears in Active Users.

![Active Users Confirmation](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/5f76aa003c8bf2dc03ec626f01ecf08d496db221/Microsoft%20365%20Administration/Create%20User%20and%20Assign%20License/Screenshots/Active_Users.png)

---

## 🔍 Verification & Auditing

### End-User Initial Login Verification
1. Open an incognito browser window and go to the Office login portal: `https://office.com`.
2. Enter Marcus Vance's cloud credentials (`mvance@://onmicrosoft.com`) and the temporary password.
3. Verify that the login sequence successfully triggers a mandatory password change screen.

![Office Portal Endpoint Login View Confirming Initial Password Reset Prompt](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/5f76aa003c8bf2dc03ec626f01ecf08d496db221/Microsoft%20365%20Administration/Create%20User%20and%20Assign%20License/Screenshots/Password_Reset.png)

***

**Maintained By:** Ikenna Mennelik Ifedobi  
**Role:** Tier 1 Help Desk Technician  

