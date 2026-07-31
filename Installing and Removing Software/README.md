# Software Management: Application Lifecycle, Version Conflicts, and Remediation Lab

Author: Ikenna Mennelik Ifedobi

Domain: Windows 11 Software Deployment and Version Management

Environment: Windows 11 Client, Adobe Acrobat Reader(Approved) Adobe Acrobat 5.0(Legacy Conflict)

Completed July 2026

---

## 🎯 Objective
To successfully deploy an approved enterprise software package, verify installation metrics, identify and isolate application version conflicts using built-in Windows diagnostic tools, and execute a clean remediation removal to restore standard operating software health.

---

## Business Scenario
**Software Configuration Incident (Date: July 24, 2026):** An employee submits a support request stating that their core productivity application is continuously crashing and throwing compatibility errors. As the Tier 1 Help Desk Technician, you suspect a software version conflict caused by unapproved program files coexisting with the company's verified deployment package. Your objective is to isolate the overlapping installations using native operating system diagnostic tools, safely purge the conflicting legacy software from the system, and restore a stable, uncorrupted application workspace for the user.

---

## 📊 Environment & Management Tools

| Infrastructure Component | Management Tool / Resource | Operational Function in Lab |
| :--- | :--- | :--- |
| **System Settings Registry** | Installed Apps List / Features | The centralized operating system ledger used to inventory active software, check version numbers, and trigger uninstall strings. |
| **Operating System Daemon** | Program Compatibility Assistant | An automated Windows safety system that intercepts and flags architectural anomalies or legacy application conflicts. |
| **Approved Repository** | Production Software Installer | The verified, signed corporate installer package cleared for enterprise deployment (e.g., Adobe Acrobat Reader v24.x). |
| **Legacy Media Vault** | Conflicting Legacy Installer | An unapproved, outdated application package used to simulate shadow IT installations and version control breaks. |
| **Target Endpoint** | Windows 11 Client Workstation (VM) | The managed virtual terminal used by Tier 1 technicians to test deployment stability and execute app lifecycle actions. |

---

## 🚀 Standard Operating Procedures

### Part A: Approved Software Deployment & Verification
1. **Execute Production Installation:** Log into the Windows 11 client virtual machine, launch the approved enterprise software installer package (e.g., Adobe Acrobat Reader v24), and complete the setup wizard.
![Windows Installation Wizard Interface Executing Approved Corporate Software Deployment](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/e73cfb32d54d3f233d51158ea8ef3194eaa57ab3/Installing%20and%20Removing%20Software/Screenshots/Installation_Wizard.png)

2. **Verify Correct Version Control Number:** Navigate to **Settings** > **Apps** > **Installed apps**, locate the software, and document the official version string to ensure alignment with company baselines.
![Windows Installed Apps Configuration Window Confirming Production Version Number](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/e73cfb32d54d3f233d51158ea8ef3194eaa57ab3/Installing%20and%20Removing%20Software/Screenshots/Correct_Version.png)

3. **Establish Operational Application Baseline:** Launch the newly installed approved software tool from the desktop to confirm it opens cleanly without generating errors.
![Approved Enterprise Software Utility Launching Cleanly on Desktop Without Error Alerts](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/e73cfb32d54d3f233d51158ea8ef3194eaa57ab3/Installing%20and%20Removing%20Software/Screenshots/Launch_Approved_Software.png)

---

### Part B: Simulating a Software Version Conflict
1. **Deploy Outdated Legacy Package:** Run an unapproved legacy or older major version of the same software application tool (e.g., legacy Adobe Reader v11) alongside the production version.

![Windows System Initializing Outdated Unapproved Legacy Application Installer Wizard](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/e73cfb32d54d3f233d51158ea8ef3194eaa57ab3/Installing%20and%20Removing%20Software/Screenshots/Legacy_Installation.png)

2. **Intercept Architectural Discrepancy:** Complete the installer prompts and observe how the underlying operating system environment responds to the dual-version installation.

---

### Part C: Conflict Identification & Isolation
1. **Analyze System Integrity Logs:** Attempt to launch the original approved application or wait for the system to process the runtime error block.

2. **Document Compatibility Daemon Warning:** Observe the automated **Program Compatibility Assistant** window popup alert indicating that an active program conflict or block has been flagged.

![Program Compatibility Assistant Pop-up Alert Intercepting Version Mismatch Block](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/e73cfb32d54d3f233d51158ea8ef3194eaa57ab3/Installing%20and%20Removing%20Software/Screenshots/Software_Conflict.png)

3. **Audit Active Application Inventory:** Return to **Settings** > **Apps** > **Installed apps** and observe the presence of both overlapping application versions sitting inside the ledger simultaneously.

---

### Part D: Remediation & Post-Repair Validation
1. **Target Conflicting Software Element:** Locate the unapproved legacy software object inside the **Installed apps** list panel layout.

2. **Execute Clean Removal Action:** Click the three dots next to the legacy entry item tool row, select **Uninstall**, and authorize the removal action thread.
![Windows Uninstallation Wizard Removing the Conflicting Legacy Application File System Structure](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/e73cfb32d54d3f233d51158ea8ef3194eaa57ab3/Installing%20and%20Removing%20Software/Screenshots/Uninstall_Legacy.png)

3. **Confirm Removal Verification:** Refresh the Installed Apps window interface ledger registry block to verify that only the single, approved production software entry remains.
![Windows Installed Apps List Audited and Confirming Only Approved Asset Remains](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/e73cfb32d54d3f233d51158ea8ef3194eaa57ab3/Installing%20and%20Removing%20Software/Screenshots/Correct_Version.png)

4. **Execute Final Software Quality Check:** Launch the approved enterprise software asset utility from the desktop workspace layout to confirm it opens successfully and operates completely without crashes or errors.
![Approved Production Software Opening Successfully and Securely Restoring Workspace Baseline](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/e73cfb32d54d3f233d51158ea8ef3194eaa57ab3/Installing%20and%20Removing%20Software/Screenshots/Launch_Approved_Software.png)

---

## 🔍 Verification & Auditing

### Software Compliance Assessment Rules
* **Multi-Version Coexistence:** Staging multiple major versions of software utilizing overlapping system extensions triggers registry overrides, corrupting core file associations.
* **Compatibility Hooking:** The Windows Program Compatibility Assistant continuously scans system event logs to block outdated runtimes from degrading standard enterprise workstation profiles.

***

**Maintained By:** Ikenna Mennelik Ifedobi  
**Role:** Tier 1 Help Desk Technician  

