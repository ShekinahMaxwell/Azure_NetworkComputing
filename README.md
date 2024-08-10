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
You have just created your first resource group. Congratulations! Next we will create our virtual network and our first virtual machine.
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
<img width="1440" alt="09" src="https://github.com/user-attachments/assets/94033e6e-cb8b-4f6e-9a32-86c27ab59e11">
</p>
<p> 
<img width="1440" alt="10" src="https://github.com/user-attachments/assets/6fea21cc-6916-4f43-aa1b-920693ec159a">
</p>
<p>
<img width="1440" alt="11" src="https://github.com/user-attachments/assets/a8e8dc7a-98ec-48bc-98a2-0c6525186efe">
</p>
<p>
<img width="1440" alt="12" src="https://github.com/user-attachments/assets/376fe6aa-2119-4af0-a428-cb0415a052af">
</p>

<p>
Select the Resource Group we created earlier. Label your Virtual Machine. It's best practice to write down which region your machines are in because ideally you want them all to be in the same region for this lab (Ex: Previously we selected East US 2 for the Resource Group, so for Virtual Machine 1 we also want to select East US 2). Select Windows 10 for our first computer. Click see all sizes and Standard _E2s_v3 - 2vcpus, 16 GiB memory. Remember your username and password! Click Review+Create. We have created our Network and VM1. 
</p>
<br />

<p>
<img width="1440" alt="13 checkpoint should get this screen" src="https://github.com/user-attachments/assets/7989ab5f-1db7-4b9d-a4ac-c90a126d0e8e">
</p>
<p>
Check Point. You should have a screen that appears as this with a virtual machine 1 created (VM1), a network security group (NSG), a virtual network interface card (NIC), a public ip address, and a virtual network. Time to create our second virtual machine.
</p>
<br />

<p>
<img width="1433" alt="15create2ndVM" src="https://github.com/user-attachments/assets/a08441d2-616a-46bd-b8d5-579b07f80537">
</p>
<p>
<img width="1440" alt="16" src="https://github.com/user-attachments/assets/3a72b762-4bb8-4abb-bc8d-eee34a976c26">
</p>
<p>
Search for virtual machines in the search bar and click Create. 
</p>
<br />

<p>
<img width="1440" alt="17" src="https://github.com/user-attachments/assets/d7b73dbc-2ef5-4424-8fa4-1e37ecde177e">
</p>
<p>
Choose the same resource group that VM1 is in. Name the machine VM2 and choose the same region you have selected for VM1.
</p>
<br />

<p>
<img width="1440" alt="18" src="https://github.com/user-attachments/assets/742a32ca-1801-4e1f-ac5f-527a806d7fef">
</p>
<p>
<img width="1437" alt="19" src="https://github.com/user-attachments/assets/ec81db97-fbcc-4fbd-86cd-9d91e20c5e6a">
</p>
<p>
Select Ubuntu for this virtual machine and pick your username and password (For the sake of this practice lab you can use the same login info that VM1 has, since we will delete everything at the end of the lab).
</p>
<br />

<p>
<img width="1440" alt="20" src="https://github.com/user-attachments/assets/8ef4e505-70f8-42bf-b87d-d2495a373a52">
</p>
<p>
<img width="1431" alt="21" src="https://github.com/user-attachments/assets/8875e361-ee8a-4412-aaa6-53fbc107bec8">
</p>
<p>
<img width="1440" alt="22" src="https://github.com/user-attachments/assets/4d12bf59-8d71-40d4-bc43-1a60b8b37bde">
</p>
<p>
<img width="1440" alt="23final product " src="https://github.com/user-attachments/assets/c4680a41-ec7f-4f3a-ac4a-fa1cf448b6ea">
</p>
<p>
Check Point. Here we have the same products for our VM2 that we did for VM1.
</P>
<br />
