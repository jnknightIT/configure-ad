<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of Active Directory within Azure Virtual Machines.<br />




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Creating a Resource Group with Server and Client
- Configuring TCP Proctols in Windows Firewall
- Installing Active Directory and User Groups
- Connecting Virtual Machine to Cloud Server and Adding Users

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/8nu5gTm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/ufOyxOy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/MU8bk0K.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Within Azure, create two virtual machines. Select "Window Data server 2022" for the first operating system.  The second VM will be "Windows 10". The domain server will be named "DC-1" and the user will be named "Client". To ensure that the IP address of the server doesn't change throughout the process, change DC-1's IP to static in the netword settings. Set Client's dns to DC-1's static ip. From Client open PowerShell and run "ipconfig /all". The output for the DNS settings should show DC-1’s private IP Address.
</p>
<br />

<p>
<img src="https://i.imgur.com/h4ysuxf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/HARpSBB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/WjuD1WL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
On DC-1 install Active Directory Domain Services. Setup a new forest. Restart and then log back into DC-1 as the new domain created and the pre-existing username. Create Organizational Units and a couple of users. Give one of the users administrator properties by right-clicking on the user, selecting "properties", select "member" tab and add them to "Domain Admins" group. Click "check names" button after typing in "domain admins" to re-affirm the existence of the group name. On Client join it to the domain (System -> Rename this PC -> Change... -> Domain)
</p>
<br />

<p>
<img src="https://i.imgur.com/J9NRIZm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://github.com/ashep1337/configure_ad/blob/main/Login%20as%20new%20user%20to%20server.png?raw=true" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Logged back into the client machine with the admin user login and allowed domain users access to remote desktop via system properties. on DC-1 create a employee OU and add users. 
  Lastly, pick a random user from the OU and log into the client machine.
</p>
<br />
