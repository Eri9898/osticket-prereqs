<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Computer)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Enable IIS
- Install Web Platform Installer
- Install My SQL (Set up Username and Passwoord)
- Install C++ Redistributable
- Configure Permissions and Install OSTicket

<h2>Installation Steps</h2>

<p>
<img src="https://github.com/Eri9898/osticket-prereqs/assets/143845247/ab671f05-1dfe-4c06-a4a0-c781f6bcabee.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

1. To begin you must first create a resource group within Microsoft Azure.  Then create a Windows10 Machine with 2-4 CPUs, make sure it is within the resource group you created. Allow the machine to create a virtual network and subnet.

</p>
<p>

</p>
<br />

<p>
<img src="https://github.com/Eri9898/osticket-prereqs/assets/143845247/261ff49c-4e4f-494c-8d2b-b1eefb5ea4b4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
2. Connect to the VM via Remote Desktop and within the VM enable IIS. Go to the control panel, then click Programs, control Panel>programs>Programs & Features> Windows Features On/Off, then scroll down and check the IIS box. Make sure the last 2 boxes are checked.
</p>
<br />
3. Next you must enable CGI and common HTTP Features. On the same windows feaures list scroll to world wide services>App Development> CGI and check the box. Scroll further down the list, check  and expand HTTP Features.  Make sure all the boxes within HHTP features are turned on. 
*IIS needs CGI and HTTP features for dynamic content such as a ticketing system.
</p>
<br />
4. Make sure IIS Managment Console is checked. Access it by scrolling back up to IIS on the same windows features window,  clicking on IIS>Web Management Tools>IIS Mangment Console
</p>
<br />
5. 8 Hit Ok and the computer should install IIS. On the web browser look up the local host 127.0.0.1 and the webpage should load. (it may not load on microsoft edge, if that is the case then download google chrome or another browser. Then search up the local host on there.)
</p>
<br />
6. Next you must install a PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi). Download the file then Open the file to install it.
</p>
<br />
7. Follow the same procedure for downloading a rewrite module (rewrite_amd64_en-US.msi).
</p>
<br />
8. Next install PHP (php-7.3.8-nts-Win32-VC15-x86.zip)
</p>
<br />
9. Create a new file named "PHP" for PHP on the local harddrive., unzip the PHP contents into C:/PHP
</p>
<br />
10. Next download Microsoft Visual C + + (VC_redist.x86.exe.)
</p>
<br />
11.  Next Install a database ((mysql-5.5.62-win32.msi)
Select the typical install, click finish to launch the configuariation wizard. Within that check standard configuaration and install.
Create your credentials for the database, your username will automatically be “root”. So create your password.  Do not forget it! Then execute.
</p>
<br />
12. Next search IIS on the windows start menu, right click and open as admin.
</p>
<br />
13. Open the PHP manager that was installed earlier. Click register and it will ask for a location, click the three dots. Locate file C:\PHP\CGI and select it.
</p>
<br />
14. Refresh IIS AFTER selecting the file.
 Then download OSTicket (osTicket v 1.12.8) onto the machine. 
Open the OSTicket file, extract and copy the zipped file "Upload" within it. Copy it into c:\inetpub\wwwroot
</p>
<br />
15. Within c:\inetpub\wwwroot rename the upload file to "OSTicket"
</p>
<br />
16. Reload IIS again and in the upper left corner go click on Ticket\YourName> Sites> Default> osTicket. On the right side of the screen click “Browse *:80” and the welcome webpage to IIS should load. It says “Thanks for choosing osTicket!”
</p>
<br />
17. On that same page, Ticket\YourName> Sites> Default> osTicket.  Double-click PHP Manager within OSticket. Click “Enable or disable an extension”
Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll
Then Refresh osTicket Browser
</p>
<br />
18. Rename ost-sampleconfig.php to ost-config.php
It is located in
C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
</p>
<br />
19. Next you will assign permissions to ost-config.php.  Right click to properties and go to security. Click advanced then disable inheritance, click remove all permissions. Next click add, click select principle and type everyone and click ok. Check box “full control” and apply.
</p>
<br />
20. Instal HeidiSQL ((((NAME)))  so that you can connect to MySQL. Open the file and install it. The app shoud open after install. On the bottom left click new, then enter username:Root then password:
Create a new session, enter username and passowrd.
</p>
<br />
21. Create a new session and connect to it by clicking open.  
</p>
<br />
22. In Heidi right click unnamed in upper left corner, then click create new then database.then name it osTIcket then say ok
</p>
<br />
23. 25 Continue Setting up osTicket in the ISS webpage, click next. Next fill out the system settings and in database settings enter your MY SQL 
MySQL Table Prefix: ost-config.php
MySQL Database: osTicket
MySQL Username: root
MySQL Password: ***** whatever you created
Click “Install Now!”
</p>
<br />
24. OS TIcket should then load up with a welcome screen. Congratulations you just installed os Ticket! c: 
