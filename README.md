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


- OSTicket
- Information internet Services Manager
  

<h2>Installation Steps</h2>

<p>

<img width="1578" height="913" alt="image" src="https://github.com/user-attachments/assets/8aa7df79-1292-4aba-b39f-f3385bc2641c" />

</p>
<p>
Azure on windows 
</p>
<br />

<p>
<img width="1287" height="848" alt="image" src="https://github.com/user-attachments/assets/b6173573-ac58-445d-a32d-0ac6b03dacd7" />

</p>
<p>
Remote Labs
</p>


<img width="997" height="1007" alt="image" src="https://github.com/user-attachments/assets/bc84a202-4205-4e2a-b43a-551c23805cd4" />




STEP 1

Create an Azure Virtual Machine Windows 10, 4 vCPUs
Name: osticket-vm
Username: labuser
Password: osTicketPassword1!

Log into the VM with Remote Desktop

STEP 2

Within the VM (osticket-vm), download the osTicket-Installation-Files.zip and unzip it onto your desktop. The folder should be called “osTicket-Installation-Files”
We will use the files in this folder to install osTicket and some of the dependencies.

Install / Enable IIS in Windows WITH CGI
World Wide Web Services -> Application Development Features -> [X] CGI




<img width="797" height="767" alt="image" src="https://github.com/user-attachments/assets/3515aaa1-eedb-45c7-951c-535036ba8039" />




STEP 3

From the “osTicket-Installation-Files” folder, install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)

STEP 4

From the “osTicket-Installation-Files” folder install the Rewrite Module (rewrite_amd64_en-US.msi)

STEP 5

Create the directory C:\PHP

STEP 6

From the “osTicket-Installation-Files” folder, unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder

From the “osTicket-Installation-Files” folder, install VC_redist.x86.exe.

<img width="810" height="877" alt="image" src="https://github.com/user-attachments/assets/8dd9a70e-5a74-4f27-add1-b1b9d11eaaf6" />


STEP 7

From the “osTicket-Installation-Files” folder, install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
Typical Setup ->
Launch Configuration Wizard (after install) ->
Standard Configuration ->
Username: root
Password: root

STEP 8

Open IIS as an Admin

Register PHP from within IIS (PHP Manager -> C:\PHP\php-cgi.exe)

Reload IIS (Open IIS, Stop and Start the server)

STEP 9

Install osTicket v1.15.8
From the “osTicket-Installation-Files” folder, unzip “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot”
Within “c:\inetpub\wwwroot”, Rename “upload” to “osTicket”

Reload IIS (Open IIS, Stop and Start the server)




<img width="593" height="926" alt="image" src="https://github.com/user-attachments/assets/85dd1d85-4968-4f48-939e-265ee9fcb454" />




STEP 10

Go to sites -> Default -> osTicket
On the right, click “Browse *:80”

Note that some extensions are not enabled

STEP 11

Go back to IIS, sites -> Default -> osTicket
Double-click PHP Manager
Click “Enable or disable an extension”
Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll
Refresh the osTicket site in your browser, observe the changes

STEP 12

Rename: ost-config.php
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php

STEP 13

Assign Permissions: ost-config.php
Disable inheritance -> Remove All
New Permissions -> Everyone -> All

Continue Setting up osTicket in the browser (click Continue)
Name Helpdesk
Default email (receives email from customers)
<img width="816" height="916" alt="image" src="https://github.com/user-attachments/assets/0fd5d9b0-46e6-4422-8d88-2ee1cfd93aca" />





STEP 14

From the “osTicket-Installation-Files” folder, install HeidiSQL.
Open Heidi SQL
Create a new session, root/root
Connect to the session
Create a database called “osTicket”

STEP 15

Continue Setting up osTicket in the browser
MySQL Database: osTicket
MySQL Username: root
MySQL Password: root
Click “Install Now!”


End Users osTicket URL:
/localhost/osTicket/ 

Clean up
Delete: C:\inetpub\wwwroot\osTicket\setup
Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php

<br />

<br />
