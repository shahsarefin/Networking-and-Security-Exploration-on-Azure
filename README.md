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

<h4>Step-by-Step Instructions:</h4>
<ol>
  <li>Create a Resource Group:
    <ul>
      <li>Go to the Azure Portal (<a href="https://portal.azure.com">portal.azure.com</a>).</li>
      <li>Click "Resource Groups" > "Create."</li>
      <li>Name the Resource Group (e.g., `Network-Security-Lab`) and select a region.</li>
      <li>Click "Review + Create" and then "Create" to finalize.</li>
    </ul>
  </li>

  <li>Create a Virtual Network:
    <ul>
      <li>Navigate to "Virtual Networks" and click "Create."</li>
      <li>Set the name to `Network-Lab-VNet`, choose your resource group, and select the region.</li>
      <li>Set the address space (e.g., `10.0.0.0/16`) and create a subnet (e.g., `Subnet-1` with `10.0.1.0/24`).</li>
      <li>Click "Review + Create" and then "Create."</li>
    </ul>
  </li>

  <li>Create the Windows 10 VM:
    <ul>
      <li>Go to "Virtual Machines" and click "Create" > "Azure Virtual Machine."</li>
      <li>Name the VM `Windows-VM`, select the Windows 10 image, and choose your resource group and VNet.</li>
      <li>Set the authentication to password, and enter a username and password (e.g., Username: `labuser`, Password: `SecurePass123!`).</li>
      <li>Ensure the VM is in the same VNet and subnet created earlier.</li>
      <li>Click "Review + Create" and then "Create."</li>
    </ul>
  </li>

  <li>Create the Ubuntu VM:
    <ul>
      <li>Repeat the VM creation steps, but select the Ubuntu Server 20.04 image.</li>
      <li>Name the VM `Ubuntu-VM`, and ensure it’s placed in the same VNet and subnet.</li>
      <li>Use SSH keys or set a password for authentication.</li>
      <li>Click "Review + Create" and then "Create."</li>
    </ul>
  </li>
</ol>

---

<!-- Step 2: Observing ICMP Traffic -->
<h3>Step 2: Observing ICMP Traffic</h3>
<p>Using Wireshark on the Windows VM, we filter ICMP traffic to observe ping requests and responses between the Windows and Ubuntu VMs. This demonstrates basic connectivity and network communication within the virtual network.</p>
<p align="center">
  <img src="INSERT_IMAGE_URL" alt="ICMP Traffic Observation" width="80%"/>
</p>

<h4>Step-by-Step Instructions:</h4>
<ol>
  <li>Install Wireshark on the Windows VM:
    <ul>
      <li>RDP into the Windows VM using Remote Desktop Connection.</li>
      <li>Download Wireshark from <a href="https://www.wireshark.org/">wireshark.org</a> and install it.</li>
    </ul>
  </li>

  <li>Start Capturing ICMP Traffic:
    <ul>
      <li>Open Wireshark and start a new capture on the main network interface.</li>
      <li>In the filter box, type `icmp` to isolate ICMP traffic.</li>
    </ul>
  </li>

  <li>Ping the Ubuntu VM from the Windows VM:
    <ul>
      <li>Open Command Prompt and run <code>ping [Ubuntu-VM Private IP]</code>.</li>
      <li>Observe the ICMP requests and replies in Wireshark, confirming connectivity.</li>
    </ul>
  </li>
</ol>

---

<!-- Step 3: Configuring Network Security Groups -->
<h3>Step 3: Configuring Network Security Groups (NSGs)</h3>
<p>We configure NSGs to control traffic flow to the Ubuntu VM by disabling and then re-enabling ICMP traffic. This step showcases the importance of NSGs in managing network security and access.</p>
<p align="center">
  <img src="INSERT_IMAGE_URL" alt="Configuring NSGs" width="80%"/>
</p>

<h4>Step-by-Step Instructions:</h4>
<ol>
  <li>Configure NSG for the Ubuntu VM:
    <ul>
      <li>Navigate to "Network Security Groups" in the Azure Portal and click "Create."</li>
      <li>Name the NSG (e.g., `Ubuntu-NSG`) and assign it to the resource group.</li>
      <li>Once created, go to the NSG settings and add an inbound security rule to allow ICMP traffic:
        <ul>
          <li>Set source and destination to `Any`, protocol to `ICMP`, and action to `Allow`.</li>
          <li>Name the rule `Allow-ICMP` and save.</li>
        </ul>
      </li>
      <li>Associate the NSG with the Ubuntu VM’s network interface.</li>
    </ul>
  </li>

  <li>Testing NSG Rules:
    <ul>
      <li>Ping the Ubuntu VM again from the Windows VM to confirm ICMP traffic is allowed.</li>
      <li>Modify the NSG rule to deny ICMP and test to ensure pings are blocked, demonstrating NSG’s effect on traffic control.</li>
    </ul>
  </li>
</ol>

---

<!-- Step 4: Inspecting SSH, DHCP, DNS, and RDP Traffic -->
<h3>Step 4: Inspecting SSH, DHCP, DNS, and RDP Traffic</h3>
<p>Using Wireshark, we inspect various network protocols to understand how different types of traffic behave within the virtual network. Each protocol demonstrates specific scenarios, such as remote access (SSH), IP configuration (DHCP), domain resolution (DNS), and remote desktop connections (RDP).</p>
<p align="center">
  <img src="INSERT_IMAGE_URL" alt="Observing SSH Traffic" width="80%"/>
</p>

<h4>Step-by-Step Instructions:</h4>
<ol>
  <li>Inspect SSH Traffic:
    <ul>
      <li>From the Windows VM, use a terminal to SSH into the Ubuntu VM (`ssh labuser@[Ubuntu-VM Private IP]`).</li>
      <li>In Wireshark, use the filter `ssh` to capture the SSH traffic, observing the secure connection setup.</li>
    </ul>
  </li>

  <li>Inspect DHCP Traffic:
    <ul>
      <li>In Wireshark, filter for DHCP traffic (`bootp`) and observe IP address requests and assignments.</li>
      <li>Renew the IP address on the Windows VM using `ipconfig /renew` in Command Prompt to see DHCP interactions.</li>
    </ul>
  </li>

  <li>Inspect DNS Traffic:
    <ul>
      <li>Use the command `nslookup [website.com]` to observe DNS requests and responses in Wireshark (`dns` filter).</li>
    </ul>
  </li>

  <li>Inspect RDP Traffic:
    <ul>
      <li>Filter for RDP traffic (`tcp.port == 3389`) to see the continuous stream of RDP data, demonstrating live remote desktop connections.</li>
    </ul>
  </li>
</ol>

---

<!-- Lab Cleanup -->
<h3>Lab Cleanup</h3>
<p>After completing all observations, we clean up the Azure environment by deleting the resource groups and VMs. This step ensures no unnecessary costs are incurred and that resources are managed efficiently.</p>
<p align="center">
  <img src="INSERT_IMAGE_URL" alt="Lab Cleanup" width="80%"/>
</p>

<h4>Step-by-Step Instructions:</h4>
<ol>
  <li>Stop the VMs:
    <ul>
      <li>Go to each VM in the Azure Portal and click "Stop" to avoid incurring costs while not in use.</li>
    </ul>
  </li>

  <li>Delete the Resource Group:
    <ul>
      <li>Once you're done, delete the entire resource group to clean up all associated resources.</li>
      <li>Navigate to "Resource Groups," select your group, click "Delete Resource Group," and confirm.</li>
    </ul>
  </li>
</ol>

---

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
