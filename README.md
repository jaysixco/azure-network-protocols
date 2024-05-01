# azure-network-protocols

<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>Network FIle Shares and Permissions </h1>
<strong> General Idea: </strong><br>
Creating four folders in DC-1 and telling Client-1's user what they're allowed to do it (will they be able to write in it, or just read it, or even have access to it at all). <br>
Create the security group before you even create the folders, so that you can just set conditions for them all in one go. <br>
For this step, have in mind the Client-1 username you plan to use. <br>
After all that is done, THEN log into Client-1 with whatever user you choose. <br>

<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Item 1
- Item 2
- Item 3
- Item 4
- Item 5

<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<strong> Create some sample file shares with various permissions </strong><br>
<strong> Note: ORDER MATTERS! Log in to DC-1 first in order to get a user to log into Client-1 with </strong><br>
<strong> Log into DC-1 as mydomain.com\jane_admin </strong><br>
<strong> Log into Client-1 as a normal user (mydomain\<someuser>) </strong><br>
<strong> In DC-1, on the C:\ drive, create 4 folders: “read-access”, “write-access”, “no-access”, “accounting” </strong><br><br> 
<strong> Set the following permissions (share the folder) for the “Domain Users” group: </strong><br>
&nbsp;&nbsp; - Right click folder > Properties> Sharing tab> Share> Type in full name of group (ex: "domain users" vs "domain"> Add> Set permission level> Share <br>
<strong> Folder: “read-access”, Group: “Domain Users”, Permission: “Read” </strong><br>
<strong> Mnemonic: </strong> D. U. read  <br>
<strong> Folder: “write-access”,  Group: “Domain Users”, Permissions: “Read/Write” </strong><br>
<strong> Mnemonic: </strong> D.U. read or write <br>
<strong> Folder: “no-access”, Group: “Domain Admins”, “Permissions: “Read/Write” </strong><br>
<strong> Mnemonic: </strong> DAd I no READ OR WRITE <br>
<strong> (Skip accounting for now) </strong> <br>
<strong> Mnemonic: </strong> ACCOUNTANTS READ & WRITE <br>

<strong> Attempt to access file shares as a normal user </strong> (<em>honestly, can skip this part for now) </em>
On Client-1, navigate to the shared folder (start, run, \\dc-1) <br>
Try to access the folders you just created. Which folders can you access? Which folders can you create stuff in? Does it make sense? <br>

<strong> Create an “ACCOUNTANTS” Security Group, assign permissions, an test access </strong><br>
<strong> Go back to DC-1, in Active Directory, create a security group called “ACCOUNTANTS” </strong><br>
On the “accounting” folder you created earlier, set the following permissions: <br>
<strong> Folder: “accounting”, Group: “ACCOUNTANTS”, Permissions: “Read/Write” <br>
On Client-1, as  <someuser>, try to access the accountants folder. It should fail. <br>
Log out of Client-1 as  <someuser> <br>
On DC-1, make <someuser> a member of the “ACCOUNTANTS”  Security Group <br>
Sign back into Client-1 as <someuser> and try to access the “accounting” share in \\DC-1\ - Does it work now? <br>


Essential steps: <br>
Login to DC-1 as mydomain.com\jane_admin (line 44) <br> 
In DC-1:  <br>
Create a security group called Accountants [line 61] <br>
Make <someuser> a member of the “ACCOUNTANTS”  Security Group (line 65-68) <br>
Create 4 folders and use mnemonics to set permissions (lines 46-55) <br>
THEN login to Client-1 with <someuser> <br>
Start, run, type: “\\dc-1”; see which folders you can/can't access <br>
</p>
<br />
<p>
<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<strong> Create some sample file shares with various permissions </strong><br>
<strong> Note: ORDER MATTERS! Log in to DC-1 first in order to get a user to log into Client-1 with </strong><br>
<strong> Connect/log into DC-1 as your domain admin account (mydomain.com\jane_admin) </strong><br>
<strong> Connect/log into Client-1 as a normal user (mydomain\<someuser>) </strong><br>
<strong> On DC-1, on the C:\ drive, create 4 folders: “read-access”, “write-access”, “no-access”, “accounting” </strong><br><br> 
<strong> Set the following permissions (share the folder) for the “Domain Users” group: </strong><br>
<strong> Folder: “read-access”, Group: “Domain Users”, Permission: “Read” </strong><br>
<strong> Mnemonic: </strong> D. U. read  <br>
<strong> Folder: “write-access”,  Group: “Domain Users”, Permissions: “Read/Write” </strong><br>
<strong> Mnemonic: </strong> D.U. read or write <br>
<strong> Folder: “no-access”, Group: “Domain Admins”, “Permissions: “Read/Write” </strong><br>
<strong> Mnemonic: </strong> DAd I no READ OR WRITE <br>
<strong> (Skip accounting for now) </strong> <br>
<strong> Mnemonic: </strong> ACCOUNTANTS READ & WRITE <br>

<strong> Attempt to access file shares as a normal user </strong> (<em>honestly, can skip this part for now) </em>
On Client-1, navigate to the shared folder (start, run, \\dc-1) <br>
Try to access the folders you just created. Which folders can you access? Which folders can you create stuff in? Does it make sense? <br>

<strong> Create an “ACCOUNTANTS” Security Group, assign permissions, an test access </strong><br>
<strong> Go back to DC-1, in Active Directory, create a security group called “ACCOUNTANTS” </strong><br>
On the “accounting” folder you created earlier, set the following permissions: <br>
<strong> Folder: “accounting”, Group: “ACCOUNTANTS”, Permissions: “Read/Write” <br>
On Client-1, as  <someuser>, try to access the accountants folder. It should fail. <br>
Log out of Client-1 as  <someuser> <br>
On DC-1, make <someuser> a member of the “ACCOUNTANTS”  Security Group <br>
Sign back into Client-1 as <someuser> and try to access the “accounting” share in \\DC-1\ - Does it work now? <br>


Essential steps: <br>
Login to DC-1 as mydomain.com\jane_admin (line 44) <br> 
In DC-1:  <br>
Create security group called Accountants [line 61] <br>
Make <someuser> a member of the “ACCOUNTANTS”  Security Group (line 65-68) <br>
Create 4 folders and use mnemonics to set permissions (lines 46-55) <br>
THEN login to Client-1 with <someuser> <br>
Start, run, type: “\\dc-1”; see which folders you can/can't access <br>
</p>
</p>
<p>

</p>


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

