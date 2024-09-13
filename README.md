# Networking-and-Security-Exploration-on-Azure
<p align="center">
  <img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Networking and Security Exploration on Azure</h1>
In this project, we conduct network security and traffic analysis experiments using Azure Virtual Machines, Wireshark, and Network Security Groups (NSGs). The lab demonstrates the management of network traffic and security in a cloud environment, highlighting practical skills in monitoring, troubleshooting, and configuring secure access controls.

<h2>Environments and Technologies Used</h2>
<ul>
  <li>Microsoft Azure (Virtual Machines/Compute)</li>
  <li>Remote Desktop</li>
  <li>Various Command-Line Tools</li>
  <li>Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)</li>
  <li>Wireshark (Protocol Analyzer)</li>
</ul>

<h2>Operating Systems Used</h2>
<ul>
  <li>Windows 10 (21H2)</li>
  <li>Ubuntu Server 20.04</li>
</ul>

<h2>High-Level Steps</h2>
<ol>
  <li>Create Azure Virtual Machines (Windows and Linux)</li>
  <li>Observe and Analyze ICMP Traffic with Wireshark</li>
  <li>Configure Network Security Groups (NSGs) to Control Traffic</li>
  <li>Inspect SSH, DHCP, DNS, and RDP Traffic</li>
  <li>Clean Up Azure Resources</li>
</ol>

<h2>Actions and Observations</h2>

<!-- Step 1: Creating Azure Virtual Machines -->
<h3>Step 1: Creating Azure Virtual Machines</h3>
<p>We start by creating two virtual machines—one Windows 10 VM and one Ubuntu VM—within the same virtual network in Azure. This setup allows us to simulate real-world networking scenarios.</p>
<p align="center">
  <img src="INSERT_IMAGE_URL" alt="Creating Virtual Machines" width="80%"/>
</p>
<p>Description of the setup process, including resource group creation, network configuration, and VM settings.</p>

<!-- Step 2: Observing ICMP Traffic -->
<h3>Step 2: Observing ICMP Traffic</h3>
<p>Using Wireshark on the Windows VM, we filter ICMP traffic to observe ping requests and responses between the Windows and Ubuntu VMs. This demonstrates basic connectivity and network communication within the virtual network.</p>
<p align="center">
  <img src="INSERT_IMAGE_URL" alt="ICMP Traffic Observation" width="80%"/>
</p>
<p>Detailed observations of ICMP traffic between the VMs, including any issues encountered and how they were resolved.</p>

<!-- Step 3: Configuring Network Security Groups -->
<h3>Step 3: Configuring Network Security Groups (NSGs)</h3>
<p>We configure NSGs to control traffic flow to the Ubuntu VM by disabling and then re-enabling ICMP traffic. This step showcases the importance of NSGs in managing network security and access.</p>
<p align="center">
  <img src="INSERT_IMAGE_URL" alt="Configuring NSGs" width="80%"/>
</p>
<p>Explanation of the configuration changes made to the NSGs and the impact on traffic as observed in Wireshark.</p>

<!-- Step 4: Inspecting SSH, DHCP, DNS, and RDP Traffic -->
<h3>Step 4: Inspecting SSH, DHCP, DNS, and RDP Traffic</h3>
<p>Using Wireshark, we inspect various network protocols to understand how different types of traffic behave within the virtual network. Each protocol demonstrates specific scenarios, such as remote access (SSH), IP configuration (DHCP), domain resolution (DNS), and remote desktop connections (RDP).</p>
<p align="center">
  <img src="INSERT_IMAGE_URL" alt="Observing SSH Traffic" width="80%"/>
</p>
<p>Observations of SSH traffic when connecting to the Ubuntu VM, including command interactions and security considerations.</p>

<p align="center">
  <img src="INSERT_IMAGE_URL" alt="Observing DHCP Traffic" width="80%"/>
</p>
<p>Details of DHCP traffic when renewing IP addresses on the VMs and what this means in a network management context.</p>

<p align="center">
  <img src="INSERT_IMAGE_URL" alt="Observing DNS Traffic" width="80%"/>
</p>
<p>Insights into DNS traffic, illustrating the process of domain name resolution and its importance for connectivity.</p>

<p align="center">
  <img src="INSERT_IMAGE_URL" alt="Observing RDP Traffic" width="80%"/>
</p>
<p>Analysis of RDP traffic, highlighting the continuous data flow and its implications for remote monitoring and control.</p>

<!-- Lab Cleanup -->
<h3>Lab Cleanup</h3>
<p>After completing all observations, we clean up the Azure environment by deleting the resource groups and VMs. This step ensures no unnecessary costs are incurred and that resources are managed efficiently.</p>
<p align="center">
  <img src="INSERT_IMAGE_URL" alt="Lab Cleanup" width="80%"/>
</p>
<p>Confirmation of resource deletion and best practices for managing cloud resources.</p>

<h2>Purpose of the Lab</h2>
<p>
  The main purpose of this lab is to gain hands-on experience in monitoring and managing network traffic between virtual machines in a cloud environment. By analyzing network traffic and configuring Network Security Groups (NSGs), this lab demonstrates practical skills in controlling network access, understanding protocol behavior, and troubleshooting connectivity issues within a secure cloud setup.
</p>

<h2>Key Learnings</h2>
<ul>
  <li><strong>Network Monitoring Skills:</strong> Gained experience in using Wireshark to capture and analyze traffic between virtual machines, an essential skill for diagnosing network-related issues.</li>
  <li><strong>Security Configuration:</strong> Learned how to configure Network Security Groups (NSGs) to manage and secure network access between virtual machines, emphasizing the role of firewalls in cloud environments.</li>
  <li><strong>Protocol Analysis:</strong> Observed various network protocols (ICMP, SSH, DHCP, DNS, RDP) in action, gaining an understanding of their functions and importance in network communication.</li>
  <li><strong>Troubleshooting Network Issues:</strong> Developed troubleshooting skills by identifying and resolving issues with network traffic and configuration settings.</li>
  <li><strong>Cloud Resource Management:</strong> Learned to manage and clean up cloud resources effectively, ensuring efficient use and cost management of Azure resources.</li>
</ul>

<h2>Concepts Taught by This Lab</h2>
<ul>
  <li><strong>Network Traffic Analysis:</strong> Understanding how to monitor and analyze network traffic using protocol analyzers like Wireshark, which is crucial for maintaining secure and efficient networks.</li>
  <li><strong>Security Management:</strong> Using Network Security Groups to control and secure access to virtual machines, illustrating key concepts of network security management.</li>
  <li><strong>Understanding Protocol Behavior:</strong> Analyzing common network protocols and their behavior to better understand how data is transmitted and secured across networks.</li>
  <li><strong>Real-World IT Support Scenarios:</strong> Simulating real-world IT support scenarios that involve monitoring, troubleshooting, and securing network environments.</li>
</ul>

<h2>Summary</h2>
<p>This project demonstrates a practical understanding of managing network traffic and security within Azure environments. By using Wireshark and configuring Network Security Groups, we gain insights into how different types of traffic behave and how they can be controlled to enhance security and performance.</p>
