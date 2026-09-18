# BitLocker Encryption and Recovery

## 🎯 Objective
To enable BitLocker Drive Encryption on an operating system drive, export the recovery key as a text file directly to a mapped network share (**`Z:`**), and simulate a customer support workflow to remediate a user locked at the boot-level recovery interface.

---

> [!CAUTION]
> **PRODUCTION SECURITY DISCLAIMER:** Saving a BitLocker recovery key to a local file or standard network folder is an extreme security risk and **strictly unacceptable in a corporate business environment**. If the network share is compromised, an attacker could locate the file and completely bypass the encryption layer. In a production enterprise ecosystem, recovery keys must be securely escrowed and centralized within an authenticated key management system such as **Active Directory Domain Services (AD DS)**, **Microsoft Entra ID**, or **Microsoft Intune**.

---

## 📊 Environment & Management Tools

| Infrastructure Component | Management Tool / Resource | Operational Function |
| :--- | :--- | :--- |
| **Full Volume Encryption** | BitLocker Manager (`control bitlocker`) | Native system utility used to initialize encryption algorithms and write protection sectors across storage disks. |
| **Corporate Network Share** | Mapped Network Partition (**`Z:`**) | Centralized network storage folder container mapped to the client workstation, used to host the backup key file. |

---

## 🚀 Standard Operating Procedures

### Part A: Enforcing BitLocker & Exporting the Recovery Key
1. Log into your domain-joined Windows 11 client virtual machine.

2. Open **File Explorer** and verify that your persistent corporate network share folder (**`Z:`**) is actively mounted and accessible.

3. Open the Start menu, type **Control Panel**, and navigate to **System and Security** > **BitLocker Drive Encryption** (or run `control bitlocker` from a Run prompt).

4. Under the Operating System Drive section row, click **Turn on BitLocker**.

![BitLocker Drive Encryption Control Panel Interface Initializing Full Storage Protection](images/01-turn-on-bitlocker.png)

5. Allow the wizard to finish running its automated hardware and configuration checks.

6. When prompted with *How do you want to back up your recovery key*, select **Save to a file**.

![BitLocker Setup Wizard Selecting Save to a File Option for the Recovery Key Backup](images/02-save-to-file-option.png)

7. When the File Explorer browse dialog pops up, select **This PC** from the sidebar, click on your mapped network drive (**`Z:`**), open the destination share folder directory space, and click **Save**.

8. Click Next, choose **Encrypt used disk space only**, select **New encryption mode**, check the box to **Run BitLocker system check**, and click **Continue**. Restart the virtual machine when prompted.

---

### Part B: Verifying the Network Backup File
1. Once the virtual machine completes its boot cycle and encryption initializes in the background, log back into your desktop workspace terminal.

2. Open **File Explorer** and click into the mapped network drive folder path layout (**`Z:`**).

3. Browse the directory listing to locate the newly written text document (e.g., `BitLocker Recovery Key [ID].txt`).

![Windows 11 File Explorer Confirming the BitLocker Recovery Key Text File Exists Inside the Mapped Z Drive Folder](images/03-network-backup-verification.png)

> [!WARNING]
> **PUBLIC PORTFOLIO SECURITY NOTE:** Even in a home lab or sandbox scenario, **never open the recovery text file to display or screenshot the raw 48-digit cryptographic key string on a public repository like GitHub**. Leaving the cleartext key visible compromises the baseline security of your lab workstation environment. Presenting an obfuscated or unopened file footprint demonstrates proper security awareness and data handling discipline to prospective employers reviewing your portfolio.

---

### Part C: Help Desk Endpoint Recovery Simulation

---

#### 1. Inbound Triage & Incident Scoping
* **Process Description:** Receive the incoming call from the locked-out end-user. Calm the customer by validating their situation and explaining that the blue screen is an automated protective feature triggered by a change in the system's hardware or firmware profile (such as a recent update). Inform them that the machine is secure and can be unlocked quickly via a phone verification sequence.

#### 2. Caller Identity Validation
* **Process Description:** Challenge the user to establish identity and asset verification before handling any cryptographic keys. Request and verify their full corporate name, employee ID, and the physical asset tag sticker located on the laptop chassis against active inventory logs to ensure proper security clearance.

#### 3. Escrow Key Retrieval
* **Process Description:** Have the user read the **Recovery Key ID** from their screen. Search the central corporate database using this ID to extract the matching 48-digit numerical key via one of the following administration consoles:

  * **Active Directory (On-Premises):** Open `dsa.msc` > enable **Advanced Features** > right-click the computer object > select **Properties** > copy the key from the **BitLocker Recovery** tab.

   * **Microsoft Entra ID (Cloud):** Log into `://microsoft.com` > go to **Devices** > **All devices** > select the computer account > click **BitLocker keys** and select **Show Recovery Key**.

#### 4. Step-by-Step Entry Guidance
* **Process Description:** Instruct the employee to ready their keyboard number keys. Read the 48-digit numerical recovery string aloud to the customer slowly, breaking the numbers down into distinct blocks of six digits at a time. Have the user type the string into the input field sequentially to process the lock clearance.
  
#### 5. Verification of Workspace Restoration
* **Process Description:** Confirm with the user that the blue screen vanishes immediately upon entering the final block. Verify that the operating system cleanly initializes the standard Windows corporate login menu. Advise the user to log in normally and keep the endpoint attached to the network link so backend storage synchronization metrics settle completely.

#### 6. Support Log Classification & Closure
* **Process Description:** Open the ticketing software console, log a comprehensive entry of the technical support workflow, and close the incident. Document all operational parameters within the case notes to preserve auditing trail transparency:

```text
============================================================
[HELP DESK INCIDENT RESOLUTION SUMMARY]
============================================================
* Incident Type: Hardware Lockout / Full Volume Encryption
* Target Endpoint Asset: WRK-W11-FIN05 (User: Marcus Vance)
* Identified Failure: Post-update TPM PCR validation break
* Recovery Action: Validated user identity; queried target
  cryptographic file vault on [Z:] via matching Recovery Key
  ID (8A2F4C7E); successfully applied 48-digit string array.
* Post-Fix Status: Partition decrypted; system operating normally.
============================================================
```

***

**Maintained By:** Ikenna Mennelik Ifedobi  
**Role:** Tier 1 Help Desk Technician  
**Date:** September 17, 2026  
