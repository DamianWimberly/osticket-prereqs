<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Installation and Configuration</h1>
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

- In Azure, Navigate to **Virtual Machines** → **Create**.
  - Select a **Windows image**.
  - Name the VM (e.g., "osTicket"), create a new resource group and select a region.
  - Choose a size with **at least 2 vCPUs**.
  - Configure networking and storage, then deploy the VM.

<table>
  <tr>
    <td><img width="200" alt="1" src="https://github.com/user-attachments/assets/7e28700b-d45d-4ae7-8d12-ad935d9dbd1d">
</td>
    <td><img width="200" alt="2" src="https://github.com/user-attachments/assets/9e461661-b6c5-4507-bad4-694523fed780">
</td>
    <td><img width="200" alt="4 copy" src="https://github.com/user-attachments/assets/d8096391-2264-4f74-a555-5417b6e72cc2">
</td>
  </tr>
  <tr>
    <td>Create the VM in Azure</td>
    <td>Networking Settings</td>
    <td>VM Overview</td>
  </tr>
</table>



🔷 ***Connect to the VM***

- Use RDP to connect to the VM via its public IP address.

<table>
  <tr>
    <td><img width="200" alt="3" src="https://github.com/user-attachments/assets/ae14a1a6-f5ba-44e8-b69b-596f1888d1c1">
</td>
    <td><img width="200" height= "150" alt="4" src="https://github.com/user-attachments/assets/6a1ef0a9-946a-4e55-8ea3-ff20661ceaa5">
  <tr>
    <td>VM Public IP Address</td>
    <td>Connect via RDP</td></td>
  </tr>
</table>



🔷 ***Install Required Software***

- Download and extract **[osTicket-Installation-Files](https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD)** in the Windows VM
  - Install **HeidiSQL** (`HeidiSQL_12.3.0.6589_Setup`)
  - Install **MySQL 5.5.62** (`mysql-5.5.62-win32`, Typical Setup → Launch Configuration Wizard → Standard Configuration, Set Username: `root`, Password: `root`)
  - Install **PHP Manager for IIS** (`PHPManagerForIIS_V1.5.0`)
  - Install **RewriteModule** (`rewrite_amd64_en-US`)
  - Install **Visual C++ Redistributable** (`VC_redist.x86.`)
 
 <table>
  <tr>
    <td><img width="200" height="150" alt="12" src="https://github.com/user-attachments/assets/2e4e2d40-86ca-4cbb-83c1-319ed0cbb5c7">
</td>
    <td><img width="200" height="150" alt="13" src="https://github.com/user-attachments/assets/2a323a41-1cc4-47ee-9503-c0c100e2bc10">
</td>
    <td><img width="150" height="150" alt="Screenshot 2024-10-02 at 9 58 01 PM" src="https://github.com/user-attachments/assets/39172d2b-4c68-40a4-9c76-62d64b3785d7"><img width="150" height="150" alt="Screenshot 2024-10-02 at 9 58 45 PM" src="https://github.com/user-attachments/assets/f70941d3-aead-411a-bcab-5c61d05410fd"><img width="150" height="150" alt="Screenshot 2024-10-02 at 10 00 59 PM" src="https://github.com/user-attachments/assets/1cca1be2-c384-400c-a6f7-917aa312dc11"></td>
   
  </tr>
  <tr>
    <td>Download & Extract</td>
    <td>osTicket Installation Files</td>
    <td>MySQL Install & Configuration</td>
  </tr>
</table>


🔷 ***Enable IIS and CGI***

- Go to **Control** **Panel** > **Programs** > **Programs and Features**
  - Check ✔ **Internet Information Services** and ✔ **CGI** (under **World Wide Web Services** > **Application Development Features**)

<table>
  <tr>
    <td><img width="200" height="150" alt="6" src="https://github.com/user-attachments/assets/559268bd-9bb4-4e67-acc2-2de9ab4a4412">
</td>
    <td><img width="200" height="150" alt="7" src="https://github.com/user-attachments/assets/5342a34f-aded-44fc-a71f-2fc9a0a296af">
</td>
    <td><img width="200" height="150" alt="9" src="https://github.com/user-attachments/assets/a5dcc679-4b28-43b6-bf8a-7300189f0fbf">
</td>
  </tr>
  <tr>
    <td>Control Panel</td>
    <td>Features/ISS Enabled </td>
    <td>CGI Enabled</td>
  </tr>
</table>

🔷 ***Registering PHP in IIS***

- Create the directory `C:\PHP`.
  - Unzip **PHP 7.3.8** (`php-7.3.8-nts-Win32-VC15-x86.zip`) from the **osTicket-Installation-Files** folder into `C:\PHP`.

- **Open IIS as Admin**.

Register PHP
  - IIS > PHP Manager > `C:\PHP\php-cgi.exe`.
- **Reload IIS**:
  - Open IIS > Stop and Start the server.


 **Reload IIS**
- Open **IIS**, stop the server, and then restart it.

 ***Install osTicket***

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

 <table>
  <tr>
    <td><img src="path_to_image1" alt="Step 1" width="200"/></td>
    <td><img src="path_to_image2" alt="Step 2" width="200"/></td>
    <td><img src="path_to_image3" alt="Step 3" width="200"/></td>
    <td><img src="path_to_image2" alt="Step 4" width="200"/></td>
    <td><img src="path_to_image3" alt="Step 5" width="200"/></td>
    <td><img src="path_to_image3" alt="Step 6" width="200"/></td>
    <td><img src="path_to_image2" alt="Step 7" width="200"/></td>
    <td><img src="path_to_image3" alt="Step 8" width="200"/></td>
  </tr>
  <tr>
    <td>Step 1</td>
    <td>Step 2</td>
    <td>Step 3</td>
    <td>Step 4</td>
    <td>Step 5</td>
    <td>Step 6</td>
    <td>Step 7</td>
    <td>Step 8</td>
  </tr>
</table>
