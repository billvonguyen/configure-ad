<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Set up resources in Azure
- Ensure connection between client and Domain controller
- Install Active Directory
- Download and install Powershell

<h2>Deployment and Configuration Steps</h2>

<p>
</p>
<p>
1. So out first step is to create a "Domain Controller" and a "Client" virtual machines for our Active Directory. To do so we must sign into our Azure account at portal.azure.com and navigate to virtual machines and create two seperate virtual machines.
</p>
<img src="https://i.imgur.com/vGQmO2W.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<br />
<p>
  2. For our domain controller, we'll name it "DC-1" and set the region to "West US 3", as for the next two options it can be left alone, and for the "Image" make sure that is set to "Windows Server 2022".
<p>
<img src="https://i.imgur.com/W1FLoUK.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
3. Create a "username" and "password" for our Virtual machine, please take note of this information so that you don't forget it. And set the "Size" of the virtual machine to "Standard, 2vcpus" as shown in the screenshot below. Also make sure to check the box by "Would you like to use a existing Windows Server License" under "Licensing" and check the box right under it for the confirmation then proceed and click on "Review and Create".
</p>
<img src="https://i.imgur.com/oTsv3sU.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<br />

<p>
4. Next step is to create a Virtual Machine for our client and you'll be repeating the same steps in the first one with a few adjustments. We'll name this virtual machine "Client-1", same region and security type and image will be "Windows 10". Make sure that both Virtual Machines are in the same resource group as well.
  
</p>
<img src="https://i.imgur.com/zNpreOh.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<p>
5. Same as in our previous virtual machine, create a "username" and "password" and please take note of it so you don't forget. Also with the same "Size" set at "Standard, 2vcpus", confirm and proceed with "Next".
  
</p>
6. Once you get to "Network Interface" click on and set the "Virtual Network" to the same as your "Domain Controller" and click on "Review + Create"

<img src="https://i.imgur.com/CRoJU7N.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<p>
7. Navigate back to "Virtual Machines" then click on "Networking" and then right beside "Network Interface:" click on "DC-1164" as shown in the screenshot below, the numbers and name maybe different depending on the name of your "Domain Controller".
</p>
<img src="https://i.imgur.com/kHYhspw.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<br />
<p>
8. Click on "Ip configurations" then the Ip address as shown below and set the address type to Static.
<img src="https://i.imgur.com/R9M0ZDt.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/1wAUwLN.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
9. Next step is to check our connection between the two Virtual Machines, so click on the "Client" Virtual Machine and copy the public ip address as shown in the screenshot below.
</p>    
<img src="https://i.imgur.com/wjWiFQI.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<p>
10. Search up and start "Remote Desktop Connection" within your operating system's search bar then enter in the ip address that you copied.
<img src="https://i.imgur.com/BD9FlDi.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
11. When prompted, login using the username and password you set up for Client's virtual machine.
</p>
<img src="https://i.imgur.com/b05SeMI.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<p>
12. Next we'll want to grab the private ip address for our "Domain Controller" so that we can check the connection between our two virtual machines. Head back to portal.azure.com and click on the Domain Controller's virtual machine and copy the private ip under "Networking".
<img src="https://i.imgur.com/L6zmOZz.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>  
</p>

<p>
13. Head back to the "Remote Desktop Connection" of "Client" and type in "cmd" and run the program, from there type in "ping -t 10.2.0.4". 
</p>
<img src="https://i.imgur.com/27RFbgW.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>  

<p>
14. Open up another remote desktop connection for your Domain Controller virtual machine using the login credentials you created earlier and entering it's public ip address. Then start up "Server Manager" if it's not up already, you can do so by searching up "Server Manager" within the search box. 
</p>
<img src="https://i.imgur.com/kxJCrrE.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>  
<p>
15. From within "Server Manager" click on "Add Roles", then proceed with next until you get to "Server Roles" then click on the checkbox by "Active Directory Domain Services", add features then continue with next and install.
</p>
<img src="https://i.imgur.com/fju7okX.png" height="50%" width="50%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/OJTFrrS.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>  

<p>
16. When the install finishes, click on "promote this server to domain controller" under the exclamation mark notification on the top right of the window.
</p>
<img src="https://i.imgur.com/42LFQ8k.png" height="50%" width="50%" alt="Disk Sanitization Steps"/> 
<p>
17. Take note just incase, but enter in a domain name of your choosing then proceed with next.
</p>
<img src="https://i.imgur.com/4LvzICR.png" height="50%" width="50%" alt="Disk Sanitization Steps"/> 
<p>
18. Followed by a password of your choosing, and please take note of it just incase, then proceed with next and install and restart the virtual machine once it's finished installing.
</p>
<img src="https://i.imgur.com/lUWI9Gl.png" height="50%" width="50%" alt="Disk Sanitization Steps"/> 





