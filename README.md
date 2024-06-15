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
<strong> Simplified version <br>
Log into DC-1 as mydomain.com\jane_admin <br>
Copy DC-1's Public IP address, if you don't have it already <br>
Open Remote Desktop Login page (type "Remote Desktop" in Start menu <br>
Paste the Public IP address, then click enter.
Click "More choices", then click "Use a different account"<br>
For the username, type "mydomain.com\jane_admin" and type the same password you created for the VM <br>
  
A - In DC-1: <br></strong>
<strong> First you have to create an Organizational Unit and name it "_SECURITY_GROUPS" </strong><br>
  1. Type "Active Directory" in Start Menu search box (1) and then cllick "Active Directory Users and Computers (ADUC)" (2) <br>
<img width="960" alt="Capture - ADUC" src="https://github.com/jaysixco/configure-ad/assets/160427311/b947408d-dde2-4fdd-9b40-57cb426ec615">
<br>
  2. Right click "mydomain.com", hover mouse over "New", and click "Organizational Unit" <br>
<img width="565" alt="Capture - OU" src="https://github.com/jaysixco/configure-ad/assets/160427311/d7c7cb8d-4d7c-40f7-bdd2-12d5f3374e75">
<br>
  3. Name it "_SECURITY_GROUPS" and then click "Ok" <br>
<img width="328" alt="sgps" src="https://github.com/jaysixco/azure-network-protocols/assets/160427311/8a73e00c-e7c5-4b3e-81e2-5b54b44a514d">
<br>
  <br>

  
<strong> B - After you create the organizational unit, add a group inside of it and name it "ACCOUNTANTS" </strong><br>
  1. Click the small arrow next to "mydomain.com" in the sidebar, then click "_SECURITY_GROUPS"
  2. Right click white space, hover over New, click Group <br>
<img width="565" alt="new - group" src="https://github.com/jaysixco/azure-network-protocols/assets/160427311/33376868-6476-4503-a6e7-eefec288062b">
<br>
  3. Name it "ACCOUNTANTS" <br>
<img width="328" alt="acntnts" src="https://github.com/jaysixco/azure-network-protocols/assets/160427311/aceaa860-ffd3-485f-a33a-6342b799e97f">
<br>
  <br>

  
<strong> C - Make <someuser> a member of the “ACCOUNTANTS”  Security Group </strong> <br>
  1. Type "Active Directory" in search bar and click Active Directory Users and Computers
  2. Click "mydomain.com", then double click "SECURITY_GROUPS" <br>
  <img width="565" alt="mydomain, then sgps" src="https://github.com/jaysixco/azure-network-protocols/assets/160427311/7f164c54-d2b5-4ef8-ad22-64c6ddcb113a"> <br>
  3. Right click "ACCOUNTANTS", then click "Properties" <br>
  <img width="565" alt="act-prop" src="https://github.com/jaysixco/azure-network-protocols/assets/160427311/8c7d2335-816b-4ff7-9bce-0659c0c7386e">
  4. Click "Members" tab, then Click "Add" <br>
  <img width="300" alt="members, then click Add" src="https://github.com/jaysixco/azure-network-protocols/assets/160427311/213f67ff-82b1-466b-96a8-1f554f0c803c">
  5. Type the username of some user generated in another hub, click "Check Names", click "Ok" <br>
  <img width="343" alt="type name, click Check Names, click Ok (1)" src="https://github.com/jaysixco/azure-network-protocols/assets/160427311/aed54309-af92-4a90-aba2-147242570ffd">
  6. Click "Apply", then  click "OK" <br>
  <img width="300" alt="click Apply, then click OK (2)" src="https://github.com/jaysixco/azure-network-protocols/assets/160427311/afc69fc4-2c46-40fa-9c41-9e3a7c518039">
  <br>
  <br>

  
<strong> D - (Still in DC-1) Create 4 folders in C:\ drive <br></strong>
    1. Type "File Explorer" in start menu search bar and click it. <br>
    2. On the sidebar, scroll down until you see "This PC". Click it. <br>
    3. Click "Windows (C:)" <br>
    4. Right click white space, hover over "New", and click "Folder" <br>
    <img width="590" alt="new folder" src="https://github.com/jaysixco/azure-network-protocols/assets/160427311/f14e75f5-48db-4b25-a0fe-9074bfd3abf6">

    6. Name the folder: “read-access” (without the quotes) then press enter <br>
    <img width="590" alt="read access" src="https://github.com/jaysixco/azure-network-protocols/assets/160427311/9707eff2-9f27-4aed-81b8-f5fe69695f51">
    7. Repeat steps 3 and 4 <br>
    8. Name the folder: “write-access” (without the quotes) then press enter <br>
    9. Repeat steps 3 and 4 <br>
    10. Name the folder: “no-access” (without the quotes) then press enter <br>
    11. Repeat steps 3 and 4 <br>
    12. Name the folder: “accounting” (without the quotes) then press enter <br>
    
  FInal product: <br>
 <img width="590" alt="final product" src="https://github.com/jaysixco/azure-network-protocols/assets/160427311/3975277b-9846-47ca-924b-f93f2a4e4dde">
  <br>
  <br>

  
<strong> E - Set permission for "read-access": </strong><br>
    1. Right click "read-access" <br>
    2. Click "Properties" <br>
    3. Click the "Sharing" tab in the page that pops up, then click "Share" <br>
    5. Type in the full name of the "Group:" below that is in the same row as the folder you clicked (ex: type "domain users" instead of just "domain", then click "Add" <br>
    <img width="441" alt="dom u add" src="https://github.com/jaysixco/azure-network-protocols/assets/160427311/23c90912-0142-477a-a751-89e999dd9c47">
    6. Set permission level to the "Permissions:" below that is in the same row  as the folder you clicked then click "Share" <br>
    <img width="441" alt="perm level" src="https://github.com/jaysixco/azure-network-protocols/assets/160427311/473a8cd0-21b8-4f54-8b96-18ef74b398bc"> <br>
<strong> Folder: “read-access”, Group: “Domain Users”, Permission: “Read” </strong><br>
<strong> Folder: “write-access”,  Group: “Domain Users”, Permissions: “Read/Write” </strong><br>
<strong> Folder: “no-access”, Group: “Domain Admins”, “Permissions: “Read/Write” </strong><br>
<strong> Folder: “accounting”, Group: “ACCOUNTANTS”, Permissions: “Read/Write” </strong><br>
  <br>
  <br>
  
<strong> F - See which folders you can or can't access </strong> <br>
    1. Login to Client-1 with username of some user <br>
    2. Right click "Start" button then click "Run" <br>
<img width="214" alt="right click start, then click run" src="https://github.com/jaysixco/azure-network-protocols/assets/160427311/28de9c64-1cb0-48af-a133-5ee87992135e">
    4. Type: “\\dc-1” (1) then click "OK" (2) <br>
<img width="285" alt="type dc-1 then click ok" src="https://github.com/jaysixco/azure-network-protocols/assets/160427311/0ac94aba-e8c4-4900-b653-2b9e76fbf5a6">
<br>
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







For write
<img width="272" alt="write - sharing tab, share" src="https://github.com/jaysixco/azure-network-protocols/assets/160427311/63f7e8bf-384e-4b3e-8228-afb1ac0c3cd6">
<img width="441" alt="write (2)" src="https://github.com/jaysixco/azure-network-protocols/assets/160427311/1bd2f0af-622a-43dc-b319-384be3c875a7">
<img width="441" alt="write (3)" src="https://github.com/jaysixco/azure-network-protocols/assets/160427311/af357095-8ad6-467c-855b-f989e61910ea">















For no access
<img width="272" alt="no act - sharing share" src="https://github.com/jaysixco/azure-network-protocols/assets/160427311/f2c73f56-c26b-4f71-b69a-1e625e507a98">
<img width="441" alt="no act dom add (2)" src="https://github.com/jaysixco/azure-network-protocols/assets/160427311/fe909afe-ff08-4259-b88a-68885916bdf8">
<img width="441" alt="no act perm level (3)" src="https://github.com/jaysixco/azure-network-protocols/assets/160427311/08aea45b-a709-49e2-880f-4e7ca1b072ad">

















For accounting
<img width="272" alt="acnting sharing, share" src="https://github.com/jaysixco/azure-network-protocols/assets/160427311/0d8b4ffd-ad81-40ba-b1ed-6e038e84a5f3">
<img width="441" alt="act, add, share" src="https://github.com/jaysixco/azure-network-protocols/assets/160427311/c3b2a512-4cbe-4c0c-aa7a-3a190e0054fa">
<img width="441" alt="act perm" src="https://github.com/jaysixco/azure-network-protocols/assets/160427311/9ca4b97b-0952-46bf-9937-a8158acbd0cb">





















