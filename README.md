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
  Once the resource group has been created then we will need to create the two virtual machines that are needed for this tutorial. In order to do this, type "virtual machines" into the Azure search bar and head to the virtual machines page. Once there click the "Create" button and start creating your first VM. For this first virtual machine, we will need to select our Resource Group ( which we created in the prior step), give our VM a name ( I choose VM1 but you can name it whatever you would like), select your Region( depending on where you are located, for example, if you live in New York City you would probably want to choose East US), choose your Image/ OS ( we want a Windows OS and so we would select Windows 10 Pro, version 22HS - x64 Gen 2), select a size (this involves deciding virtual CPU and RAM resources and selecting Standard_E2s_v3(2 vpcus with 16GiB of memory) should be sufficient enough) and then lastly create your admin account by creating a username and password. You can use the default options for inbound port rules, availability zones, and availability options. Once you have filled out the basics page you then head over to the Networking tab up top.
</p>
<br />

<p>
<img src="https://i.imgur.com/w4FNSya.png" height="80%" width="80%" alt="Networking Tab on Virtual Machine Page"/>
</p>
<p>
Once we are on the networking page, a virtual network, subnet, and public IP address should be already created for us by default. The Subnet IP will be important later because this is what we will use to communicate with the Linux VM that we will be creating in the next step. It will also be essential for us to select the same virtual network (VM-1 -vnet or in your case the name may be different) for the second VM to ensure that both VMs are operating under the same umbrella virtual network. After reviewing this page, click "review+create" at the bottom which should take you to the validation page. On the validation page click "create" at the bottom and your first VM will begin being spun up.
</p>
<br />

<p>
<img src="https://i.imgur.com/5TKwrzD.png" height="80%" width="80%" alt="Second Virtual Machine Creation"/>
</p>
<p>
Now that the first virtual machine has been created we can move on to creating our second virtual machine. We would mimic the same steps as above with some minor adjustments. Because we will be using a Linux OS for this virtual machine we will select Ubuntu Server 20.04 LTS - x64 Gen2 as the Image. Also, we will need to give this virtual machine a different name ( we chose VM2 but you can name this VM whatever you like). As you head to the bottom of the page you will notice that the authentication type defaulted to SSH public key, we will want to select "password" instead and create a username and password for this VM. After this is done head over to the networking tab.
</p>
<br />

<p>
<img src="https://i.imgur.com/TQPxZe6.png" height="80%" width="80%" alt="Networking Tab Two on Virtual Machine Page"/>
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
