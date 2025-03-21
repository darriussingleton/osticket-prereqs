<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket. osTicket is an open source support ticketing system. It integrates inquiries created via email and web-based forms into a easy-to-use  web interface. It can be installed on most operating systems fairly easily and it is completely free. It includes feature like custom fields, forms, and list. You can create custom queues based on criteria specified by admin/creator/owner. It includes ticket filtering features and even has a custom knowledge base you can create and utilize. <br/>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop Connection
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)

<h2>List of Prerequisites</h2>

- MySQL
- HeidiSQL
- PHP
- osTicket (opensource)
- IIS (server) and Management Console

<h2>Installation Steps</h2>

<h3>Setup a Resource Group</h3>
<p>
 Select "Create new Resource Group" and choose which Azure subscription to assign the resource group under. Give the resource group a unique name then, select which region you want the resource group in. 
 </p>
 
 <p>
<img src="https://imgur.com/UcrF1lq.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>

 <h3>Create a Virtual Machine</h3>
 
 <p>
 Search for a Virtual machine from  the Azure marketplace. Scroll down to find the "Image" option and select "Windows 10 Pro, Version 22H2, x64 Gen2." Ensure the virtual machine has at least 2 vCPUs and 16 GB of memory, which you can set in the "Size" option on the same page.</p>

<ul>
  <li>
    <strong>Virtual Machine Name:</strong> osticket-vm
  </li>
  <li>
    <strong>Username:</strong> labuser
  </li>
  <li>
    <strong>Password:</strong> osTicketPassword1!
  </li>
</ul>
<p>
<img src="https://imgur.com/GD6UmcV.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<h3>Log into the VM with Remote Desktop</h3>
 <p>On your pc click inside the search and type "remote desktop connection". Once the connection screen opens up you will need to go to the Azure VM and copy the VM's IP address and paste it into the field that says "Computer". Then you will use the username and  password you entered for the VM when you created it. This will allow you you to control the VM from your personal PC.</p>
<p>
<img src="https://imgur.com/vxWmP1M.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<h3>Installing osTicket</h3>
<p>
osTicket can be downloaded from their official site or their github repository.
 <p>Download osTicket from the official website:</p>
<a href="https://osticket.com/download/">osTicket Download</a>
<p>View the osTicket source code and contribute on GitHub:</p>
<a href="https://github.com/osTicket/osTicket">osTicket GitHub Repository</a>
</p>


<p>While remotely operating the VM (osticket-vm), download the osTicket-Installation-Files.zip and unzip it onto the desktop (osticket-vm). The folder should be called “osTicket-Installation-Files”
Use the files in this folder to install osTicket and some of the dependencies.
</p>
<p>
<img src="https://imgur.com/hYCJK0W.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>

<p>
First go to the settings Menu then to programs in order to 
Install / Enable IIS in Windows WITH CGI
World Wide Web Services -> Application Development Features -> [X] CGI
</p>

<img src="https://imgur.com/pMLATpb.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<img src="https://imgur.com/n1WbLJm.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<p>
From the “osTicket-Installation-Files” folder, install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)

From the “osTicket-Installation-Files” folder install the Rewrite Module (rewrite_amd64_en-US.msi)

Create a folder named  "C:\PHP"
</p>


<p>
From the “osTicket-Installation-Files” folder, unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and place it inside the  “C:\PHP” folder

From the “osTicket-Installation-Files” folder, install VC_redist.x86.exe.

From the “osTicket-Installation-Files” folder, install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
Typical Setup ->
Launch Configuration Wizard (after install) ->
Standard Configuration ->
<ul>
 <li>Username: root</li>
<li><strong>Password: root</strong></li>
</p>

<p>
<img src="https://imgur.com/9M6REEF.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>

<p>
Open IIS as an Admin
</p>

<img src="https://imgur.com/ukLQ6mi.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<p>Register PHP from within IIS (PHP Manager -> C:\PHP\php-cgi.exe)

Reload IIS (Open IIS, Stop and Start the server)

Install osTicket v1.15.8
From the “osTicket-Installation-Files” folder, unzip “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot”
Within “c:\inetpub\wwwroot”, Rename “upload” to “osTicket”

Reload IIS (Open IIS, Stop and Start the server)

Go to sites -> Default -> osTicket
On the right, click “Browse *:80”

Some extensions are not enabled so you you will have to manually enable them by
Go back to IIS, sites -> Default -> osTicket
Double-click PHP Manager</p>

<img src="https://imgur.com/wGCnqwI.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<p>Click “Enable or disable an extension”
<ul>
  <li>Enable: php_imap.dll</li>
  <li>Enable: php_intl.dll</li>
  <li>Enable: php_opcache.dll</li>
</ul>
</p>


<img src="https://imgur.com/7Z9Idq5.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<img src="https://imgur.com/4Ktb791.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>


<p>Rename: ost-config.php
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php


Assign Permissions: ost-config.php
Disable inheritance -> Remove All
New Permissions -> Everyone -> All
</p>

<p>
<img src="https://imgur.com/rwF0zPV.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>

<p>
Continue Setting up osTicket in the browser 
Name Helpdesk
Default email (receives email from customers)

From the “osTicket-Installation-Files” folder, install HeidiSQL.
Create a new session, root/root
Connect to the session
Create a database called “osTicket”
</p>

<p>
<img src="https://imgur.com/440GbCE.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>


<p>
Continue Setting up osTicket in the browser
<ul>
  <li><strong>MySQL Database:</strong> osTicket</li>
  <li><strong>MySQL Username:</strong> root</li>
  <li><strong>MySQL Password:</strong> root</li>
</ul>
Important Security Note: Using "root" as both the MySQL username and password is extremely insecure and should never be done in a production environment. For development or testing on a local, isolated machine, it might be acceptable, but for anything accessible over a network, you must create a dedicated MySQL user with limited privileges and a strong, unique password.
</p>


<p>
<img src="https://imgur.com/4tyoPnd.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>

<p>

You should be able to browse to your help desk login page: http://localhost/osTicket/scp/login.php

End Users osTicket URL:
http://localhost/osTicket/ </p>
<p>
 
<img src="https://imgur.com/iTh8Tsx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

