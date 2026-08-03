# Onboarding and Offboarding Workflow

## 🎯 Objective
To execute a comprehensive, audited identity and asset onboarding sequence on an enterprise endpoint by tracking an incoming onboarding mandate, creating directory objects under standard containers, and deploying required productivity workloads.

---

## 🏢 Business Scenario
**Onboarding Phase (Date: August 3, 2026):** Human Resources submits a new starter notice for an employee named Marcus Vance, who is joining the Corporate Finance division. As the Tier 1 Help Desk Technician, your objective is to handle his full identity provisioning, workspace hardware staging, and corporate drive mappings to ensure immediate day-one productivity in alignment with corporate deployment baselines.

 **Offboarding Phase (Date: August 10, 2026):** Human Resources issues an official separation notice for Marcus Vance at the conclusion of his service. As the Tier 1 Help Desk Technician, your objective is to respond to the support ticket to immediately revoke his active directory account access, strip his inherited group permissions, scramble his login credentials, and process his returned corporate hardware against the asset deployment compliance checklist.

---

## 📊 Environment & Infrastructure Map

| Infrastructure Component | Management Tool / Resource | Operational Function |
| :--- | :--- | :--- |
| **Domain Controller (`10.0.0.220`)** | Active Directory Users & Computers (`dsa.msc`) | Handles centralized identity objects, group allocations, and processing authentication flags. |
| **Corporate File Server** | Advanced Share & NTFS Permissions | Hosts secure departmental storage shares (`\\10.0.0.220\FinanceShare`) mapped across endpoints. |
| **Help Desk Workstation** | Windows 11 Client Workstation (VM) | The targeted deployment hardware asset used to test domain attachments, mount network drives, and track user states. |
| **Application Layer** | Enterprise Software Repository | Houses verified productivity installer packages and corporate messaging configurations (Microsoft 365, Teams). |

---

## 🚀 Standard Operating Procedures

### Part A: Phase 1 - Employee Onboarding Workflow

#### 1. Incoming Ticket Log Verification
![Notepad Window Interface Confirming and Staging Enforced HR Onboarding Metadata Variables](images/01-notepads-onboarding-ticket.png)

#### 2. Active Directory Identity Provisioning
1. Log into the Domain Controller and open **Active Directory Users and Computers** (`dsa.msc`).
2. Navigate to the default **Users** container path under the root domain tree hierarchy (`lab.local/Users`).
3. Right-click inside the `Users` container pane, select **New** > **User**, and provision the new hire identity (**Marcus Vance**, username: `mvance`).
4. Set a complex temporary password, check **"User must change password at next logon"**, and click Finish.
![Active Directory Users and Computers Initializing New Hire User Account Parameters inside Users Container](images/02-provision-new-user.png)

#### 3. Department Security Group Creation
1. Remain within the default **Users** container path under the root domain tree hierarchy (`lab.local/Users`).
2. Right-click inside the `Users` container pane and select **New** > **Group**.
3. Name the global security group `Finance`, ensuring the scope is set to **Global** and type is set to **Security**.
4. Double-click the newly created `Finance` group object, navigate to the **Members** tab, click **Add...**, and bind user `mvance` to the registry group ledger.
![Active Directory Users and Computers Nesting New Hire Account into Scoped Departmental Group](images/03-create-security-group.png)

#### 4. Client Workstation Domain Join
1. Boot the unmanaged corporate laptop virtual machine, navigate to **Settings** > **Network & internet** > **Advanced network settings**, and configure the manual Preferred DNS target box to `10.0.0.220`.
2. Navigate to **System** > **About** > **Advanced system settings** > **Computer Name** tab, and click **Change...**.
3. Toggle membership from Workgroup to **Domain**, input `lab.local`, and pass authorized domain administrator credentials to approve the connection handshake. Acknowledge the welcome greeting popup and click **Restart Now**.
![Windows 11 Client Device Completing Domain Handshake Connection and Requesting System Reboot](images/04-client-domain-join.png)

#### 5. Software Deployment & Email Access Configuration
1. Log into the domain-attached Windows 11 workstation using the new hire's temporary credentials, and complete the forced initial password reset prompt.
2. Launch the enterprise software deployment utility to install required workplace packages (e.g., Microsoft 365 apps, Microsoft Teams).
3. Open the mail utility app, populate user fields using the corporate UPN (`mvance@lab.local`), and complete the connection authentication loop to activate corporate email delivery.
![Windows 11 Client Application Interface Verifying Clean Corporate Email Profile Integration](images/05-configure-email-access.png)

#### 6. Persistent Departmental Drive Mapping
1. Open **File Explorer**, right-click **This PC**, and select **Map network drive...**.
2. Assign drive letter **`Z:`**, input the server UNC storage path `\\10.0.0.220\FinanceShare`, and ensure **"Reconnect at sign-in"** is checked.
3. Click Finish, then execute a quick system log out and log back in to finalize the network link persistent attachment.
![Windows 11 File Explorer Confirming Successful Mapping of Persistent Z Drive Storage Volume](images/06-map-persistent-drive.png)

#### 7. Day One Handover Note Generation
* Create a day one handover note summarizing the approved workflow. This document will be given to the user and is attached to the ticket.
![Notepad Ticket Onboarding Handover]()

---

### Part B: Phase 2 - Employee Offboarding Workflow

#### 1. Inbound Separation Ticket Verification
Document the key requirements from the incoming HR offboarding ticket to verify all mandatory separation parameters:

![Notepad Window Interface Reviewing and Confirming Mandated HR Offboarding Compliance Metrics](images/01-notepads-offboarding-ticket.png)

#### 2. Disable Active Directory Account
1. Log into your Domain Controller desktop workspace.
2. Open the Start menu, type `dsa.msc`, and press **Enter** to launch **Active Directory Users and Computers**.
3. In the left navigation tree, expand the domain root and browse to the default **Users** container path: `lab.local/Users`.
4. Locate the user object **Marcus Vance** (username: `mvance`), right-click the record row, and select **Disable Account**. Acknowledge the immediate confirmation popup.

![Active Directory Users and Computers Console Instantly Revoking Interactive Logon Capabilities](images/02-disable-departing-user.png)

#### 3. Remove Group Memberships
1. Double-click the disabled `mvance` user profile object icon to open its properties window sheet.
2. Navigate into the **Member Of** properties tab layout pane view.
3. Highlight the assigned `Finance` security group and email distribution listings, click the **Remove** button, and confirm the change.

![Active Directory Account Properties Purging Group Membership Access Tokens](images/03-strip-group-permissions.png)

#### 4. Reset the Password
1. Close the properties sheet, right-click the `mvance` user profile object icon again, and select **Reset Password...**.
2. Input a long, randomized text character string into the password fields to overwrite the user's old credentials and click **OK**.

![Active Directory Account Reset Password Box Overwriting User Credentials with Randomized String](images/04-randomize-password.png)

#### 5. Collect the Device and Complete the Hardware Checklist
1. Recover the physical corporate laptop device asset and peripherals assigned to Marcus Vance (`WRK-W11-FIN05`) from the workspace terminal layout.
2. Run a physical assessment sweep on the components and fill out the tracking criteria checklist:

![Tier 1 Inventory Staging Grid Processing Returned Corporate Computer Hardware Assets](images/05-hardware-collection.png)



---

**Maintained By:** Ikenna Mennelik Ifedobi  
**Role:** Tier 1 Help Desk Technician  
