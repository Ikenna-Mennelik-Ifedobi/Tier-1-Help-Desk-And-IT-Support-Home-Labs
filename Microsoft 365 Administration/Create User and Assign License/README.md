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

![Microsoft 365 Admin Center User Creation Wizard Screen](images/01-m365-create-user.png)

4. Create a temporary password and check the box for **"Require this user to change their password when they first sign in"**. Click Next.
5. In the Product Licenses step, check the box to assign a **Microsoft 365 Business Standard** license to this account. Click Next and click Finish.

![Microsoft 365 Product Licensing Grid Assigning Business Standard Subscription to User](images/02-m365-assign-license.png)

6. Confirm the user appears in Active Users.

![Active Users Confirmation](images/03-m365-license-inventory.png)

---

## 🔍 Verification & Auditing

### End-User Initial Login Verification
1. Open an incognito browser window and go to the Office login portal: `https://office.com`.
2. Enter Marcus Vance's cloud credentials (`mvance@://onmicrosoft.com`) and the temporary password.
3. Verify that the login sequence successfully triggers a mandatory password change screen.

![Office Portal Endpoint Login View Confirming Initial Password Reset Prompt](images/04-user-login-verify.png)

***

**Maintained By:** Ikenna Mennelik Ifedobi  
**Role:** Tier 1 Help Desk Technician  

