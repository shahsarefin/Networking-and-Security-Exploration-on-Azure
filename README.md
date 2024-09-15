# Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines

In this project, I explored how to monitor network traffic between Azure Virtual Machines using Wireshark and experimented with Network Security Groups (NSGs) to control and observe the traffic.

## Environments and Technologies Used

- **Microsoft Azure** (Virtual Machines/Compute)
- **Remote Desktop Protocol (RDP)**
- **Command-Line Tools** (PowerShell, SSH)
- **Network Protocols** (ICMP, SSH, DHCP, DNS, RDP)
- **Wireshark** (Protocol Analyzer)

## Operating Systems Used

- **Windows 10 (21H2)**
- **Ubuntu Server 20.04**

## High-Level Steps

1. Create Azure Virtual Machines (Windows 10 and Ubuntu).
2. Observe ICMP Traffic using Wireshark.
3. Configure Network Security Groups (NSGs) to control and filter traffic.
4. Capture traffic for SSH, DHCP, DNS, and RDP using Wireshark.

## Detailed Steps and Observations

### Part 1: Setting Up Virtual Machines in Azure

- **Create a Resource Group:**
  - Navigate to the [Azure Portal](https://portal.azure.com).
  - Create a resource group, e.g., `Network-Security-Lab`.
  - Choose **Canada Central** as the region (since I'm based in Winnipeg).
  
  ![VM Created Virtual Network](Lab-2-Azure-Networking-Security/1-vm-created-virtual-network-created.png)

- **Create a Windows 10 Virtual Machine (VM):**
  - Use the previously created resource group.
  - Configure a new Virtual Network (VNet) and Subnet for the VM.
  
  ![Remote Desktop Connection to Windows VM](Lab-2-Azure-Networking-Security/2-Remote-Desktop-Connection-to-Windows-VM.png)

- **Create an Ubuntu Server VM:**
  - Select the same resource group and virtual network.
  - Set up SSH login with username and password.

### Part 2: Observing ICMP Traffic

- **Access Windows 10 VM via Remote Desktop:**
  - From the Azure portal, connect to the Windows VM using RDP.

- **Install Wireshark on Windows VM:**
  - Download and install Wireshark to capture network traffic.
  - Start capturing packets and apply an ICMP filter.

  ![ICMP Filtering in Wireshark](Lab-2-Azure-Networking-Security/3-icmp-filtering-search-in-wireshark.png)

- **Ping the Ubuntu VM:**
  - Retrieve the private IP of the Ubuntu VM.
  - From the Windows VM, use `ping <Ubuntu IP>` in Command Prompt.
  
  ![Ping Ubuntu VM](Lab-2-Azure-Networking-Security/4-Ping-Ubuntu-VM-from-Windows-VM-and-capture-network-traffic-filter-by-icmp-protocol-in-wireframe.png)

- **Ping a Public Website:**
  - Use `ping www.google.com` and observe the traffic in Wireshark.
  
  ![Ping Google from Windows VM](Lab-2-Azure-Networking-Security/5-Ping-Google-from-windows-vm-with-wireshark-filter-by-icmp-protocol.png)

### Part 3: Configuring Network Security Groups (NSGs)

- **Disable ICMP Traffic:**
  - Start a continuous ping from the Windows VM to the Ubuntu VM.
  - Go to the NSG for the Ubuntu VM in Azure and block inbound ICMP traffic.
  
  ![Block ICMP from Ubuntu VM NSG](Lab-2-Azure-Networking-Security/6-Created-Rule-to-block-icmp-from-ubuntu-vm-nsg.png)

  - Observe how the ping fails, and Wireshark shows no ICMP replies.

  ![ICMP Traffic Blocked](Lab-2-Azure-Networking-Security/7-ICMP-Traffic-Blocked.png)

- **Re-enable ICMP Traffic:**
  - Allow ICMP traffic again through the NSG.
  - Watch how the pings resume and traffic flows again in Wireshark.
  
  ![Revert NSG Rule to Allow ICMP](Lab-2-Azure-Networking-Security/8-Reverted-the-NSG-rule-to-allow-icmp-again.png)

  ![Ping Working After Reverting Rules](Lab-2-Azure-Networking-Security/9-icmp-or-ping-working-again-after-reverting-rules.png)

### Part 4: Observing SSH, DHCP, DNS, and RDP Traffic

- **SSH Traffic:**
  - From the Windows VM, SSH into the Ubuntu VM using its private IP.
  - Filter for SSH traffic in Wireshark to observe secure traffic.
  
  ![Observing SSH Traffic](Lab-2-Azure-Networking-Security/10-observing-SSH.png)

- **DHCP Traffic:**
  - On the Windows VM, run `ipconfig /renew` in Command Prompt to request a new IP.
  - Filter for DHCP packets and observe the traffic exchange.
  
  ![Observing DHCP Traffic](Lab-2-Azure-Networking-Security/11-Observing-DHCP-Traffic.png)

- **DNS Traffic:**
  - Use `nslookup` to query DNS for websites like `google.com`.
  - Observe the DNS requests and responses in Wireshark.
  
  ![Observing DNS Traffic](Lab-2-Azure-Networking-Security/12-Observing-DNS-Traffic.png)

- **RDP Traffic:**
  - Filter for RDP traffic in Wireshark (`tcp.port == 3389`).
  - Observe continuous traffic as the RDP session streams the desktop.
  
  ![Observing RDP Traffic](Lab-2-Azure-Networking-Security/13-Observing-RDP-Traffic.png)

## Lab End Screenshot

![Lab End Screenshot](Lab-2-Azure-Networking-Security/14-Lab-End-Screenshot.png)

## Lab Cleanup

- Close the Remote Desktop session.
- Delete the Resource Group and verify all resources are removed.
