<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket: Prerequisites and Installation</h1>


<h2>Description</h2>
In this guide, I will prepare the prerequisites and install the ticketing system we will be using in the next guides, osTicket, from scratch, using Azure. osTicket is an open source Help Desk ticketing system that you will most likely see being used frequently in many IT workspace settings. <br/>
<br/>

Need the files to follow along? They can be located [here.](https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6)
<br />


<h2>Environments and Utilities Used</h2>

- <b>Microsoft Azure</b>
- <b>Virtual Machines</b>
- <b>Remote Desktop Connection</b>
- <b>Internet Information Services</b>
- <b>MySQL</b>


<h2>Operating Systems Used </h2>

- <b>Windows 10</b>

<h2>Steps to Take:</h2>

<p align="center">
Head to Microsoft Azure and create a resource group: <br/>
<img src="https://i.imgur.com/H0croZs.png" height="80%" width="80%" alt="Setting Up in Azure">
<br />
<br />
<img src="https://i.imgur.com/uXIIs8F.png" height="80%" width="80%" alt="Setting Up in Azure">
<br />
<br />
After it's created, make a virtual machine next. Make sure the image is Windows 10:  <br/>
<img src="https://i.imgur.com/qX0jEjU.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Next, use Remote Desktop Connection to connect to the VM: <br/>
<img src="https://i.imgur.com/2o2w8cW.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Afterwards, install and enable IIS (Internet Information Servies) by going to Control Panel> Programs> Turn Windows Features On or Off> Internet Information Services and enable it then World Wide Web Services> Application Development Features and check the box for CGI:  <br/>
<img src="https://i.imgur.com/yKnBXiO.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Next, head on down to the Common HTTP Features dropdown in the same popup and check all boxes, then click "OK": <br/>
<img src="https://i.imgur.com/D8qX42e.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Type in the loopback IP (127.0.0.1) in the internet browser. If you see this page, that means the web server installed without any issue:  <br/>
<img src="https://i.imgur.com/RnXWPx7.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Now, install PHP manager for IIS Setup:  <br/>
<img src="https://i.imgur.com/m8zURKW.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Install IIS URL Rewrite Module:  <br/>
<img src="https://i.imgur.com/gSJFuvR.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Once those have installed I will create a PHP directory on the C drive:  <br/>
<img src="https://i.imgur.com/iK1B5hc.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Download PHP and extract the zip file in the PHP directory, and then download Microsoft Visual C++:  <br/>
<img src="https://i.imgur.com/OTugv8A.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Download MySQL. Click Typical, launch Configuration Wizard after installation, and click Standard Configuration:  <br/> 
<img src="https://i.imgur.com/ejtbi0J.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Next, input the login information. Keep the password in a safe place. Typing it out in a Notepad is not advised:  <br/>
<img src="https://i.imgur.com/ECaTnv8.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Open IIS as an admin:  <br/>
<img src="https://i.imgur.com/3IEYqch.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Next go to PHP Manager> Register new PHP version and choose the file shown below:  <br/>
<img src="https://i.imgur.com/K6BQ6RA.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Go back to osticketVM Home and hit Restart on the right-hand side:  <br/>
<img src="https://i.imgur.com/9FFBTGg.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Next up, download osTicket. Once it's finished, copy the upload file to the wwwroot file in the inetpub directory (the path is: C:/inetpub/wwwroot):  <br/>
<img src="https://i.imgur.com/KCuNBBI.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Rename upload file to osTicket:  <br/>
<img src="https://i.imgur.com/Kxs94vJ.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Reload IIS by restarting the server again, and then click Browse *80 (http) on the right-hand side:  <br/>
<img src="https://i.imgur.com/EMcYPhE.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
This page should open in your browser:  <br/>
<img src="https://i.imgur.com/VpHkqHn.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
You'll need to enable a couple of extensions. Head to Sites> Default Web Site> osTicket, then click PHP Manager> Enable or disable an extension. Enable php_imap.dll, php_intl.dll, and php_opcache.dll:  <br/>
<img src="https://i.imgur.com/8KwiLOz.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Now, there are more check marks on the osTicket page:
<img src="https://i.imgur.com/sZhwjY9.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Next up, browse in File Explorer to C:> osTicket> include> ost-sampleconfig.php and remove the "sample" from the name:  <br/>
<img src="https://i.imgur.com/9yof5Nw.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Right-click on ost-config.php> Properties> Security> Advanced> Disable Inheritance> Remove all inherited permissions from this object:  <br/>
<img src="https://i.imgur.com/3v0GAnk.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Click on the add button to add permissions to the file> Select a principal> type "everyone"> Check Names> OK> check all permissions> OK> Check Full Control> apply> OK:  <br/>
<img src="https://i.imgur.com/DhlvUdy.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Hit continue on the osTicket web page in the browser and fill out the set up page:  <br/>
<img src="https://i.imgur.com/6PdRN6A.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Install HeidiSQL from the setup links:  <br/>
<img src="https://i.imgur.com/3C0oibE.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
In HeidiSQL click New> Username = root> Password = mySQL password from mySQL setup> Open. Following that, right click Unnamed> Create> New Database> Name it osTicket> OK. Then continue to fill out the database portion of osTicket setup. Click Install Now in the osTicket site when done:  <br/>
<img src="https://i.imgur.com/i43oF0c.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Finally, before we're all done here, head to C:> inetpub> wwwroot> osTicket and look for the setup file and delete it. Then go to C drive> inetpub> wwwroot> osTicket> include. Right-click on ost-config.php> Properties> Security> Advanced> Select Everyone and click edit. Make sure that, out of all the boxes, ONLY the Read & Execute and Read boxes are checked, then click apply:  <br/>
<img src="https://imgur.com/EUGA49u.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
<img src="https://imgur.com/UNdkpyC.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />

<h2>There you have it-- that's how to install osTicket!</h2>
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
