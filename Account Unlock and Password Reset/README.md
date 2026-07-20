# Active Directory Group Policy Configuration & Account Lockout Resolution Lab

## 🎯 Objective
To configure automated brute-force defense parameters via Group Policy, trigger an enforced security lockout on a client machine, and perform identity-verified account unlocking and credential resets within Active Directory Users and Computers (ADUC).

---

## Business Scenario
 **User Lockout Incident (Date: July 14, 2026):** Marcus Vance, the Business Strategist in the Marketing division, returns to the office after an extended leave. He fails to recall his current network profile credentials and accidentally inputs an incorrect password string three consecutive times on his Windows 11 virtual machine. The domain security parameters trigger instantly, locking out his profile. Marcus contacts the IT Help Desk via telephone requesting immediate assistance. As a Tier 1 Help Desk Technician, you must verify his employee identity parameters, clear the Active Directory account restriction, and issue a secured temporary password so he can log back in and resume work.

---

## Environment & Management Tools

| Infrastructure Component | Management Tool / Resource | Operational Function in Lab |
| :--- | :--- | :--- |
| **Domain Controller (`10.0.0.220`)** | Group Policy Management Console (`gpmc.msc`) | Administrative snap-in used to configure domain-wide account lockout thresholds and password safety parameters. |
| **Help Desk Workstation** | Active Directory Users and Computers (`dsa.msc`) | Management GUI used by Tier 1 support to locate the target user, clear the security restriction, and apply resets. |
| **Directory Structures** | Organizational Units (OUs) | Logical folder tree paths (`lab.local/Employees/Marketing`) where the target user profile object resides. |
| **Target Endpoint** | Windows 11 Client Workstation (VM) | Managed operating system environment used to manually input bad passwords and verify policy execution. |

---

## 🚀 Standard Operating Procedures

### Part A: Group Policy Enforcement
1. **Launch Group Policy Console:** Log into the Domain Controller and open the Group Policy Management Console (`gpmc.msc`).

2. **Edit Domain Policy Object:** Expand the forest tree, right-click the **Default Domain Policy**, and select **Edit** to open the management editor.

3. **Navigate to Lockout Threshold:** Browse to **Computer Configuration** > **Policies** > **Windows Settings** > **Security Settings** > **Account Policies** > **Account Lockout Policy**.

4. **Configure Access Limits:** Double-click **Account lockout threshold**, modify the value field to **3 invalid logon attempts**, and apply changes.

![Group Policy Management Editor Configuring Account Lockout Threshold to 3 Attempts](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/60b61960f106133cef54274effd42ff87c02cba2/Account%20Unlock%20and%20Password%20Reset/Password_Attempt_Limit.png)

5. **Force Security Policy Replication:** Open an administrative Command Prompt or PowerShell terminal and execute the infrastructure command:
   ```cmd
   gpupdate /force
   ```
![gpupdate command to enforce security policy](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/60b61960f106133cef54274effd42ff87c02cba2/Account%20Unlock%20and%20Password%20Reset/gpupdate.png)
---

### Part B: Lockout Simulation (Windows 11 VM)
1. **Navigate to Client Terminal:** Access the console interface of the domain-joined Windows 11 client virtual machine.

2. **Simulate Brute-Force Inputs:** Select employee **Marcus Vance** (`mvance@lab.local`) at the logon screen.

3. **Trigger Automated Account Lockout:** Intentionally input an incorrect password string three consecutive times.

4. **Verify Endpoint Enforcement:** Confirm that the Windows Security architecture halts further attempts and displays the explicit error message: *"The referenced account is currently locked out and may not be logged on to."*

![Account is locked](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/60b61960f106133cef54274effd42ff87c02cba2/Account%20Unlock%20and%20Password%20Reset/Account_Locked.png)

---

### Part C: Help Desk Account Remediation
1. **Open Directory Administration:** Launch Active Directory Users and Computers (`dsa.msc`) on the management terminal.

2. **Locate Target Profile Record:** Navigate into the nested container directory path `lab.local/Employees/Marketing` and double-click user **Marcus Vance**.

3. **Clear Security Restrictions:** Select the **Account** property tab, check the box next to **"Unlock account. This account is currently locked out on this Active Directory Domain Controller"**, and click **Apply**.

![Active Directory Account Properties Checking the Unlock Account Status Box](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/60b61960f106133cef54274effd42ff87c02cba2/Account%20Unlock%20and%20Password%20Reset/Account_Unlocked.png)

4. **Initialize Credential Reset Action:** Right-click the user object icon within the main pane and select **Reset Password...**.

5. **Stage Temporary Password:** Type a complex temporary password into the authentication fields.

6. **Enforce Next Logon Password Change:** Check the option box for **"User must change password at next logon"** and select **OK** to restore full user capability.

![Active Directory Reset Password Dialog box Enforcing Next Logon Parameter](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/60b61960f106133cef54274effd42ff87c02cba2/Account%20Unlock%20and%20Password%20Reset/Temporary_Password.png)

---

## 🔍 Verification & Auditing

### Group Policy Verification
* Run `net accounts` inside a client terminal window to confirm that the local machine recognizes the 3-attempt account lockout threshold from the domain controller.

### Operational Access Restoration
* Verify that the black downward warning symbol is removed from Marcus Vance's object profile icon inside the ADUC panel.
* Log in to the Windows 11 virtual machine using the staged credentials and verify that the interface seamlessly forces a new personal password configuration.

![Password change for windows 11 client machine](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/60b61960f106133cef54274effd42ff87c02cba2/Account%20Unlock%20and%20Password%20Reset/Password_Change.png)

***

**Maintained By:** Ikenna Mennelik Ifedobi  
**Role:** Tier 1 Help Desk Technician  

