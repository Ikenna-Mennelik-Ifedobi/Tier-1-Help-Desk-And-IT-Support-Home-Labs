# Network Diagnostics: Troubleshoot DNS and Browser Failure

This repository documents the standard operational procedures for isolating localized DNS name resolution failures from comprehensive wide area network (WAN) internet connectivity losses within the `lab.local` environment.

---

## 🎯 Objective
To systematically diagnose network adapter faults, prove the functional difference between DNS resolution issues and true physical connectivity outages using command-line diagnostic utilities, and safely restore network parameters on a Windows 11 workstation.

---

## 📊 Environment & Troubleshooting Tools

| Infrastructure Component | Management Tool / Resource | Operational Function in Lab |
| :--- | :--- | :--- |
| **Domain Controller (`10.0.0.220`)** | Active Directory Domain Services | Hosts the active internal DNS infrastructure database used to resolve network and web queries. |
| **Help Desk Workstation** | Windows Command Prompt (`cmd.exe`) | Administrative command-line environment used to execute low-level connection validation utilities. |
| **Target Endpoint** | Windows 11 Client Workstation (VM) | The managed terminal used to execute diagnostic tests, simulate adapter faults, and run verification software. |
| **Target Infrastructure** | Corporate Gateways & Public Hosts | Primary local router interface (`10.0.0.1`) and external public backbone routing footprints (`8.8.8.8`). |

---

## 🚀 Standard Operating Procedures

### Part A: Baseline Operational Verification
1. **Launch Web Browser Terminal:** Log into the Windows 11 client virtual machine and open a default web browser (e.g., Microsoft Edge or Google Chrome).

2. **Execute Initial Web Lookup:** Type an external web address (such as `google.com`) into the browser navigation URL bar and press enter.

3. **Verify Baseline Operational Health:** Confirm that the website landing page loads seamlessly, establishing that external network routing and DNS name resolution are functioning as expected.

![Web Browser Successfully Loading Google Homepage Confirming Healthy DNS](images/browser-baseline-success.png)

---

### Part B: Simulating the Fault (Misconfiguration)
1. **Access Adapter Settings:** Open **Settings** on the Windows 11 client machine and navigate to **Network & internet** > **Advanced network settings**.

2. **Locate Interface Parameters:** Select the active primary network adapter (Ethernet or Wi-Fi) and click **View additional properties**.

3. **Inject Unreachable DNS IP:** Locate the **DNS server assignment** row, click **Edit**, change the dropdown configuration to **Manual**, toggle **IPv4** to **On**, and assign an unreachable dummy IP address (e.g., `10.99.99.99`).

![Windows 11 IPv4 Network Adapter Properties Manual DNS Configuration Entry](images/dns-fault-injection.png)

4. **Commit Configuration Changes:** Click **Save** to lock the faulty name translation parameters into the active network adapter stack.

---

### Part C: Command-Line Diagnostic Verification
1. **Open Console Utility:** Right-click the Windows Start menu and select **Terminal** or **Command Prompt**.

2. **Execute Domain Resolution Test:** Attempt to reach an external host by running the standard connectivity diagnostic:
   ```cmd
   ping google.com
   ```
   * **Expected Failure Output:** `Ping request could not find host google.com. Please check the name and try again.` (Indicates the system cannot successfully map the text name to a numeric IP).

![Command Prompt Ping Attempt to Domain Name Yielding Unresolvable Host Error](images/ping-domain-failure.png)

3. **Prove Raw WAN IP Reachability:** Test low-level network path processing by skipping the name server lookup tier entirely and pinging a known public network backbone directly:
   ```cmd
   ping 8.8.8.8
   ```
   * **Expected Success Output:** Clean, low-latency ICMP Echo replies. This explicitly proves that the workstation retains active routing out to the open internet, isolating the issue purely away from a physical cord or ISP outage.

![Command Prompt Ping to Public IP Address Returning Clean Successful Replies](images/ping-ip-success.png)

4. **Isolate Name Server Failure:** Directly query the network name translation system using the infrastructure analysis tool:
   ```cmd
   nslookup google.com
   ```
   * **Expected Failure Output:** `DNS request timed out.` or `No response from server.` (Confirms the lookup query is failing exclusively against the dead `10.99.99.99` destination).

![Command Prompt NSLookup Diagnostic Tool Output Timed Out Against Dummy IP](images/nslookup-timeout-failure.png)

---

### Part D: Network Parameter Restoration
1. **Return to Interface Properties:** Re-open the active client network adapter profile configurations menu under Advanced Network Settings.

2. **Point Client to Working DNS Server:** Edit the IPv4 parameters, clear out the unreachable dummy address, and set the **Preferred DNS** box back to the active internal infrastructure path at `10.0.0.220`.

3. **Flush Local Client Resolver Cache:** Open Command Prompt and clear out any stale or corrupted diagnostic logs held by the operating system resolver by running:
   ```cmd
   ipconfig /flushdns
   ```

![Command Prompt IPConfig FlushDNS Tool Executing Cache Purge Confirmation](images/ipconfig-flushdns.png)

4. **Execute Post-Repair Verification:** Re-run `nslookup google.com` and reload your desktop web browser to confirm that internal names resolve instantly and application communications are restored.

![Command Prompt Post Repair NSLookup Successfully Mapping Domain to IP Footprints](images/nslookup-repair-success.png)

---

## 🔍 Verification & Auditing

### Fault Isolation Check
* Review diagnostic outputs to prove that a failed `ping domain.com` matched with a successful `ping IP_Address` constitutes a DNS configuration failure, not a physical cable connection drop.

### Operational Access Restoration Check
* Verify that the client workstation successfully queries external internet space without delay following the correction of the primary adapter parameters.

***

**Maintained By:** Ikenna Mennelik Ifedobi  
**Role:** Tier 1 Help Desk Technician  

