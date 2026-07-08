# Windows Server 2022: AD DS Installation & Domain Controller Promotion

## 📌 Lab Objective
This lab documents the step-by-step process of preparing a standalone Windows Server 2022 instance, installing the Active Directory Domain Services (AD DS) role, and promoting the server to a primary Domain Controller (DC) for a new forest. 

### 🛠️ Skills Gained / Tools Used
* **Operating System:** Windows Server 2022 Standard
* **Roles & Features:** Active Directory Domain Services (AD DS), DNS Server
* **Administrative Tools:** Server Manager, AD DS Configuration Wizard
* **Core Concepts:** Root Domain Trees, Forest Deployment, Bridged Networking

---

## 🚀 Step-by-Step Implementation

### Step 1: Network Discovery & Pre-Requisite Server Preparation
To safely configure a static IP in a bridged environment without disrupting existing home network traffic, network discovery was performed on the host machine.

1. Opened Command Prompt on the host machine and ran `ipconfig` to determine the home network layout:
   * **Subnet Gateway:** Found to be `10.0.0.1`
   * **Subnet Mask:** `255.255.255.0`
2. Selected a high IP address (`10.0.0.220`) outside the home router's typical dynamic DHCP pool to prevent IP address conflicts with household devices.
3. Changed the server's randomized computer name to a standardized enterprise name: `DC01`.
4. Assigned the static IPv4 configuration to the Server's network adapter:
   * **IP Address:** `10.0.0.220`
   * **Subnet Mask:** `255.255.255.0`
   * **Default Gateway:** `10.0.0.1` (Points directly to the physical home router)
   * **Preferred DNS:** `127.0.0.1` (Loopback address ensuring the server points to its own local AD-integrated DNS zone)

![Server Rename Confirmation](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/98c043dae632934c707165080f01144a822b39cd/01a-server-prep.png)
![Static IP and DNS Setiings](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/d85f21a24fe8a99f2baf174fe4f6b3df4b118cc0/01b-static-ip.png)

### Step 2: Installing the AD DS Binary Files
* Opened **Server Manager** and initiated the *Add Roles and Features Wizard*.
* Selected **Role-based or feature-based installation**.
* Selected `DC01` from the server pool and checked the box for **Active Directory Domain Services**.
* Accepted the required management features and completed the installation wizard.

![AD DS Role Selection in Server Manager](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/52030ecd6efd356c51c943c161faa20d58111994/vmware_HbXO2var0M.png)

### Step 3: Promoting the Server to a Domain Controller
* Clicked the yellow notification flag in Server Manager and selected **Promote this server to a domain controller**.
* In the Deployment Configuration, selected **Add a new forest**.
* Specified the Root Domain Name: `lab.local`.

### Step 4: Configuring Domain Options & DSRM
* Set the Forest and Domain functional levels to **Windows Server 2016** (highest available option in Server 2022).
* Ensured **Domain Name System (DNS) server** was checked.
* Created a secure **Directory Services Restore Mode (DSRM)** password and stored it safely.
* Clicked through the NetBIOS name confirmation (`LAB`) and paths setup.

### Step 5: Prerequisites Check & Installation
* The wizard performed a prerequisite check to verify the network and system configuration.
* Reviewed and ignored minor warnings regarding delegation for DNS and cryptography algorithms.
* Clicked **Install**. The server automatically rebooted upon completion to finalize the promotion.

![Prerequisites Verification and Install](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/39c465fbd0a13aa5c84b496ddb12688cf2433782/vmware_HbXO2var0M.png)

---

## 🔍 Verification & Post-Installation Checks
* **Sign-in Verification:** Logged back into the server using the new domain administrator format: `LAB\Administrator`.
* **Administrative Tools:** Verified that **Active Directory Users and Computers**, **Active Directory Domains and Trusts**, and **DNS Manager** consoles now appear under the Windows Administrative Tools menu.
* **Network Connectivity:** Ran `ping google.com` to verify that the server can still successfully pass external traffic through the bridged gateway to the internet while maintaining active domain services.

---

## 💡 Key Takeaways
* **Bridged DNS Rule:** Because the network is bridged to a home router, any subsequent client VMs joined to this domain **must** have their Preferred DNS explicitly pointed to `10.0.0.220`. If left to automatic DHCP, clients will query the home router instead of the domain controller, causing domain join failures.
* **IP Management:** Choosing a static address high up in the subnet range keeps the lab traffic completely isolated from standard household Wi-Fi/Ethernet assignments.

