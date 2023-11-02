<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com)

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

- Create a resource group in Azure that will contain the virtual network and subnet networks
- Create two virtual machines in the resource group that will run Windows OS and Linux respectively 
- Download Wire Shark to analyze protocol traffic between the two virtual machines
- Step 4

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/mi7o6xu.png" height="80%" width="80%" alt="Create Resource Group"/>
</p>
<p>
To start this tutorial you must have a Microsoft Azure account. Please sign up for Microsoft Azure if you haven't already. Once you have signed up with Azure, and created a tenant and subscription group, you need to create a resource group.
To do this type in resource group in the search bar on the dashboard and go to the resource group page. Once there click the "create resource group" button and start filling out the details. For the purpose of this tutorial, we will be naming our resource group Net-tutorial01 but you can name yours whatever you would like. Once you give the resource group a name you can skip the Tags tab and click the "review+create" tab to get your resource group created.
</p>
<br />

<p>
<img src="https://i.imgur.com/WeIjDgW.png" height="80%" width="80%" alt="Virtual Machine Creation"/>
</p>
<p>
  Once the resource group has been created then we will need to create the two virtual machines that are needed for this tutorial. In order to do this, type "virtual machines" into the Azure search bar and head to the virtual machines page. Once there click the "Create" button and start creating your first VM. For this first virtual machine, we will need to have a Windows OS, so 
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
