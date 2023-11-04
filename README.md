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
On this page, we just need to confirm that the virtual network is the same as the virtual network that was chosen for the first virtual machine (in this case VM1 -vnet). We will also leave the subnet at the default option and click "review+ create" at the bottom of the page. Once we reach the validation page we will select "create" and our second virtual machine will be spun up.
</p>
<br />

<p>
<img src="https://i.imgur.com/2fSbjTc.png" height="80%" width="80%" alt="Remote Desktop"/>
</p>
<p>
With the second virtual machine created our initial setup is complete. Our next step is to use our remote desktop program to remote into our first virtual machine with the Windows OS. Windows users will already have remote desktop installed but for Mac users, you will need to go to the app store and download remote desktop.
</p>
<br />

<p>
<img src="https://i.imgur.com/zD9C3Us.png" height="80%" width="80%" alt="Remoting In"/>
</p>
<p>
In order to use remote desktop simply click "Add PC" (this may be different for Windows) and copy your public IP address from your first virtual machine ( you can find this by searching virtual machine in the search bar and clicking the name of your first virtual machine(in our case that would be VM1) and paste it into the PC name section. Once that is done you can click "add". Then after clicking the add button the remote instance will be added and you can just click again to connect. When you attempt to connect you will be prompted with a window asking for a username and password. For this, simply use the same username and password that you established when you created your first virtual machine. Press continue and you will be taken to your remote desktop.
</p>
<br />

<p>
<img src="https://i.imgur.com/zGbEkPP.png" height="80%" width="80%" alt="WireShark"/>
</p>
<p>
  Now that we are inside our remote desktop we want to have the ability to analyze our network traffic and fortunately for us, there is a nifty software called Wireshark that will allow us to do this for free. Search for wireshark using the provided Microsoft Edge browser and click on the wireshark.org page. Once on the page click the "Get started" button which will take you to your installer options. Click Windows x64 Installer and start the installation process. 
</p>
<br />

<p>
<img src="https://i.imgur.com/r6N7fFc.png" height="80%" width="80%" alt="WireShark Installed"/>
</p>
<p>
Now that WireShark has been installed, open up the application and click the Ethernet option on the first page. This should take you to the "capturing from Ethernet" page where you will be shown all of the traffic occurring on your virtual machine. Most of this traffic is generated by behind-the-scenes processes on your VM. Now, to start communicating with our other virtual machine we will start by filtering some of this network traffic. In the filter bar above type in icmp, which stands for Internet Control Messaging Protocol, and click the blue right arrow sign for it to take effect.
</p>
<br />

<p>
<img src="https://i.imgur.com/IPlqCsT.png" height="80%" width="80%" alt="Ping VM2"/>
</p>
<p>
Because we are filtering traffic by ICMP, if we use the ping command to ping our second virtual machine, the traffic will appear in the WireShark console because ping utilizes ICMP. But in order to ping our second virtual machine we need to find its private IP address. This can easily be done by going back to your Azure page and heading to the virtual machine's page and selecting your second virtual machine. In our case, our private IP address is 10.0.05, and so we would want to ping 10.0.05. To start pinging our second VM, open up Powershell and type ping 10.0.0.5. Because there is nothing set up in our second virtual machine to block our ping traffic, each of the four ping requests that are sent from our first virtual machine to our second virtual machine is successful.
</p>
<br />

<p>
<img src="https://i.imgur.com/ErTtENZ.png" height="80%" width="80%" alt="Ping Google"/>
</p>
<p>
Next, let's ping a well-known website like Google.com. To do this we will type ping Google.com into Powershell. As seen in the picture above we received four successful replies from Google's IP address 142.251.16.113.
</p>
<br />

<p>
<img src="https://i.imgur.com/sHnoSJO.png" height="80%" width="80%" alt="Network Security Group"/>
</p>
<p>
Now let's demonstrate what would happen if the ping requests that were sent from our first VM to our second VM were blocked by our second VM's network security group. A network security group contains security rules that can allow or deny inbound and outbound traffic. In order for us to block the pings coming from the first virtual machine we will have to create a security rule in the second VM's network security group that denies ICMP network traffic. To start let's create a continuous ping request to VM2 by typing in the command ping -t 10.0.0.5, the "-t" tells VM1 to send this ping request until we cancel the command. Now let's head back to Microsoft Azure and type in network security groups in the search bar. Once you are on the page, click the network security group that corresponds to your second virtual machine. In our case that would be VM2-nsg. On the next page click "inbound security rules" under settings and then click the "Add" button to add your security rule.
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
