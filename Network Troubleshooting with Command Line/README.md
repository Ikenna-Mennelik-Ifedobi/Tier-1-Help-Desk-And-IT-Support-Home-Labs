# Network Troubleshooting with Command Line

Author: Ikenna Mennelik Ifedobi

Domain: Network Diagnostics; Command Line

Environment: Windows 11 Client Machine

Completed: July 2026

---

## 🎯 Objective
To systematically document the behavior of local IP configuration metrics, interface state commands, and address resolution tables before, during, and after a simulated hardware-level network adapter disconnection on a Windows 11 workstation.

---

## Business Scenario
 **Network Stack Incident (Date: July 24, 2026):** An employee contacts the Tier 1 Help Desk reporting a sudden and complete loss of both internal intranet applications and external web connectivity on their workstation following a background network profile update. As the Tier 1 Help Desk Technician handling this ticket, your objective is to isolate whether the root cause stems from a localized software stack failure, an incorrect IP binding configuration, or a hardware-level media connection drop. You will utilize native command-line diagnostic tools to pinpoint the exact layer where network transmission cuts off, analyze how the operating system manages communication tables while the interface is completely disconnected from the network link, and safely restore full corporate network access for the employee.

---

## 📊 Environment & Diagnostic Tools

| Infrastructure Component | Management Tool / Resource | Operational Function in Lab |
| :--- | :--- | :--- |
| **Local IP Stack Utilities** | `ipconfig` tool suite | Used to gather comprehensive adapter details (`/all`), discard current DHCP leases (`/release`), and request new leases (`/renew`). |
| **Local Loopback / NIC IP** | `127.0.0.1` & Local Machine IP | Used to analyze software stack function vs. local network card interface configuration boundaries. |
| **Address Resolution Protocol** | `arp -a` command utility | Displays the local hardware-to-IP address mapping table to evaluate gateway resolution properties. |
| **Target Infrastructure** | Corporate Gateway & Public WAN | Default gateway router interface (`10.0.0.1`) and external public backbone routing footprints (`8.8.8.8`). |
| **Target Endpoint** | Windows 11 Client Workstation (VM) | The managed virtual terminal used to execute diagnostic tests and simulate the hardware-level media disconnection. |

---

## 🚀 Standard Operating Procedures

### Part A: Establishing the Operational Baseline (Pre-Disconnection)
Before simulating the hardware fault, execute a comprehensive bottom-up diagnostic sweep to verify optimal layer-1 through layer-3 connection health.

1. **Document Master IP Configurations:** Open Command Prompt and run the configuration review utility:
   ```cmd
   ipconfig /all
   ```
![Command Prompt Output Displaying Master IP Configuration and Adapter Properties](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/395b8263202109a0c1d35220512fe0e292b7bc1f/Network%20Troubleshooting%20with%20Command%20Line/Screenshots/ipconfig_all.png)

2. **Validate Local Software Stack:** Confirm the operating system can process low-level network instructions:
   ```cmd
   ping 127.0.0.1
   ```
![Command Prompt Successful Ping Output to Loopback Address](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/395b8263202109a0c1d35220512fe0e292b7bc1f/Network%20Troubleshooting%20with%20Command%20Line/Screenshots/loopback_address.png)

3. **Validate Local Interface Assignment:** Ping the machine's own assigned local IP address (e.g., `10.0.0.50`) to verify the interface card is bound to the stack.
   ```cmd
   ping [Your_Machine_IP]
   ```
![Command Prompt Successful Ping Output to Machine Assigned IP Address](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/395b8263202109a0c1d35220512fe0e292b7bc1f/Network%20Troubleshooting%20with%20Command%20Line/Screenshots/client_machine_ip.png)

4. **Validate Local Subnet Gateway:** Ping the default gateway to ensure local area network path routing is open:
   ```cmd
   ping 10.0.0.1
   ```
![Command Prompt Successful Ping Output to Default Gateway Router](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/395b8263202109a0c1d35220512fe0e292b7bc1f/Network%20Troubleshooting%20with%20Command%20Line/Screenshots/Default_Gateway.png)

