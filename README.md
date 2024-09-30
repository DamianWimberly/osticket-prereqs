<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket. Installing its dependencies (such as PHP, MySQL, and a web server like ISS) during the initial setup ensures the software has the necessary components to run smoothly, handle database operations, and serve the web interface properly.<br />




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- [osTicket-Installation-Files](https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD)
- Azure Virtual Machine (VM) Setup
- RDP
- IIS
- PHP
- MySQL 5.5.62
- Visual C++ Redistributable
- HeidiSQL

<h2>Installation Steps</h2>

🔷 ***Create an Azure Virtual Machine***

- Log in to the Azure portal.
- Navigate to **Virtual Machines** → **Create**.
- Select a **Windows image**.
- Name the VM (e.g., "osTicket"), create a new resource group and select a region.
- Choose a size with **at least 2 vCPUs**.
- Configure networking and storage, then deploy the VM.

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

🔷 ***Connect to the VM***

- Use RDP to connect to the VM via its public IP address.

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

🔷 ***Install Required Software***

- **Install Visual C++ Redistributable** (`VC_redist.x86.exe` from "osTicket-Installation-Files").
- **Install MySQL 5.5.62** (`mysql-5.5.62-win32.msi`, Typical Setup).
  - Launch Configuration Wizard → Standard Configuration.
  - Set Username: `root`, Password: `root`.

  <p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

🔷 ***Set Up IIS and PHP***

- Open **IIS** as Admin.
- Register PHP: PHP Manager → `C:\PHP\php-cgi.exe`.
- Reload IIS (Stop/Start the server).

  <p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

🔷 ***Install osTicket***

- Unzip `osTicket-v1.15.8.zip` and move the "upload" folder to `C:\inetpub\wwwroot`. Rename it to "osTicket."
- Reload IIS and browse to **Sites** → **Default** → **osTicket** → **Browse *:80**.

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

🔷 ***Enable PHP Extensions***

- Enable in PHP Manager:
  - `php_imap.dll`
  - `php_intl.dll`
  - `php_opcache.dll`
- Reload IIS and refresh the osTicket site.

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

🔷 ***Configure osTicket Settings***

- Rename `ost-sampleconfig.php` to `ost-config.php` (`C:\inetpub\wwwroot\osTicket\include`).
- Set permissions for `ost-config.php`:
  - Disable inheritance → Remove All.
  - Grant Full Control to "Everyone."

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

🔷 ***Finalize Installation***

- Complete setup in the browser (helpdesk name, default email).
- **Install HeidiSQL**, create a session (`root/root`), and create a database named "osTicket."
- Finalize setup in the browser:
  - Database: `osTicket`, Username: `root`, Password: `root`.
  - Click **Install Now!**

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
