# Windows 11 Domain Join Documentation

Author: Ikenna Mennelik Ifedobi

Doamin: Active Directory Administration

Environment: Windows 11 Client Machine(Virtualized Bridged Network) + Windows Server 2022

Completed: July 2026

---

## 🎯 Objective
To successfully add a Windows 11 workstation to the centralized network domain, enabling the employee to authenticate and log in using their company domain credentials.

### 🏢 Business Scenario Example
A new employee has just been onboarded, and you are preparing their company-issued Windows 11 workstation. Before the user can log in with their corporate account credentials, the laptop must be joined to the internal company domain network (`lab.local`). As the IT support technician, you need to manually configure the network DNS settings so the machine can find the network, verify the connection, and securely complete the domain join process before handing the asset over to the employee.

---

## 🎛️ Network Environment Details

* **Company Domain Name:** `lab.local`
* **Primary Domain Controller IP:** `10.0.0.220`
* **Primary DNS Server:** `10.0.0.220`
* **Client Operating System Deployment:** Windows 11 Pro / Enterprise

---

## 🛠️ Configuration & Implementation

### 1. Configure Client DNS Settings
The Windows 11 workstation must use the company network DNS server to locate the authentication domain.

1. Open **Settings** on the Windows 11 client machine.
2. Navigate to **Network & internet** > **Advanced network settings**.
3. Select the active primary network adapter (Ethernet or Wi-Fi).
4. Expand the properties tray and click **View additional properties**.
5. Locate the **DNS server assignment** row and click **Edit**.
6. Switch the configuration dropdown selection from *Automatic (DHCP)* to **Manual**.
7. Toggle the **IPv4** network slider switch to **On**.
8. Populate the **Preferred DNS** target box with `10.0.0.220`.
9. Select **Save** to apply the settings.

![Windows 11 IPv4 DNS Configuration Settings](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/fedcb00e4b526fea6095a6ca4ae0a86938096374/Join%20a%20Windows%2011%20Machine%20to%20a%20Domain/Preferred%20DNS.png)

---

### 2. Verify Domain Connectivity
Before executing the domain modification, validate that the workstation can communicate with the company domain network.

Open **Command Prompt** and execute the following network diagnosis commands:
```cmd
nslookup lab.local
ping lab.local
```
* **Expected Result:** Both system utilities must successfully return and resolve the server IP footprint at `10.0.0.220`.

![Command Prompt Ping and Nslookup Output Verification](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/935c04f35b09dff8e7694f77f063a55f62c26dfc/Join%20a%20Windows%2011%20Machine%20to%20a%20Domain/CMD.jpg)

---

### 3. Join the Workstation to `lab.local`

1. Open **Settings** > **System** > **About**.
2. Select **Advanced system settings** located under the device specifications block.
3. In the System Properties box, remain on the **Computer Name** tab and select **Change...**.
4. Locate the **Member of** toggle group, select **Domain**, and type: `lab.local`
5. Select **OK**.

![System Properties Computer Name Domain Input Window](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/bc26b3e531db6f3dd996b85656d4972670098069/Join%20a%20Windows%2011%20Machine%20to%20a%20Domain/Domain%20Rename.png)

6. When the Windows Security prompt appears, enter administrative authorization credentials to approve the join:
   * **Username:** `lab.local\Administrator` (or designated delegation account)
   * **Password:** *[Your Domain Password]*
7. Select **OK**.

![Active Directory Domain Admin Credentials Prompt](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/8058846e39605ab3c176dc3bbe27649348c3fe44/Join%20a%20Windows%2011%20Machine%20to%20a%20Domain/vmware_NKrS8jcNKG.png)

---

### 4. Finalize and Reboot
1. A system message reading *"Welcome to the lab.local domain"* indicates a successful domain join.
2. Click **OK** through the successive acknowledgement warnings.
3. Click **Close** on the master System Properties window.
4. Select **Restart Now** when prompted to initialize the domain configuration.

---

## 🔍 Post-Join Verification & Authentication

### Initial User Login
1. At the Windows 11 startup lock screen, select **Other user** in the lower-left section.
2. The user can now authenticate using their new corporate credentials:
   * **Format:** `username@lab.local` or `LAB\username`
   * **Password:** *[The User's Assigned Corporate Password]*

![Windows 11 Other User Domain Login Screen](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/4b0f07a199669e5062fd3708469304a518fdde47/Join%20a%20Windows%2011%20Machine%20to%20a%20Domain/Other%20User.jpg)

### Incident Resolution Guides
* **Fault: "An Active Directory Domain Controller could not be contacted"**
  * Run `ipconfig /all` in terminal to confirm `10.0.0.220` is still set as the primary DNS server.
  * Verify the workstation is properly plugged into the company network or connected to the corporate office Wi-Fi.
* **Fault: "The network path was not found"**
  * Check the target Domain Controller to confirm corporate network firewalls are not intercepting traffic.

