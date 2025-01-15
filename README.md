<img src="https://i.imgur.com/svCFZeT.png" height="40%" width="40%" alt="osticket"/>
<br />
<h1>Installation of osTicket </h1>

<h2>Description</h2>
In this tutorial, we will walk you through the process of installing osTicket on a Windows virtual machine.
<br />


<h2>Languages and Utilities Used</h2>

- <b>Microsoft Remote Desktop</b> 
- <b>Microsoft Azure</b>
- <b>Internet Information Services</b>

<h2>Environments Used </h2>

- <b>Windows 10</b>

<h2>Prerequisites</h2>

- <b>osTicket Installation files</b>


<h2>Lab walk-through:</h2>

<p align="center">
<br/>
<img src="https://i.imgur.com/I5QCsU7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Create a Windows Virtual Machine
Go to Azure and create a Windows virtual machine.
Once the VM is created, retrieve the public IP address of the machine.
Use Remote Desktop Connection to connect to your virtual machine using the public IP address.<br/>
<br/>
<img src="https://i.imgur.com/aystIzA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Install and Enable IIS (Internet Information Services)
IIS will act as the web server that hosts the osTicket application and allows users to access it through their browsers.<br />
Open Control Panel > Programs > Turn Windows features on or off.
Check the box for Internet Information Services (IIS) and click OK.
IIS should now be installed and running on your machine.<br />
<br/>
<img src="https://i.imgur.com/4S817mh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
In preparation for this lab I've gathered the needed resources to install osTicket, use this photo as a reference moving forward.<br />
<br/>Install PHP- PHP is required for server-side scripting to run osTicket.
Download PHP from the official PHP website.
Create a folder named PHP on the *C:* drive (C:\PHP).
Extract all PHP files into this folder (C:\PHP)<br/>
<br/>Install MySQL- MySQL is the database management system that stores osTicket data.<br/>
During installation, remember the root password as you'll need it later to connect to MySQL.<br/>
<br/>Install Visual C++ Redistributable- The Visual C++ Redistributable files are needed to ensure that PHP and other dependencies can run correctly.<br/>
<br/> Install osTicket- 
 Extract the zip file to a location of your choice.
Inside the extracted folder, you'll find a folder named upload. Copy the entire upload folder to C:\inetpub\wwwroot on your computer.
Rename the upload folder to osTicket.<br/>
<br/>
<img src="https://i.imgur.com/FGvoxsq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Now we will configure IIS to work with PHP.<br />
 Open IIS Manager as Administrator.
In the Connections pane, click on the vm and select PHP Manager.
In PHP Manager, choose to register the new PHP version and point to the C:\PHP folder.
Restart IIS by stopping and starting the service.<br/>
<br/>
<img src="https://i.imgur.com/DSJJupp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
While in IIS we need to ensure that the required PHP extensions are enabled<br/>
<br/>In IIS Manager, navigate to Sites > Default Web Site > osTicket.
Double-click on PHP Manager.
Under the PHP Extensions section, enable the following extensions:
php_imap.dll
php_intl.dll
php_opcache.dll
<br/>
<img src="https://i.imgur.com/7I7mobF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
We now need to configure the osTicket system.<br/>
<br/>Go to the C:\inetpub\wwwroot\osTicket\include folder.
Rename the file ost-sampleconfig.php to ost-config.php.<br/>
<br/>
<img src="https://i.imgur.com/fc6bzr5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
For osTicket to make changes to its configuration file, we need to modify its permissions.<br/>
<br/>Right-click on ost-config.php and select Properties.
Go to the Security tab and click Advanced.
Click Disable inheritance and remove all existing permissions.
Add a new permission principle by selecting Everyone and giving it Full Control**For Lab Only**.
Click OK to save the changes.<br/>
<br/>
<img src="https://i.imgur.com/YO8HMcj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>In IIS Manager, navigate to Sites > Default Web Site > osTicket.
On the right side, click *Browse 80 to open the installation page in your web browser.
When the osTicket setup page loads, click Continue.
Fill out the installation form with the appropriate details<br/>
<br/>
<img src="https://i.imgur.com/hi1T6JI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
Install HeidiSQL to Manage MySQL Database
Open HeidiSQL and create a new session.
Connect to the MySQL session.
Create a new database named osTicket.<br/>
<br/>Return to the osTicket installation page in your web browser.
Complete the remaining steps in the installation process, including setting up the administrator account.
Once everything is configured, you should be able to access your osTicket system through your web browser.<br/>
<br/>
Congratulations! You've successfully installed osTicket on your Windows virtual machine. 
