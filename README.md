<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop Protocol (RDP)
- Internet Information Services (IIS)
- MySQL
- PHP

<h2>Operating Systems Used</h2>

- Windows 10 (21H2)

<h2>List of Prerequisites</h2>

- Azure Subscription and access to the Azure Portal
- Ability to create and connect to a Windows 10 VM
- Remote Desktop Connection enabled
- Basic knowledge of IIS, PHP, and MySQL
- osTicket Installation Files (provided zip folder)

<h2>Installation Steps</h2>

<h3>1. Create Azure Virtual Machine</h3>
<p>
  
<img src="https://i.imgur.com/cy8s7yg.png" height="80%" width="80%" alt="Creating Azure VM"/>
</p>
<p>
Create a Windows 10 Virtual Machine in Azure with the following specifications:
<ul>
  <li>Name: <b>osticket-vm</b></li>
  <li>Username: <b>labuser</b></li>
  <li>Password: <b>osTicketPassword1!</b></li>
  <li>Size: At least 2 vCPUs</li>
</ul>
Connect using Remote Desktop once the VM is running.
</p>
<br />

<h3>2. Setup and Configure IIS with Required Features</h3>
<p>
<img src="https://i.imgur.com/116qaJn.png" height="80%" width="80%" alt="Installing IIS"/>
</p>
<p>
Enable IIS and CGI:
<pre>
Control Panel → Programs and Features → Turn Windows features on or off →
✔ Internet Information Services
  ✔ World Wide Web Services
    ✔ Application Development Features
      ✔ CGI
</pre>
</p>
<br />

<h3>3. Install osTicket Dependencies</h3>
<p>
<img src="https://i.imgur.com/Qn6turJ.png" height="80%" width="80%" alt="Installing Dependencies"/>
</p>
<p>
Inside the <code>osTicket-Installation-Files</code> folder:
<ul>
  <li>Install <b>PHP Manager for IIS</b></li>
  <li>Install <b>URL Rewrite Module</b></li>
  <li>Create folder <code>C:\PHP</code> and extract PHP 7.3.8 into it</li>
  <li>Install <b>VC_redist.x86.exe</b></li>
  <li>Install <b>MySQL 5.5.62</b> (Typical Setup → Standard Configuration)</li>
  <li>Username: <b>root</b>, Password: <b>root</b></li>
</ul>
</p>
<br />

<h3>4. Configure IIS and PHP</h3>
<p>
<img src="https://i.imgur.com/Yjb12LX.png" height="80%" width="80%" alt="PHP Manager Configuration"/>
</p>
<p>
Use PHP Manager in IIS to register PHP:
<code>C:\PHP\php-cgi.exe</code><br/>
Restart IIS (stop and start the server).
</p>
<br />

<h3>5. Install osTicket</h3>
<p>
<img src="https://i.imgur.com/jvvF35P.png" height="80%" width="80%" alt="osTicket Files"/>
</p>
<p>
Unzip <code>osTicket-v1.15.8.zip</code> from the installation files and:
<ol>
  <li>Copy the <code>upload</code> folder into <code>C:\inetpub\wwwroot</code></li>
  <li>Rename <code>upload</code> to <code>osTicket</code></li>
  <li>Restart IIS</li>
  <li>Browse to: <code>http://localhost/osTicket</code></li>
</ol>
</p>
<br />

<h3>6. Enable PHP Extensions</h3>
<p>
<img src="https://i.imgur.com/bgFXRBZ.png" height="80%" width="80%" alt="PHP Extensions"/>
</p>
<p>
In IIS:
<ol>
  <li>Sites → Default → osTicket → PHP Manager</li>
  <li>Enable these extensions:
    <ul>
      <li>php_imap.dll</li>
      <li>php_intl.dll</li>
      <li>php_opcache.dll</li>
    </ul>
  </li>
</ol>
Refresh the osTicket page to verify the extensions are enabled.
</p>
<br />

<h3>7. Configure osTicket</h3>
<p>
<img src="https://i.imgur.com/osr8lfJ.png" height="80%" width="80%" alt="Configuring osTicket"/>
</p>
<p>
<ol>
  <li>Rename: <code>ost-sampleconfig.php</code> → <code>ost-config.php</code></li>
  <li>Location: <code>C:\inetpub\wwwroot\osTicket\include\</code></li>
  <li>Set permissions: Disable inheritance → Remove all → Grant Everyone Full Control</li>
</ol>
</p>
<br />

<h3>8. Create MySQL Database</h3>
<p>
<img src="https://i.imgur.com/eAOW5uO.png" height="80%" width="80%" alt="HeidiSQL"/>
</p>
<p>
Install HeidiSQL and:
<ol>
  <li>Create new session using root/root</li>
  <li>Create a new database named <code>osTicket</code></li>
</ol>
</p>
<br />

<h3>9. Finalize Installation</h3>
<p>
<img src="https://i.imgur.com/Ou8bHgw.png" height="80%" width="80%" alt="Final Setup"/>
</p>
<p>
Return to the browser setup page:
<ol>
  <li>Database: <code>osTicket</code></li>
  <li>Username: <code>root</code></li>
  <li>Password: <code>root</code></li>
  <li>Click <b>Install Now!</b></li>
</ol>
You should see a success message and be redirected to the login page:
<code>http://localhost/osTicket/scp/login.php</code>
</p>
<br />

<h3>10. Post-Installation Cleanup</h3>
<p>
<ol>
  <li>Delete: <code>C:\inetpub\wwwroot\osTicket\setup</code></li>
  <li>Set <code>ost-config.php</code> permissions to <b>Read-only</b></li>
</ol>
</p>
<h2>Conclusion</h2>
<p>
  Setting up osTicket on a Windows 10 VM in Azure is a perfect way to get hands-on experience with web configurations, database management, and deploying real-life applications. You work with tools like IIS, PHP,  and MySQL, and observe how everything is put together to support a full-fledged help desk system. 
</p>
<p>
  Now that osTicket is running, we are ready to manage support tickets and explore more advanced features.
</p>

<br />