5. **Validate Wide Area Network Path:** Ping an external public host to confirm internet-wide route processing is healthy:
   ```cmd
   ping 8.8.8.8
   ```
![Command Prompt Successful Ping Output to External Public IP Address](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/395b8263202109a0c1d35220512fe0e292b7bc1f/Network%20Troubleshooting%20with%20Command%20Line/Screenshots/Public_ip.png)

---

### Part B: Simulating the Hardware Fault (NIC Disconnection)
1. **Disconnect Virtual Network Hardware:** Access your hypervisor software dashboard (such as VMware, Hyper-V, or Proxmox) and disconnect the network adapter or uncheck the "Connected" option box on the Windows 11 virtual machine settings pane.

![Hypervisor Settings Disconnecting the Virtual Network Adapter from the VM](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/395b8263202109a0c1d35220512fe0e292b7bc1f/Network%20Troubleshooting%20with%20Command%20Line/Screenshots/Disconnect_Network_Adapter.png)

---

### Part C: Analyzing the Disconnected Interface Lifecycle
Execute the following commands in exact chronological order to document how the Windows operating system behaves when network media is completely missing.

1. **Discard Active IP Lease Parameters:** Run the release utility to clear out the current configuration parameters:
   ```cmd
   ipconfig /release
   ```
   * **Expected Behavior:** The console outputs an error indicating that the operation cannot be performed on the interface while its media is disconnected.

![Command Prompt IPConfig Release Failing Due to Disconnected Media State](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/395b8263202109a0c1d35220512fe0e292b7bc1f/Network%20Troubleshooting%20with%20Command%20Line/Screenshots/ipconfig_release.png)

2. **Attempt Lease Renewal Protocol:** Force a lease request out to the subnet infrastructure:
   ```cmd
   ipconfig /renew
   ```
   * **Expected Behavior:** The command fails immediately with a strict media-disconnected warning, as no DHCP discover frames can be transmitted onto the physical wire.

![Command Prompt IPConfig Renew Failing with Media Disconnected Error Code](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/395b8263202109a0c1d35220512fe0e292b7bc1f/Network%20Troubleshooting%20with%20Command%20Line/Screenshots/ipconfig_renew.png)

3. **Evaluate Local Address Resolution Table:** Inspect the local cache mapping table to evaluate gateway resolution properties:
   ```cmd
   arp -a
   ```
   * **Expected Behavior:** The command returns empty or displays no active entries for the default gateway, showing that resolution paths are invalid without an active network link.

![Command Prompt ARP Cache Command Output Showing No Active Gateway Resolution entries](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/395b8263202109a0c1d35220512fe0e292b7bc1f/Network%20Troubleshooting%20with%20Command%20Line/Screenshots/Inspect_arp_table.png)

---

### Part D: Hardware Reconnection & Post-Repair Validation
1. **Reconnect Virtual Network Hardware:** Return to your hypervisor dashboard settings pane, re-enable the network adapter link, or check the "Connected" option box for the Windows 11 virtual machine.

2. **Execute Final Reachability Sweep:** Return to the Command Prompt and ping the public network host backbone again to confirm the link layer has re-established communication:
   ```cmd
   ping 8.8.8.8
   ```

![Command Prompt Final Verification Test Returning Successful Pings Following Hardware Reconnection](https://github.com/Ikenna-Mennelik-Ifedobi/Tier-1-Help-Desk-And-IT-Support-Home-Labs/blob/395b8263202109a0c1d35220512fe0e292b7bc1f/Network%20Troubleshooting%20with%20Command%20Line/Screenshots/public_ip_again.png)

---

## 🔍 Verification & Auditing

### Media Disconnection Operational Matrix
* **`ipconfig /release & /renew` behavior:** Windows explicitly blocks DHCP handshakes and locks state fields when media sense protocols report a broken physical link layer.
* **`arp -a` behavior:** The address resolution cache cannot establish or maintain layer-2 MAC translations for the default gateway once the interface hardware goes offline.

***

**Maintained By:** Ikenna Mennelik Ifedobi  
**Role:** Tier 1 Help Desk Technician  

