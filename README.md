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

- Install / Enable IIS in Windows with CGI
- Install PHP Manager for IIS
- Install the Rewrite Module
- Create PHP folder in C drive
- Unzip the PHP Installer Package into the PHP folder
- Install Visual C++ Redistributable or VC_Redist
- Install and Configure MySQL
- From within IIS as an admin, register PHP
- Unzip osTicket Installation Files, then copy the "upload" file into c:\inetpub\wwwroot and rename to "osTicket"
- Enable extentions so osTicket displays properly
- Rename Sampleconfig to "ost-config"
- Assign permissions to ost-config
- Name your helpdesk / input your info
- Install HeidiSQL
- Create a new session, root/root
- Create a database in the session called "osTicket"
- Input database info into osTicket and install!

<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/mNqDVnC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Within Control Panel, you want to press "uninstall or change a program". From there on the left you want to click "Turn windows features on or off". After, you want to check the box for "World Wide Web Services-> Application Development Features -> and CGI" this gives osTicket a web server to run on and CGI lets IIS understand and execute PHP code (what osTicket uses).
</p>
<br />

<p>
<img src="https://i.imgur.com/9maKGGX.jpeg" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
In this step, you want to download PHP manager for IIS, and Rewrite Module, these help IIS manage and read the PHP code that osTicket uses.
</p>
<br />

<p>
<img src="https://i.imgur.com/Cm4X69o.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
This next step is really simple, you just want to create a PHP folder inside your C drive (C:\PHP). This is for storage purposes and for osTicket to know where its data is being stored.
</p>
<br />

<p>
<img src="https://i.imgur.com/nFHK8tr.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
In this step, I unzipped the PHP Installer package into the PHP folder I just created in my C drive. 
</p>
<br />

<p>
<img src="https://i.imgur.com/kNPSNmr.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
I then downloaded VC_redist (Visual C++ redistributable), this is important because PHP needs VC_Redist libraries to run properly on windows. VC_Redist downloads these libraries onto your computer so PHP has access to these tools to do things like read files, interact with IIS, and even something as simple as running the code smoothly.
</p>
<br />

<p>
<img src="https://i.imgur.com/Cm4X69o.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
This next step is really simple, you just want to create a PHP folder inside your C drive (C:\PHP). This is for storage purposes and for osTicket to know where its data is being stored.
</p>
<br />

<p>
<img src="https://i.imgur.com/Cm4X69o.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
This next step is really simple, you just want to create a PHP folder inside your C drive (C:\PHP). This is for storage purposes and for osTicket to know where its data is being stored.
</p>
<br />
