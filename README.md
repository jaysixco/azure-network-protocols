# azure-network-protocols

<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />
In this tutorial, you are going to play 3 roles:  administrator, agent, user <br>
In this tutorial, you/we are going to be creating and delegating tickets <br>

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
Create some sample file shares with various permissions
Note: ORDER MATTERS! Log in to DC-1 first in order to get a user to log into Client-1 with
Connect/log into DC-1 as your domain admin account (mydomain.com\jane_admin)
Connect/log into Client-1 as a normal user (mydomain\<someuser>)
On DC-1, on the C:\ drive, create 4 folders: “read-access”, “write-access”, “no-access”, “accounting” 
[read, write, no, accounting - has a kind of sing-song rhythm to it!]
Set the following permissions (share the folder) for the “Domain Users” group:
Folder: “read-access”, Group: “Domain Users”, Permission: “Read”
Mnemonic: D. U. read 
Folder: “write-access”,  Group: “Domain Users”, Permissions: “Read/Write”
Mnemonic: D.U. read or write 
Folder: “no-access”, Group: “Domain Admins”, “Permissions: “Read/Write”
Mnemonic: DAd I no READ OR WRITE
(Skip accounting for now)
Mnemonic: ACCOUNTANTS READ & WRITE

Attempt to access file shares as a normal user
On Client-1, navigate to the shared folder (start, run, \\dc-1)
Try to access the folders you just created. Which folders can you access? Which folders can you create stuff in? Does it make sense?
Non-mandatory Extra steps

Create an “ACCOUNTANTS” Security Group, assign permissions, an test access
Go back to DC-1, in Active Directory, create a security group called “ACCOUNTANTS”
On the “accounting” folder you created earlier, set the following permissions:
Folder: “accounting”, Group: “ACCOUNTANTS”, Permissions: “Read/Write”
On Client-1, as  <someuser>, try to access the accountants folder. It should fail. 
Log out of Client-1 as  <someuser>
On DC-1, make <someuser> a member of the “ACCOUNTANTS”  Security Group
Sign back into Client-1 as <someuser> and try to access the “accounting” share in \\DC-1\ - Does it work now?

General Idea:
Creating four folders in DC-1 and telling Client-1's user what they're allowed to do it (will they be able to write in it, or just read it, or even have access to it at all).
Create the security group before you even create the folders, so that you can just set conditions for them all in one go.
For this step, have in mind the Client-1 username you plan to use.
After all that is done, THEN log into Client-1 with whatever user you choose.

Any Questions I Have Before Starting?
Step 16 - how to make <someuser> member of “ACCOUNTANTS” group.
WITy (What I'll Try): Right clicking stuff and looking for something that says “members” or “users”

Essential steps:
Login to DC-1 as mydomain.com\jane_admin
In DC-1: 
Create security group [step 11]
make <someuser> a member of the “ACCOUNTANTS”  Security Group
Create 4 folders and use mnemonics to set permissions
THEN login to Client-1 with <someuser>
Start, run, type: “\\dc-1”; see which folders you can/can't access
</p>
<br />
<p>

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


<img width="960" alt="Ticket LIfecycle - Karen's Complaint" src="https://github.com/jaysixco/ticket-lifecycle/assets/160427311/b80253e6-9fff-4e21-9a45-53b605d68663">
<img width="959" alt="Ticket LIfecycle - Reassign Button" src="https://github.com/jaysixco/ticket-lifecycle/assets/160427311/beeacf9e-dbd6-45dd-a792-345745867684">

