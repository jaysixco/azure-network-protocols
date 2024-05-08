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
<strong> Simplified version <br>
- Log into DC-1 as mydomain.com\jane_admin <br>
- In DC-1: <br></strong>
Active Directory Users and Computers > Right click "mydomain.com" > Hover over "New" > Click "Organizational Unit" > Name it "_SECURITY_GROUPS" > Then add ACCOUNTANTS inside of it (Right click white space + New + Group)
  <br>
&nbsp; - Create security group called Accountants <br>
&nbsp;&nbsp; - First you have to create an OU (_SECURITY_GROUPS) <br>
&nbsp;&nbsp; - Then add ACCOUNTANTS inside of it (Right click + New + Group] <br>
&nbsp; - Make <someuser> a member of the “ACCOUNTANTS”  Security Group <br>
  ADUC > right click "ACCOUNTANTS" > click "Members" tab > click "Add" > type <someuser> > click "Check Names" > click "Ok" > click "Apply" > click "OK"
  <br>
- <strong> (Still in DC-1) Create 4 folders in C:\ drive <br></strong>
  Type File Explorer in search bar > click "This PC" > click "Windows (C:)" > Right click white space > click/hover "New" > click "Folder"
  <br>
&nbsp;&nbsp; - “read-access”, “write-access”, “no-access”, “accounting” <br>
- <strong> Set the following permissions: </strong><br>
&nbsp;&nbsp; - Right click folder > Properties> Sharing tab> Share> Type in full name of group (ex: "domain users" vs "domain"> Add> Set permission level> Share <br>
<strong> Folder: “read-access”, Group: “Domain Users”, Permission: “Read” </strong><br>
<strong> Mnemonic: </strong> D. U. read  <br>
<strong> Folder: “write-access”,  Group: “Domain Users”, Permissions: “Read/Write” </strong><br>
<strong> Mnemonic: </strong> D.U. read or write <br>
<strong> Folder: “no-access”, Group: “Domain Admins”, “Permissions: “Read/Write” </strong><br>
<strong> Mnemonic: </strong> DAd I no READ OR WRITE <br>
<strong> Folder: “accounting”, Group: “ACCOUNTANTS”, Permissions: “Read/Write” </strong><br>
<strong> Mnemonic: </strong> ACCOUNTANTS READ & WRITE <br>
<strong> Login to Client-1 with <someuser> </strong><br>
<strong> Right click "Start" button > click "Run" > type: “\\dc-1”; see which folders you can/can't access </strong><br> 

</p>
</p>
<p>

</p>


<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor iSFn reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

