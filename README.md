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
<img src="https://i.imgur.com/mNqDVnC.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
In order to download osTicket theres a lot of prerequesites. To start, I went to Control Panel, and to pressed "uninstall or change a program". From there on the left I clicked "Turn windows features on or off". After, I checked the boxes for "World Wide Web Services-> Application Development Features -> and CGI" this gives osTicket a web server to run on and CGI lets IIS (Internet Information Services) understand and execute PHP code (what osTicket uses).
</p>
<br />

<p>
<img src="https://i.imgur.com/9maKGGX.jpeg" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
In this step, I downloaded PHP manager for IIS, and Rewrite Module, these help IIS manage and read the PHP code that osTicket uses.
</p>
<br />

<p>
<img src="https://i.imgur.com/Cm4X69o.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
This next step is really simple, all I did was create a PHP folder inside my C drive (C:\PHP). This is for storage purposes and for osTicket to know where its data is being stored.
</p>
<br />

<p>
<img src="https://i.imgur.com/ljeCzln.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
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
<img src="https://i.imgur.com/uq29gES.jpeg" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, I downloaded MySQL, and changed the configuration to standard. After, I made the username and password "root, root". MySQL is a database management system that stores and organizes data for websites/apps (like osTicket). This is needed because MySQL is where all the data (like tickets, users, messages, etc.) gets stored in a structured way. The reasoning for changing the configuration is to ensure your MySQL setup is stable and ready for smaller setups like osTicket. As for the username and password being "root"... the user "root" is basically the default admin user for MySQL, similar to an admin account.
</p>
<br />

<p>
<img src="https://i.imgur.com/M8rtoc0.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
The next essential step, is to register PHP from within IIS. So I ran IIS as an admin and registered it. This essentially tells IIS that PHP is installed, manages it, and makes sure IIS knows how to execute PHP files.
</p>
<br />

<p>
<img src="https://i.imgur.com/4dVzbVO.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now, I needed to get the core osTicket files into C:\inetpub\wwwroot.. "wwwroot" is the default location on the IIS web server where websites are hosted. This is where IIS serves up the web pages when someone visits the site. To do this I unzipped the osTicket file, then found the "upload" folder, where the core osTicket files live - the application’s scripts, templates, database connection files, etc. From here I copied it into the C:\inetpub\wwwroot\, and renamed it to "osTicket" which just makes it easier to access via the browser. e.g. instead of "http://yourwebsite.com/upload", I can go to "http://yourwebsite.com". To make a long explanation short, this step essentially moves the osTicket application into the location where IIS can recognize and serve it as a live web application.
</p>
<br />

<p>
<img src="https://i.imgur.com/83QVb7u.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, I went into IIS-> sites -> default website -> osTicket, and clicked the "browse.80 (http)" on the right. It then opened osTicket installer (if you do everything correctly it should). When I opened it, I saw some green check marks and some red X's... this means I need to enable some extensions to make it compatable.
</p>
<br />

<p>
<img src="https://i.imgur.com/8o17kyI.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
In order to enable these extensions, I went back into IIS -> sites -> osTicket, then clicked PHP manager. At the bottom it says enable extentions, from there I went to enable these three extentions; php_opcache.dll, php_intl.dll, and php_imap.dll.. now ill explain what each of these do.. For "opcache", Instead of repeatedly running the same PHP scripts every time a page loads, opcache stores the compiled version of the code in memory, making things faster.. For "imap", it allows PHP to communicate with email servers using the IMAP protocol, and for osTicket this is useful for retrieving ticket updates via email.. Finally for "intl" (internationalization), it helps PHP handle things like dates, currencies, and other language-related features, and helps osTicket allow the app to display things properly in different languages or date/time formatting.
</p>
<br />

<p>
<img src="https://i.imgur.com/fumYnUk.jpeg" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, we need to turn the sample configuration file into the real thing, and change its permissions.. To do this, I went into C:\inetpub\wwwroot\osTicket\include\, at the bottom there is a file called "ost-sampleconfig.php". I simply changed the name to "ost-config.php". Next, I right clicked it, went to properties->security->advanced. From there I removed all inherited permissions. Then I gave everyone full control. I did this so any user accessing the osTicket files, has permission to read, write, and modify those files as needed. (for the lab purposes of course).
</p>
<br />

<p>
<img src="https://i.imgur.com/BbA72uO.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now, all I did was go back into the osTicket webpage and put in my helpdesk info; such as the helpdesks name, email, and the admin user's information as well.
</p>
<br />

<p>
<img src="https://i.imgur.com/HVXjkFy.jpeg" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, I downloaded HeidiSQL. HeidiSQL allows me to connect to my MySQL server (the one I set up earlier) and create the actual database where osTicket will store all its data. Then from within HeidiSQL, I created a new session called "root", and inside that session I created a database called "osTicket".
</p>
<br />

<p>
<img src="https://i.imgur.com/SiHZWTh.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now all that was left to do was, go back into osTicket, and fill in the database information with the one I just created in HeidiSQL, and press install!!!
</p>
<br />

<p>
<img src="https://i.imgur.com/79ldsuP.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
BOOM!! After pressing install, osTicket was installed and I had access to the ticket creator AND the staff control panel. :)
<br />
