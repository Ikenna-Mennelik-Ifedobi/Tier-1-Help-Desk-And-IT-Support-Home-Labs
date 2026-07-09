# Windows 11 Domain Join Documentation

This document outlines the standard operational configuration steps required to join a Windows 11 client machine to the company network domain.

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

![Windows 11 IPv4 DNS Configuration Settings](images/dns-configuration.png)

---

### 2. Verify Domain Connectivity
Before executing the domain modification, validate that the workstation can communicate with the company domain network.

Open **Command Prompt** and execute the following network diagnosis commands:
```cmd
nslookup lab.local
ping lab.local
```
* **Expected Result:** Both system utilities must successfully return and resolve the server IP footprint at `10.0.0.220`.

![Command Prompt Ping and Nslookup Output Verification](images/network-verification.png)

---

### 3. Join the Workstation to `lab.local`

1. Open **Settings** > **System** > **About**.
2. Select **Advanced system settings** located under the device specifications block.
3. In the System Properties box, remain on the **Computer Name** tab and select **Change...**.
4. Locate the **Member of** toggle group, select **Domain**, and type: `lab.local`
5. Select **OK**.

![System Properties Computer Name Domain Input Window](images/domain-input.png)

6. When the Windows Security prompt appears, enter administrative authorization credentials to approve the join:
   * **Username:** `lab.local\Administrator` (or designated delegation account)
   * **Password:** *[Your Domain Password]*
7. Select **OK**.

![Active Directory Domain Admin Credentials Prompt](images/domain-credentials.png)

---

### 4. Finalize and Reboot
1. A system message reading *"Welcome to the lab.local domain"* indicates a successful domain join.

![Welcome to the Domain Success Notification Pop-up](images/welcome-success.png)

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

![Windows 11 Other User Domain Login Screen](images/domain-login.png)

### Incident Resolution Guides
* **Fault: "An Active Directory Domain Controller could not be contacted"**
  * Run `ipconfig /all` in terminal to confirm `10.0.0.220` is still set as the primary DNS server.
  * Verify the workstation is properly plugged into the company network or connected to the corporate office Wi-Fi.
* **Fault: "The network path was not found"**
  * Check the target Domain Controller to confirm corporate network firewalls are not intercepting traffic.

