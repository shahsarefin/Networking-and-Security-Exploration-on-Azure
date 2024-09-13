# Learning Notes: Networking and Security Exploration on Azure

## Overview
This document contains detailed learning notes from the "Networking and Security Exploration on Azure" project. It highlights key concepts, practical skills, and knowledge gained during the project.

### 1. Network Monitoring with Wireshark
- **Purpose:** Wireshark is used to capture and analyze network traffic. It helps in identifying how data flows between devices and in diagnosing network issues.
- **Key Points to Remember:**
  - **Filters:** Use filters (e.g., `icmp`, `ssh`, `dns`) to isolate specific traffic types.
  - **Traffic Analysis:** Observing ping requests and responses can help determine connectivity between devices.
  - **Protocol Behavior:** Different protocols have specific patterns; understanding these helps in identifying normal vs. abnormal traffic.

### 2. Configuring Network Security Groups (NSGs)
- **Purpose:** NSGs act as a firewall to control inbound and outbound traffic for Azure Virtual Machines.
- **Key Points to Remember:**
  - **Rules:** NSGs use rules to allow or deny traffic based on IP addresses, ports, and protocols.
  - **Common Configurations:** 
    - Allow ICMP to enable pinging.
    - Block specific traffic types (e.g., SSH, ICMP) to secure VMs.
  - **Practical Use:** Disabling ICMP can stop ping requests, which helps understand security configurations' impacts.

### 3. Protocols and Their Functions
- **ICMP (Internet Control Message Protocol):** Used for sending error messages and operational information (e.g., ping).
- **SSH (Secure Shell):** Provides secure access to remote devices. Observing SSH traffic helps in understanding secure data transfer.
- **DHCP (Dynamic Host Configuration Protocol):** Automatically assigns IP addresses to devices on a network.
- **DNS (Domain Name System):** Translates domain names into IP addresses, essential for locating devices on the internet.
- **RDP (Remote Desktop Protocol):** Used for remote access to Windows devices, constantly sends data streams for screen updates.

### 4. Troubleshooting Network Issues
- **Identifying Connectivity Problems:** Use ICMP traffic to see if devices can communicate. Lack of responses may indicate a network or security issue.
- **Analyzing Blocked Traffic:** Check NSG rules to see if specific traffic types are being blocked, leading to communication failures.
- **Protocol-Specific Issues:** Understanding protocol behaviors helps in pinpointing where communication breaks down (e.g., blocked SSH might mean port 22 is closed).

### 5. Cloud Resource Management
- **Creating and Deleting Resources:** Learn how to manage VMs and resource groups in Azure, ensuring you only use what you need to avoid extra costs.
- **Best Practices:**
  - Always clean up resources after testing to save on costs.
  - Organize resources into groups for easy management and deletion.
