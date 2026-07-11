# Identity Management Lab: Active Directory User & Group Lifecycle Modification

Author: Ikenna Mennelik Ifedobi

Domain: Active Directory Administration

Windows 11 Client Machine + Windows Server 2022(Virtualised Bridged Network)

Completed July 2026

---

## 🎯 Objective
To establish a secure, audited process for managing user identity lifetimes. This includes creating account objects in dedicated Organizational Units (OUs), populating precise profile metadata, managing group access controls, and executing immediate account state changes (suspend/re-enable) based on official corporate requests.

---

### 🏢 Business Scenario 
* **Identity Provisioning Event (Date: July 10, 2026):** A new hire requires immediate environment setup inside the domain network. As a Tier 1 Help Desk Technician, you must create a new domain user object under a distinct departmental OU (`lab.local/Employees/Marketing`), populate their operational contact parameters, and map their profile to a specific departmental file share group.

* **HR Suspension Operations (Date: July 13, 2026):** Human Resources issues an urgent policy suspension notice regarding this user. To guarantee complete risk mitigation, you must instantly block interactive network logon paths.

* **Reinstatement Operations (Date: July 17, 2026):** Following a resolved internal HR inquiry, you receive authorization to restore full access. You must reverse the suspension, unlock the authentication profile, and ensure zero degradation of group-level network permissions.

---

## 📊 Environment & Management Tools

| Infrastructure Component | Management Tool / Resource | Operational Function in Lab |
| :--- | :--- | :--- |
| **Domain Controller (`10.0.0.220`)** | Active Directory Domain Services | Hosts the centralized `lab.local` database, handles network authentication requests, and processes user profile state changes. |
| **Windows Server 2022** | Active Directory Users and Computers (`dsa.msc`) | Desktop MMC administrative snap-in console used by Tier 1 support to create OUs, populate user fields, and modify access flags. |
| **Directory Structures** | Organizational Units (OUs) | Logical folder tree paths (`lab.local/Employees/Marketing`) used to isolate departments and manage access boundaries. |
| **Access Control Lists** | Security Group Allocations | Global and Domain Local groupings (e.g., `Marketing-Dept-GG`) used to map folder permissions based on departmental design. |
| **Target Endpoint** | Windows 11 Client Workstation | Managed network hardware asset used by Tier 1 technicians to verify live logins and test user account suspensions. |

---

## 🚀 Steps

### Part A: Provisioning & Group Allocation
1. **Launch Administration Console:** Run Active Directory Users and Computers (`dsa.msc`) on the Tier 1 workstation.

2. **Navigate to Parent Container:** Double-click the root domain structure and locate the parent Organizational Unit named `Employees`.

3. **Build Nested Departmental OU:** Right-click the `Employees` OU, select **New** > **Groups**, name it `Marketing`, and click OK.

4. **Configure the Marketing Group:** Set the Group Scope to Global and Group Type to Security.

5. **Initialize User Object:** Right-click the newly created `Marketing` Group, select **New** > **User**, and fill in the official first name, last name, and User Principal Name (UPN).

![Active Directory Creating New User Object inside Marketing Group](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/1934a6cc3a4293f01354567727398a67e8344a51/User%20Account%20Management/New%20User%20Object.png)

6. **Populate Profile Metadata Attributes:** Open the new user's **Properties** sheet and fill in the text fields across the **General**, **Organization**, and **Telephones** tabs (e.g., Office Phone, Job Title, Department, Manager name).

![Active Directory User Properties Profile Attribute Metadata Fields](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/1934a6cc3a4293f01354567727398a67e8344a51/User%20Account%20Management/General_Properties.png)
![Active Directory User Properties Profile Attribute Metadata Fields](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/1934a6cc3a4293f01354567727398a67e8344a51/User%20Account%20Management/Organization_Properties.png)


7. **Assign Security Group Allocation:** Navigate to the **Member Of** properties tab, click **Add...**, select the designated network access group (e.g., `Marketing-Dept-GG`), and click apply.

![Active Directory User Properties Group Membership Assignment](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/1934a6cc3a4293f01354567727398a67e8344a51/User%20Account%20Management/Marketing%20Group%20Membership.png)

---

### Part B: HR Suspension Handling
1. **Process Suspension Mandate:** Navigate to the nested path `lab.local/Employees/Marketing` and locate the target user account.

2. **Execute Access Revocation:** Right-click the target user record, click **Disable Account**, and acknowledge the status lock warning dialog box.

![Active Directory Users and Computers Disabling Marketing User Profile](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/1934a6cc3a4293f01354567727398a67e8344a51/User%20Account%20Management/Disabled.png)

---

### Part C: Reinstatement Handling
1. **Process Reinstatement Mandate:** Search the `lab.local/Employees/Marketing` hierarchy to identify the currently suspended account profile.

2. **Execute Access Restoration:** Right-click the user object and click **Enable Account**.

![Active Directory Objects Tree Showing Disabled Object Overlay](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/1934a6cc3a4293f01354567727398a67e8344a51/User%20Account%20Management/Enabled.png)

3. **Verify Security Identifiers:** Inspect the **Member Of** panel to ensure department-level security groups remained unaltered throughout the suspension period.

---

## 🔍 Verification & Auditing

### Provisioning & Attributes Check
* Review the User Properties sheet inside ADUC to ensure that telephone, title, and manager lookup chains link back properly.

### Suspension State Check
* Confirm the account icon displays a black downward-pointing arrow, validating that active authentication endpoints will reject the user's password.

### Reinstatement State Check
* Verify that the downward arrow overlay clears from the user's icon. Test interactive workstation connectivity using the employee's existing profile parameters.

***

**Maintained By:** Ikenna Mennelik Ifedobi  
**Role:** Tier 1 Help Desk Technician  

