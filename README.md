<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Item 1 (Create Virtual Machine in Azure)
Create a Resource Group
Create a Windows 10 Virtual Machine (VM) with 2-4 Virtual CPUs
When creating the VM, allow it to create a new Virtual Network (Vnet). Create an Azure Virtual Machine Windows 10, 4 vCPUs
Name: Vm-osticket
Username: labuser (for example/whatever you chose)
Password: osTicketPassword1! (for example/whatever you chose) 
Install / Enable IIS in Windows WITH
CGI and Common HTTP Features
World Wide Web Services -> Application Development Features ->
[X] CGI
[X] Common HTTP Features
AND IIS Management Console
Internet Information Services -> Web Management Tools -> IIS Management Console
	[X] IIS Management Console



- Item 2 download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi) > download and install the Rewrite Module (rewrite_amd64_en-US.msi) >
  Create the directory C:\PHP > download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP > download and install VC_redist.x86.exe. > download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
Typical Setup ->
Launch Configuration Wizard (after install) ->
Standard Configuration ->
Password1





- Item 3 Open IIS as an Admin

Register PHP from within IIS


Install osTicket v1.15.8
Download osTicket from the Installation Files Folder
Extract and copy “upload” folder to c:\inetpub\wwwroot
Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”

Reload IIS (Open IIS, Stop and ReStart the server)

Go to sites -> Default -> osTicket
On the right, click “Browse *:80”

Note that some extensions are not enabled
Go back to IIS, sites -> Default -> osTicket
Double-click PHP Manager
Click “Enable or disable an extension”
Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll
Refresh the osTicket site in your browse, observe the changes

Rename: ost-config.php
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php

Assign Permissions: ost-config.php
Disable inheritance -> Remove All
New Permissions -> Everyone -> All

Continue Setting up osTicket in the browser (click Continue)
Name Helpdesk
Default email (receives email from customers)


- Item 4 download and install HeidiSQL.
Open Heidi SQL
Create a new session, root/Password1
Connect to the session
Create a database called “osTicket”

Continue Setting up osticket in the browser
MySQL Database: osTicket
MySQL Username: root
MySQL Password: Password1
Click “Install Now!”

- Item 5 Congratulations, hopefully it is installed with no errors!
Browse to your help desk login page: http://localhost/osTicket/scp/login.php

Clean up
Delete: C:\inetpub\wwwroot\osTicket\setup
Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php


<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/e2Hjkuv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
After successfully installing all the required software via files referenced above users will reach this point. The purpose of this picture is to provide context that if you've made it this far it's safe to assume you've installed everything correctly. With the database being created using HeidiSQL you now take the created name of the database "osticket" and fill in the MySQL database on the left. Username should be root and Password1 in this example (ideally it's whatever you've set it to).
</p>
<br />

<p>
<img src="https://i.imgur.com/bzuyjtx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Login screen once everything is filled out. Your user name and password will vary depending on what you decided to use, this should be this first time you VM- osticking system has been logged into. I would like to note it would be beneficial to write down your login credentials as it can be confusing once additional users are added.
</p>
<br />

<p>
<img src="https://i.imgur.com/d1QlHly.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Finally you've installed everything that was required, set permissions and succesfully logged in. A few things I want to point out on the dashboard: "Open" shows one ticket that is automatically generated this is to be expected. The section referenced "Users" this is where users will be created and mainatained. Looking to the top right of the screen "Admin Portal" when selected you'll see a change to that section which will be "Agent portal" two different sections of the UI to do different things, this is very important.
</p>
<br />
