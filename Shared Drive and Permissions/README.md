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

## 🚀 Standard Operating Procedures

### Part A: Active Directory Infrastructure Staging
1. **Launch Directory Management Console:** Open the Start menu on the Domain Controller, type `dsa.msc`, and press **Enter** to launch **Active Directory Users and Computers**.
2. **Navigate to Target Container:** Expand the root domain tree layout (`lab.local`) and select the **Employees** Organizational Unit (OU).
3. **Initialize Security Group Object:** Right-click inside the blank right-hand directory pane, select **New** > **Group**, and populate the following parameters:
   * **Group name:** `Finance-Dept-GG`
   * **Group scope:** Global
   * **Group type:** Security
4. **Commit the Group Profile:** Click **OK** to save the new global security group to the directory ledger.
![Active Directory Users and Computers Creating the Finance Global Security Group Object](images/00-create-security-group.png)

5. **Assign Target User to Group:** Double-click the newly created `Finance-Dept-GG` object, navigate to the **Members** tab, and click **Add...**.
6. **Query and Bind Identity Profile:** Type `Sarah Jenkins` into the object name field selection tray, click **Check Names** to resolve her domain account, and click **OK** twice to bind her profile to the group resource list.
![Active Directory Users and Computers Assigning Sarah Jenkins to the Finance Security Group](images/00-add-sarah-to-group.png)

---

### Part B: Server-Side Share Provisioning & Permissions Staging
1. **Initialize File System Folder:** Open **File Explorer** on the Domain Controller, navigate to your primary data storage volume layout (e.g., `C:\`), right-click inside the empty workspace space, select **New** > **Folder**, and name it `Finance_Data`.
2. **Configure Network Share Access:** Right-click the newly created folder, navigate to **Properties** > **Sharing** > **Advanced Sharing**, check **Share this folder**, click **Permissions**, and configure the *Everyone* group object to **Change/Read** permissions.
![Windows Server Advanced Sharing Properties Console Configuring Share Permissions](images/01-share-permissions.png)

3. **Configure NTFS Security Layer:** Switch to the **Security** tab, click **Advanced**, disable permission inheritance, and strip unapproved users from the Access Control List (ACL).
4. **Scope Access to Security Group:** Click **Add**, target the explicit departmental security group (`Finance-Dept-GG`), and assign them **Modify, Read & execute, List folder contents, Read, and Write** permissions.
![Windows Server Advanced Security Settings Appending Departmental Security Group to NTFS ACL](images/02-ntfs-permissions.png)

---

### Part C: Client-Side Drive Mapping & Access Boundary Testing
1. **Initialize Authorized Client Session:** Log into the domain-joined Windows 11 client virtual machine using the credentials of an authorized employee (**Sarah Jenkins**) who belongs to the security group.
2. **Execute Network Drive Mapping:** Open **File Explorer**, right-click **This PC**, and select **Map network drive...**.
3. **Target UNC Infrastructure Path:** Assign an available drive letter (**`Z:`**) and input the Universal Naming Convention (UNC) path targeting the server repository: `\\10.0.0.220\Finance_Data`.
4. **Enable Persistent Connection Flag:** Ensure the checkbox for **"Reconnect at sign-in"** is explicitly checked so that the network mapping persists across system reboots and logoffs.
![Windows 11 Map Network Drive Window with Reconnect at Sign In Option Enabled](images/03-map-network-drive.png)

5. **Execute Session Reset:** **Log out** of the Windows 11 workstation completely and **log back in** as the authorized user. This ensures that the newly created persistent network drive mount configuration commits safely to the user's profile database.
![Windows 11 Client Workstation Authorized User Executing Session Reset Before Folder Access](images/04-authorized-session-reset.png)

6. **Verify Authorized Access Flow:** Open File Explorer, navigate to the newly mapped **`Z:`** drive folder layout, create a blank text document, write sample string metrics, and save the file.
![Windows 11 File Explorer Confirming Successful File Creation by Authorized User](images/05-authorized-access-success.png)

7. **Initialize Unauthorized Client Session:** Log out of the Windows 11 terminal and sign back in using an unapproved user account (**Marcus Vance**) that is not a member of the security group.
8. **Attempt Direct Share Penetration:** Open File Explorer, navigate to the address bar, and manually attempt to browse directly to the network path: `\\10.0.0.220\Finance_Data`.
9. **Document Access Denied Intercept:** Observe that the local operating system security layer intercepts the connection handshake and flags the explicit restriction window popup: *"Windows cannot access \\10.0.0.220\Finance_Data. You do not have permission to access..."*
![Windows Security Prompt Blocking Connection and Generating Network Error Access Denied Alert](images/06-access-denied-block.png)

---

### Part D: Remediation and Access Resolution
1. **Launch Directory Management Console:** Return to the Tier 1 help desk administrative console and open Active Directory Users and Computers (`dsa.msc`).
2. **Locate Target Access Group:** Search for or browse to the dedicated security group folder and double-click the `Finance-Dept-GG` object properties.
3. **Append Restricted User to Group:** Click on the **Members** tab, select **Add...**, enter the username of the unauthorized employee (**Marcus Vance**) who was blocked in the previous step, and click **OK** to apply.
![Active Directory Users and Computers Appending the Blocked Employee to the Target Security Group](images/07-add-user-to-group.png)

4. **Execute Forced Kerberos Token Refresh:** Instruct the unauthorized user to **log out** of the Windows 11 client virtual machine completely and **log back in**. This breaks their current security context and forces the OS to pull down a brand-new Kerberos Ticket-Granting Ticket (TGT) populated with the new security group SID from the Domain Controller.
![Windows 11 Client Workstation Logging Off to Refresh Enforced Active Directory Security Tokens](images/08-user-logoff-token-refresh.png)

5. **Execute Successful Access Check:** Open File Explorer and access the network share directory path `\\10.0.0.220\Finance_Data`. Verify that the folder opens successfully without error prompts, and confirm the user can read and modify the existing files.
![Windows 11 File Explorer Displaying Successful Directory Access and File Content Reading Following Group Modification](images/09-access-resolution-success.png)

---

## 🔍 Verification & Auditing

### Permission Negotiation Logic Rule
* **Share vs. NTFS Combining Rule:** When a user accesses files over a network path, Windows evaluates both the Share permissions and NTFS permissions, enforcing the **most restrictive** restriction. 
* **Token Refresh Rule:** Group membership modifications do not apply to active, logged-in user sessions. A complete logoff and logon sequence is mandatory for the client subsystem to pull down the newly added Security Identifiers (SIDs) from the domain controller.

***

**Maintained By:** Ikenna Mennelik Ifedobi  
**Role:** Tier 1 Help Desk Technician  
