# Learning Notes: Networking and Security Exploration on Azure

## Overview
This document contains detailed learning notes from the "Networking and Security Exploration on Azure" project. It highlights key concepts, practical skills, and knowledge gained during the project, focusing on network monitoring, security configurations, and troubleshooting within an Azure environment.

---

### 1. Network Monitoring with Wireshark

- **Purpose:**  
  Wireshark is used to capture and analyze network traffic. It helps in identifying how data flows between devices, diagnosing network issues, and understanding protocol behavior in real-time.

- **Key Points to Remember:**
  - **Filters:** Use filters (e.g., `icmp`, `ssh`, `dns`) to isolate specific traffic types for focused analysis.
  - **Traffic Analysis:** Observing ping requests and responses helps determine connectivity between devices, useful in diagnosing basic network issues.
  - **Protocol Behavior:** Different protocols have specific patterns; understanding these helps in identifying normal vs. abnormal traffic.

- **Real-World Application:**  
  Wireshark is frequently used in IT support roles to troubleshoot network issues, such as slow performance or connection problems, by analyzing packet data.

- **Common Mistakes and Solutions:**
  - **Mistake:** Incorrect filter syntax leading to missing critical traffic.  
    **Solution:** Double-check filter expressions and use the autocomplete suggestions within Wireshark to avoid errors.
  - **Mistake:** Failing to capture traffic on the correct interface.  
    **Solution:** Ensure you select the correct network adapter before starting the capture.

---

### 2. Configuring Network Security Groups (NSGs)

- **Purpose:**  
  NSGs act as firewalls to control inbound and outbound traffic for Azure Virtual Machines, enhancing security by managing access based on IP addresses, ports, and protocols.

- **Key Points to Remember:**
  - **Rules:** NSGs use rules to allow or deny traffic based on specific criteria. Configurations can be customized to secure VMs effectively.
  - **Common Configurations:** 
    - Allow ICMP to enable pinging between VMs.
    - Block specific traffic types (e.g., SSH, ICMP) to secure VMs from unauthorized access.
  - **Practical Use:** Disabling ICMP can stop ping requests, useful in testing and validating security configurations.

- **Real-World Application:**  
  NSGs are commonly used in cloud environments to restrict access to sensitive systems, ensuring only authorized users can connect, and are vital in implementing security best practices.

- **Common Mistakes and Solutions:**
  - **Mistake:** Misconfigured rules blocking essential traffic.  
    **Solution:** Regularly review NSG rules, especially after changes, to ensure critical services are not inadvertently blocked.
  - **Mistake:** Rule priority conflicts leading to unexpected behavior.  
    **Solution:** Understand that NSG rules are processed in priority order; adjust rule priorities to ensure the correct rules are applied.

- **Commands to Remember:**
  - **PowerShell to Create NSG Rule:**  
    ```powershell
    New-AzNetworkSecurityRuleConfig -Name "Allow-ICMP" -Protocol "ICMP" -Direction "Inbound" -Priority 100 -SourceAddressPrefix "Any" -SourcePortRange "*" -DestinationAddressPrefix "Any" -DestinationPortRange "*" -Access "Allow"
    ```

---

### 3. Protocols and Their Functions

- **ICMP (Internet Control Message Protocol):**  
  Used for sending error messages and operational information (e.g., ping). Critical for testing connectivity and diagnosing network issues.

- **SSH (Secure Shell):**  
  Provides secure command-line access to remote devices. Observing SSH traffic helps understand secure data transfers and access controls.

- **DHCP (Dynamic Host Configuration Protocol):**  
  Automatically assigns IP addresses to devices on a network. Analyzing DHCP traffic can help identify configuration issues related to IP assignment.

- **DNS (Domain Name System):**  
  Translates domain names into IP addresses, essential for locating devices on the internet and internal networks. DNS issues often lead to connectivity problems.

- **RDP (Remote Desktop Protocol):**  
  Used for remote access to Windows devices, constantly sending data streams for screen updates, which is critical for IT support and administration tasks.

---

### 4. Troubleshooting Network Issues

- **Identifying Connectivity Problems:**  
  Use ICMP traffic to verify device communication. Lack of responses usually indicates a network or security issue, such as incorrect NSG settings.

- **Analyzing Blocked Traffic:**  
  Check NSG rules to see if specific traffic types (e.g., SSH) are being blocked, leading to communication failures. Use Wireshark filters to confirm traffic flows as expected.

- **Protocol-Specific Issues:**  
  Understanding protocol behaviors helps pinpoint where communication breaks down:
  - **Blocked SSH:** Often indicates that port 22 is closed by an NSG or firewall rule.
  - **DHCP Issues:** Look for failed IP requests to diagnose address allocation problems.

- **Common Troubleshooting Scenarios:**
  - **Scenario:** Cannot SSH into a VM.  
    **Solution:** Check if the NSG allows SSH traffic and verify the server is accepting connections on the correct port.
  - **Scenario:** Ping requests are failing.  
    **Solution:** Ensure ICMP is allowed in the NSG rules; use Wireshark to see if ICMP packets are reaching the destination.

---

### 5. Cloud Resource Management

- **Creating and Deleting Resources:**  
  Managing VMs and resource groups in Azure efficiently ensures that you only use necessary resources, minimizing costs and reducing security risks.

- **Best Practices:**
  - Always clean up resources after testing to save on costs. Use tags to label resources for easy identification during cleanup.
  - Organize resources into groups for easier management and policy application. Regularly review resource usage to identify unused or unnecessary assets.

- **Real-World Application:**  
  Effective resource management is crucial in cloud environments to avoid unexpected charges and ensure that all deployed resources are secure and compliant with organizational policies.

---
