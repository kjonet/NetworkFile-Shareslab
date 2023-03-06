<h1> FILE AND NETWORK SHARES PERMISSIONS LAB </h1>

<p> The lab is designed to show how administrators can grant network and file shares to the users on the domain. </p>

<h3> Step 1: </h3>

<p> Log on to your Domain Controller using your adinistartor account.Before we can assign permissions, we will need a few users to work with. We can implement a powershell script that will automate random users for us to use. To do this, open Powershell ISE as an administrator. Copy the contents of the script from here: https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1 </p>

<p>Select “New Script” paste the copied contents and press play. A list of random users should begin to populate in the “_EMPLOYEES_” folder on the DC. 
</p>
<a href="https://imgur.com/Ws0H0lI"><img src="https://i.imgur.com/Ws0H0lI.png" title="source: imgur.com" /></a>

<h3> Step 2: </h3>


<p> Navigate to Users and Computers from Active Directory and log in as one of the users in the “_EMPLOYEES” folder. Select a user to log in as. The user password will be “Password1” as defined by the powershell script. 
</p>

<p>Sign into a PC on the domain network. In this lab we’re signing on to a virtual client PC we created earlier. </p>

<h3> Step 3: </h3>


<p>Using remote desktop, sign onto the Domain Controller virtual machine, “AD-DC”. Within the C: drive, we will create folders with certain permissions. We will create 4 folders titled the following:  "read-access" "read/write-access" "no-access" and "accounting".
</p>

<a href="https://imgur.com/vssHIgU"><img src="https://i.imgur.com/vssHIgU.png" title="source: imgur.com" /></a>

<p>Next, we will create shares for each one. To do this, right click on the folder you want to assign permissions to. Go to properties and then the share tab. Select “Share”, In the Network Access prompt, we will type in either Domain Users or Admin users (depending on the folder) and grant either read or read/write permissions. </p>

<a href="https://imgur.com/DDIoM0l"><img src="https://i.imgur.com/DDIoM0l.png" title="source: imgur.com" /></a>


<p>The "read-access" Folder will only have read permission fro domain users. The "Write-access"  folder will have read/write permissions for domain users. The "no-access" folder will grant read/write permissions to admins only.</p> 

<a href="https://imgur.com/yNWHjbT"><img src="https://i.imgur.com/yNWHjbT.png" title="source: imgur.com" /></a>

<h3> Step 4: </h3>

<p> Next, navigate to the Client PC VM. Go over to the C: Drive and type \\AD-DC in the address bar of the file explorer. The the folders that we configured earlier should populate on the network share. If the user clicks on the “No-access” folder, they should get a warning saying they do not have permissions to access the folder. The “Read-access” folder will only grant the user read permissions within that folder but they won’t be able to create any documents within it, while the “Write-access” folder will allow the user read/write permissions such as saving and/or deleting a text file. </p>

<a href="https://imgur.com/42IAhAz"><img src="https://i.imgur.com/42IAhAz.png" title="source: imgur.com" /></a>

<h3> Step 5: </h3>

<p>Back in the DC virtual Machine, go to Active Directory. Create a security group named “ACCOUNTANTS” Any users we assign here will be allowed permissions into the “ACCOUNTANTS” folder. Next, go bak to the C: drive and locate the “Accountents” folder created earlier. Right click and select Properties. Go to the Sharing tab, click share and add “ACCOUNTANTS” and give the security group Read/Write access. The folder will only be accessed by any users within the accounting folder. </p>

<a href="https://imgur.com/WQoj5op"><img src="https://i.imgur.com/WQoj5op.png" title="source: imgur.com" /></a>






