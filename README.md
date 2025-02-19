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

- MySQL
- HeidiSQL
- PHP
- osTicket (opensource)
- IIS and Management Console

<h2>Installation Steps</h2>

<h3>Setup a Resource Group</h3>
 Select "Create new Resource Group" and choose which Azure subscription to assign the resource group under. Give the resource group a unique name then, select which region you want the resource group in. 
 <p>
<img src="https://imgur.com/UcrF1lq" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

 <h3>Create a Virtual Machine</h3>
 Search for a Virtual machine from  the Azure marketplace. Scroll down to find the "Image" option and select "Windows 10 Pro, Version 22H2, x64 Gen2." Ensure the virtual machine has at least 2 vCPUs and 16 GB of memory, which you can set in the "Size" option on the same page.

Name the Virtual Machine
   Name: osticket-vm
   Username: labuser
   Password: osTicketPassword1!

<p>
<img src="https://imgur.com/GD6UmcV" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>



Log into the VM with Remote Desktop

<p>
<img src="https://imgur.com/vxWmP1M" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
Within the VM (osticket-vm), download the osTicket-Installation-Files.zip and unzip it onto your desktop. The folder should be called “osTicket-Installation-Files”
We will use the files in this folder to install osTicket and some of the dependencies.
</p>
<p>
<img src="https://imgur.com/hYCJK0W" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

First go to the settings Menu then to programs in order to 
Install / Enable IIS in Windows WITH CGI
World Wide Web Services -> Application Development Features -> [X] CGI

<img src="[https://imgur.com/n1WbLJm](https://imgur.com/n1WbLJm)" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://imgur.com/n1WbLJm" height="80%" width="80%" alt="Disk Sanitization Steps"/>

From the “osTicket-Installation-Files” folder, install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)

From the “osTicket-Installation-Files” folder install the Rewrite Module (rewrite_amd64_en-US.msi)

Create the directory C:\PHP

<img src="https://imgur.com/g5VYdsF" height="80%" width="80%" alt="Disk Sanitization Steps"/>



From the “osTicket-Installation-Files” folder, unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder

From the “osTicket-Installation-Files” folder, install VC_redist.x86.exe.

From the “osTicket-Installation-Files” folder, install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
Typical Setup ->
Launch Configuration Wizard (after install) ->
Standard Configuration ->
Username: root
Password: root

<p>
<img src="https://imgur.com/9M6REEF" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

Open IIS as an Admin

Register PHP from within IIS (PHP Manager -> C:\PHP\php-cgi.exe)

Reload IIS (Open IIS, Stop and Start the server)

Install osTicket v1.15.8
From the “osTicket-Installation-Files” folder, unzip “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot”
Within “c:\inetpub\wwwroot”, Rename “upload” to “osTicket”

Reload IIS (Open IIS, Stop and Start the server)

Go to sites -> Default -> osTicket
On the right, click “Browse *:80”

Note that some extensions are not enabled
Go back to IIS, sites -> Default -> osTicket
Double-click PHP Manager
Click “Enable or disable an extension”
Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll
Refresh the osTicket site in your browser, observe the changes

Rename: ost-config.php
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php

Assign Permissions: ost-config.php
Disable inheritance -> Remove All
New Permissions -> Everyone -> All

<p>
<img src="https://imgur.com/rwF0zPV" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

Continue Setting up osTicket in the browser (click Continue)
Name Helpdesk
Default email (receives email from customers)

From the “osTicket-Installation-Files” folder, install HeidiSQL.
Open Heidi SQL
Create a new session, root/root
Connect to the session
Create a database called “osTicket”

<p>
<img src="https://imgur.com/440GbCE" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>



Continue Setting up osTicket in the browser
MySQL Database: osTicket
MySQL Username: root
MySQL Password: root
Click “Install Now!”

<p>
<img src="https://imgur.com/4tyoPnd" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

Congratulations, hopefully it is installed with no errors!
Browse to your help desk login page: http://localhost/osTicket/scp/login.php

End Users osTicket URL:
http://localhost/osTicket/ 

<p>
<img src="https://imgur.com/iTh8Tsx" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
