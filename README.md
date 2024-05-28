# azure-network-protocols

<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>Network File Shares and Permissions </h1>
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
Log into DC-1 as mydomain.com\jane_admin <br>
  
A - In DC-1: <br></strong>
<strong> First you have to create an Organizational Unit and name it "_SECURITY_GROUPS" </strong><br>
  1. Type "Active Directory" in Start Menu search box (1) and then cllick "Active Directory Users and Computers (ADUC)" (2) <br>
<img width="960" alt="Capture - ADUC" src="https://github.com/jaysixco/configure-ad/assets/160427311/b947408d-dde2-4fdd-9b40-57cb426ec615">
<br>
  2. Right click "mydomain.com", hover mouse over "New", and click "Organizational Unit" <br>
  insert screenshot <br>
  3. Name it "_SECURITY_GROUPS" and then click "Ok" <br>
  insert screenshot <br>
  <br>

  
<strong> B - After you create the organizational unit, add a group inside of it and name it "ACCOUNTANTS" </strong><br>
  1. Right click white space, [click/hover?] New, click Group <br>
  insert screenshot <br>
  2. Name it "ACCOUNTANTS" <br>
  insert screenshot <br>
  <br>

  
<strong> C - Make <someuser> a member of the “ACCOUNTANTS”  Security Group </strong> <br>
  1. Type "Active Directory" in search bar and click Active Directory Users and Computers <br>
  2. Right click "ACCOUNTANTS" <br>
  3. click "Members" tab <br>
  insert screenshot <br>
  4. click "Add" <br>
  5. Type the username of some user generated in another hub 
  add link <br>
  6. click "Check Names" <br>
  7. click "Ok" <br>
  8. click "Apply" <br>
  9. click "OK" <br>
  <br>
  <br>

  
<strong> D - (Still in DC-1) Create 4 folders in C:\ drive <br></strong>
    1. Type "File Explorer" in start menu search bar and click it. <br>
    2. On the sidebar, scroll down until you see "This PC". Click it. <br>
    3. click "Windows (C:)" <br>
    4. Right click white space, hover over "New", and click "Folder" <br>
    6. Name the folder: “read-access” (without the quotes) <br>
    7. Repeat steps 3 and 4 <br>
    8. Name the folder: “write-access” (without the quotes)<br>
    9. Repeat steps 3 and 4 <br>
    10. Name the folder: “no-access” (without the quotes) <br>
    11. Repeat steps 3 and 4 <br>
    12. Name the folder: “accounting” (without the quotes) <br>
  <br>
  <br>

  
<strong> E - Set the following permissions: </strong><br>
    1. Right click the folder <br>
    2. Click "Properties" <br>
    3. Click the "Sharing" tab in the page that pops up <br>
    4. Click "Share" <br>
    5. Type in the full name of the "Group:" below that is in the same row as the folder you clicked (ex: type "domain users" instead of just "domain" <br>
    6. Click "Add" <br>
    7. Set permission level to the "Permissions:" below that is in the same row  as the folder you clicked <br>
    8. Click "Share" <br>
<strong> Folder: “read-access”, Group: “Domain Users”, Permission: “Read” </strong><br>
<strong> Folder: “write-access”,  Group: “Domain Users”, Permissions: “Read/Write” </strong><br>
<strong> Folder: “no-access”, Group: “Domain Admins”, “Permissions: “Read/Write” </strong><br>
<strong> Folder: “accounting”, Group: “ACCOUNTANTS”, Permissions: “Read/Write” </strong><br>
  (insert screenshot of read access)
  <br>
  <br>
  
<strong> F - See which folders you can or can't access </strong> <br>
    1. Login to Client-1 with username of some user <br>
    2. Right click "Start" button <br>
    3. Click "Run" <br>
  insert screenshot <br>
    4. Type: “\\dc-1” <br>
  insert screenshot <br>
    5. Click on the different folders and you see which folders you can/can't access </strong><br> 
    (for example, read-access will not allow us to write anything in it because we have set Permission only to read)

<strong> Finish </strong>
</p>
<p>
  <em>
    All above steps are accurate. Can follow it and it will work. Fix formatting. 
  </em>
</p>

Notes later
- Add screenshots for part where you set permissions
- Delete mnemonics
