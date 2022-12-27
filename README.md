<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Windows Server 2019 Datacenter (1809)

<h2>High-Level Steps</h2>

- Create sample file share folders with permissions
- Access file shares as a normal users
- Create an "ACCOUNTANTS" Sccurity Group, assign permissions, and test access

<h2>Actions and Observations</h2>

<h3>Create sample file share folders with permissions</h3>

<p>
<img src="https://i.imgur.com/ulODls5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create 2 instances of your remote desktop and login you domain controller as an admin and your client PC as one of the users.
</p>
<br />

<p>
<img src="https://i.imgur.com/802hsrZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From your domain controller click on the Windows Explorer icon on your taskbar-->This PC-->Click on your C: drive to open its contents.
</p>
<br />

<p>
<img src="https://i.imgur.com/1DohoPM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From your domain controller in the C:\ drive create 4 folders: "read-access", "write-access", "no-access", and "accounting".
</p>
<br />

<p>
<img src="https://i.imgur.com/bgCYhn3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In Windows C:\ drive right click the folder-->hover to Properties-->Click on the Sharing Tab-->Click on Share from the Sharing tab-->Type Domain Users in the bar above the name and permission level. 

There will be a drop down menu that will allow you to select the permission level for your domain users.  Check "Read" for the read-access folder, "Read/Write" for the write-access folder. Instead of adding domain users in the no-access folder, we will use domain admins instead and provide them with "Read/Write" access.  This will give normal users no access to that folder. 

We will go to the client PC and check folders for access in the following steps.
</p>
<br />

<p>
<img src="https://i.imgur.com/Z8kDOs0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Once your permissions are set there, you can send  and email of that shared folder or share the link into another app.  In the individual items section, there will be a file path that you can copy and paste in a windows explorer search box that will take you to that specific folder.
</p>
<br />

<p>
<img src="https://i.imgur.com/PW1fiMv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open each folder and create a text document that we can test for access when we log into the client virtual machine as a domain user.  To create the document, right click on each folder-->hover to New-->hover to text document and click.
</p>
<br />

<p>
<img src="https://i.imgur.com/L2W3COP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Once your file is created, type a sample text, go to File>Save As-->Name your file-->Click Ok.
</p>
<br />

<h2>Attempt to access file shares as a normal user</h2>
<p>
<img src="https://i.imgur.com/E5yyzi2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
On Client-1, navigate to the shared by typing Run in the search bar-->type \\DC-1-->The network folder should populate in a new window.
</p>
<br />

<p>
<img src="https://i.imgur.com/qHHhIZ9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open the read-access folder-->Open your test file-->Attempt to edit the text and save the document. A dialog box will show that you have read access only.
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
