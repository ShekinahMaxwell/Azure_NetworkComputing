<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
<p>In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. Topics covered will be the creation of resources in Azure such as a resource groups, Azure virtual networks and subnets, two Azure virtual machines (Windows-10 and Linux-Ubuntu) and Azure Network Security Groups (Firewall Resource). This will also cover how to use remote Desktop with MacOS and how to perform activites on the Network.</p>

<h2>Overview Diagram</h2>

<p> 
<img width="652" alt="01concept" src="https://github.com/user-attachments/assets/b44681a7-cb42-4c59-ae60-e468199d2155">
</p>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Step 1: Create Resource Group
- Step 2: Create Virtual Network
- Step 3: Create Virtual Machines 1 and 2
- Step 4: Remote desktop instruction for Mac users
- Step 5: Performing activities on the Network we created

<!----------------Step 1: Resource Group Creation------------------->
<h2>Actions and Observations</h2>

<p>
<img width="1303" alt="01" src="https://github.com/user-attachments/assets/699b7dc9-7c3e-4a69-92b7-f6aae4f51da6">
</p>

<p>
Go to portal.azure.com. Assuming you already have an account with a subscription, search resources in the search box and click on create resource group.
</p>
<br />
<!------------------------------------------------------------------>
<p>
<img width="1440" alt="02" src="https://github.com/user-attachments/assets/8552c709-ca12-410f-93a5-5ecd41310f48">
</p>

<p>
Label your resource group and choose the region most appropriate (If you have trouble later on, you may need to just change your region). Click Review + Create. Then click Create.
</p>
<br />
<!------------------------------------------------------------------>
<p>
<img width="1435" alt="04" src="https://github.com/user-attachments/assets/204173e2-d96c-4d8f-8a29-40f978136509">
</p>
<p>
You have just created your first resource group. Congratulations!
</p>
<br />
<!----------------Step 2: Create Virtual Machine 1 and 2------------------->
<p>
<img width="1440" alt="05" src="https://github.com/user-attachments/assets/9eca4c94-da93-4b5a-b8c7-7d8efb807494">
</p>
<img width="1435" alt="06" src="https://github.com/user-attachments/assets/6391272f-fd05-423d-9231-5740d75504b1">
</p>
<p>
Search Virtual Machines in the search bar. Click Create, then click Azure Virtual Machine.
</p>
<br />

<p>
<img width="1436" alt="07" src="https://github.com/user-attachments/assets/50029046-4996-4fde-9688-dd34f4ec3673">
</p>
<p>
<img width="1440" alt="08" src="https://github.com/user-attachments/assets/0d1df2ed-9483-4ef2-8f2f-fb157fb3266f">
</p>
<p>
Select the Resource Group we created earlier. Label your Virtual Machine. It's best practice to write down which region your machines are in because ideally you want them all to be in the same region for this lab (Ex: Previously we selected East US 2 for the Resource Group, so for Virtual Machine 1 we also want to select East US 2). Select Windows 10 for our first computer. Click see all sizes and Standard _E2s_v3 - 2vcpus, 16 GiB memory. Remember your username and password!
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
