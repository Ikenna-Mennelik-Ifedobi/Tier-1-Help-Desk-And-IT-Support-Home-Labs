# Windows Server Infrastructure: File Share Deployment and Access Control Remediation

Author: Ikenna Mennelik Ifedobi

Domain: Active Directory Administration File Sharing and Permissions

Environment: Windows Server 2022 + Windows 11 Client Machine(Virtualized-Bridged Network)

Completed: August 2026

---

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

## 🚀 Standard Operating Procedures

### Part A: Infrastructure Provisioning & Security Staging
1. **Create Shared Folder on Server:** Log into the Domain Controller, open **File Explorer**, navigate to the `C:\` drive volume, right-click the blank directory space, select **New** > **Folder**, and name it `FinanceShare`.

2. **Provision Directory Users and Security Group:** Open **Active Directory Users and Computers** (`dsa.msc`), navigate to your target Organizational Unit (`lab.local/Employees`), and execute the following staging operations:
   * Right-click, select **New** > **Group**, and create a global security group named `Finance`.
   * Ensure user accounts exist for both employees (Sarah Jenkins and Marcus Vance).

3. **Establish Initial Group Nesting Matrix:** Double-click the `Finance` security group object, navigate to the **Members** tab, and click **Add...**. Populate the field to add **Sarah Jenkins** to the group registry. Do **not** add the other user (**Marcus Vance**), leaving him unmapped to isolate access boundaries.

![Active Directory Management Console Provisioning the Finance Security Group Matrix](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/09b8f3a837e2b46ec2ee2f3f0127fd3b912039a6/Shared%20Drive%20and%20Permissions/Screenshots/Add_Sarah_Jenkins_to_Finance.png)

4. **Configure Share Permissions:** Right-click the `FinanceShare` folder on your server disk, navigate to **Properties** > **Sharing** > **Advanced Sharing**, check **Share this folder**, and click **Permissions**. Click **Add...**, type in the `Finance` security group name, and check the boxes to assign them **Change** and **Read** permissions.

![Windows Server Properties Window Appending Share Level Control Permissions](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/09b8f3a837e2b46ec2ee2f3f0127fd3b912039a6/Shared%20Drive%20and%20Permissions/Screenshots/Configure_Share_Permissions.png)

5. **Configure NTFS Permissions:** Switch to the folder's **Security** tab, click **Advanced** Click **Add**, select the `Finance` security group object, and grant them explicit **Modify, Read & execute, List folder contents, Read, and Write** permissions. Leave the rest of the existing list parameters untouched.

![Windows Server Advanced Security settings Layering NTFS ACL Group Bounds](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/09b8f3a837e2b46ec2ee2f3f0127fd3b912039a6/Shared%20Drive%20and%20Permissions/Screenshots/Configure_NTFS_Permissions.png)

---

### Part B: Client-Side Mapping & Access Validation Testing
1. **Map Network Drive on Client Machine:** Log into your domain-joined Windows 11 client virtual machine using the authorized account credentials (**Sarah Jenkins**). Open **File Explorer**, right-click **This PC**, select **Map network drive...**, choose drive letter **`Z:`**, and target the server UNC path: `\\10.0.0.220\FinanceShare`. Ensure **"Reconnect at sign-in"** is enabled, click Finish, and complete a system **log off and log back in** to commit the persistent mapping.

![Windows 11 Client Terminal Mapping Persistent Network Path to Z Drive](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/09b8f3a837e2b46ec2ee2f3f0127fd3b912039a6/Shared%20Drive%20and%20Permissions/Screenshots/Map_to_Zdrive.png)

2. **Test Access of Authorized User:** Open the mapped **`Z:`** drive partition window as the authorized user. Right-click the empty folder canvas directory, select **New** > **Text Document**, append validation string metrics inside the file, and click save to confirm functional write authorization.

![Windows 11 File Explorer Confirming Successful Text File Write Generation](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/8bbd8a9fc6d0018327a84eaca2cce06d9ba44e61/Shared%20Drive%20and%20Permissions/Screenshots/Test_Document_from_Zdrive.png)

3. **Test Access of Unauthorized User:** Log out of the Windows 11 client machine session and sign back in using the unmapped user profile credentials (**Marcus Vance**). Open File Explorer, navigate to the folder URL address bar, and manually attempt to enter the directory path: `\\10.0.0.220\FinanceShare`.

4. **Document Access Denied Isolation Intercept:** Observe that the endpoint security subsystem catches the handshake rejection and generates the explicit verification alert box: *"Windows cannot access \\10.0.0.220\FinanceShare. You do not have permission to access..."*

![Windows Security Subsystem Intercepting Connection and Displaying Access Denied Warning](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/8bbd8a9fc6d0018327a84eaca2cce06d9ba44e61/Shared%20Drive%20and%20Permissions/Screenshots/Access_Denied.png)

---

### Part C: Access Remediation & Final Verification
1. **Resolve the Access Issue:** Return to your Tier 1 support workstation terminal console and access **Active Directory Users and Computers** (`dsa.msc`). Search for the `Finance` security group object properties sheet, click the **Members** tab, select **Add...**, input the unmapped employee profile name (**Marcus Vance**), and click apply to append him to the resource list.

![Active Directory Management Tool Appending Blocked User to the Finance Group List](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/8bbd8a9fc6d0018327a84eaca2cce06d9ba44e61/Shared%20Drive%20and%20Permissions/Screenshots/Update_Finance_Group_List.png)

2. **Log Off and Log Back In as Newly Added Member:** Return to the Windows 11 virtual machine client workstation layout. Execute a complete user **log off** sequence, then immediately **log back in** as Marcus Vance. This forces the client workstation to destroy his stale login context and pull down a brand-new Kerberos security token embedded with the updated group membership identifiers.

3. **Verify Restored Access Standing:** Open File Explorer and attempt to open the shared folder network path `\\10.0.0.220\FinanceShare`. Verify that the folder interface directory opens instantly without warning prompts, confirming full environment access restoration.

![Windows 11 File Explorer Displaying Successful Access Verification Following Token Synchronization](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/8bbd8a9fc6d0018327a84eaca2cce06d9ba44e61/Shared%20Drive%20and%20Permissions/Screenshots/Shared_Folder_by_Network_PAth.png)

---

## 🔍 Verification & Auditing

### Permission Negotiation Logic Rule
* **Share vs. NTFS Combining Rule:** When a user accesses files over a network path, Windows evaluates both the Share permissions and NTFS permissions, enforcing the **most restrictive** restriction. 
* **Token Refresh Rule:** Group membership modifications do not apply to active, logged-in user sessions. A complete logoff and logon sequence is mandatory for the client subsystem to pull down the newly added Security Identifiers (SIDs) from the domain controller.

***

**Maintained By:** Ikenna Mennelik Ifedobi  
**Role:** Tier 1 Help Desk Technician  
