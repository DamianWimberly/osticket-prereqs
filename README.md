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
    <td><img width="100" height="100" alt="Screenshot 2024-10-02 at 9 58 01 PM" src="https://github.com/user-attachments/assets/39172d2b-4c68-40a4-9c76-62d64b3785d7"><img width="100" height="100" alt="Screenshot 2024-10-02 at 9 58 45 PM" src="https://github.com/user-attachments/assets/f70941d3-aead-411a-bcab-5c61d05410fd"><img width="100" height="100" alt="Screenshot 2024-10-02 at 10 00 59 PM" src="https://github.com/user-attachments/assets/1cca1be2-c384-400c-a6f7-917aa312dc11"></td>
   
  </tr>
  <tr>
    <td>Download & Extract</td>
    <td>osTicket Installation Files</td>
    <td>MySQL Configuration</td>
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

- Create the directory `C:\PHP`
  - Unzip **PHP 7.3.8** (`php-7.3.8-nts-Win32-VC15-x86.zip`) from the **osTicket-Installation-Files** folder into `C:\PHP`.

- Register PHP
    - IIS(open as admin) > PHP Manager > `C:\PHP\php-cgi.exe`.
    - Reload IIS: Stop and Start the server
 <table>
  <tr>
    <td><img width="200" height="150" alt="Screenshot 2024-10-05 at 9 12 10 AM" src="https://github.com/user-attachments/assets/b1127462-7e07-4b0e-8aeb-10bc5710f7f9"></td>
    <td><img width="100" height="75" alt="Screenshot 2024-10-05 at 9 14 41 AM 1" src="https://github.com/user-attachments/assets/8ec72176-5a7d-4f08-8c06-56a5790ea898"><img width="100" height="75" alt="Screenshot 2024-10-05 at 9 15 53 AM" src="https://github.com/user-attachments/assets/4cfa70fa-91f9-43ff-8048-632907adf72d"></td>
    <td><img width="200" height="150" alt="Screenshot 2024-10-05 at 9 41 07 AM" src="https://github.com/user-attachments/assets/1aa4e66d-a4a8-42f1-b317-8e5093e7d8a1"></td>
    <td><img width="100" height="75" alt="Screenshot 2024-10-05 at 9 42 20 AM" src="https://github.com/user-attachments/assets/e5e49ef9-7936-4926-88be-4032ce42a756"><img width="100" height="75" alt="Screenshot 2024-10-05 at 9 42 45 AM" src="https://github.com/user-attachments/assets/ec0c7407-96ce-4c5b-b846-7ddf848f8cf5"><img width="200" height="75" alt="Screenshot 2024-10-05 at 9 43 55 AM" src="https://github.com/user-attachments/assets/04ceb4cd-5396-41e5-a4cf-b15290a84cb9"></td>
    <td><img width="200" height="150" alt="Screenshot 2024-10-05 at 9 45 05 AM" src="https://github.com/user-attachments/assets/9083dda2-b9b8-44fe-90db-34872166324e"></td>  
  </tr>
  <tr>
    <td>Create C:\PHP</td>
    <td>Unzip PHP 7.3.8 into C:\PHP</td>
    <td>Open IIS</td>
    <td>Register PHP</td>
    <td>Restart the Server</td>
  </tr>
</table>

🔷  ***Install osTicket***

- Unzip `osTicket-v1.15.8.zip` and move the "upload" folder to `C:\inetpub\wwwroot`. Rename it to "osTicket."
- Reload IIS and browse to **Sites** → **Default** → **osTicket** → **Browse*:80(http)**.

 <table>
  <tr>
    <td><img width="200" height="150" alt="Screenshot 2024-10-05 at 10 35 55 AM" src="https://github.com/user-attachments/assets/894092d5-c8d6-4ce4-aa6a-16b50691d28b"><img width="200" height="150" alt="Screenshot 2024-10-05 at 1 46 47 PM" src="https://github.com/user-attachments/assets/10c61aaa-c320-4e56-8db9-389eb224697f"> </td>
    <td><img width="200" height="150" alt="Screenshot 2024-10-05 at 10 41 29 AM" src="https://github.com/user-attachments/assets/14b27f6c-38fc-4720-8182-396fe5430e8f"><img width="200" height="150" alt="Screenshot 2024-10-05 at 10 42 17 AM" src="https://github.com/user-attachments/assets/c4440a0c-ca96-4a31-aa60-7efdad79bcba"></td>
    <td><img width="200" height="150" alt="Screenshot 2024-10-05 at 10 46 41 AM" src="https://github.com/user-attachments/assets/b2366c1a-8012-424f-8c60-097ed166ceb4"></td>
    <td><img width="200" height="150" alt="Screenshot 2024-10-05 at 10 52 26 AM" src="https://github.com/user-attachments/assets/04e96774-c975-4da3-8bdd-a1736b1e4e7d"></td>
  </tr>
  <tr>
    <td>Unzip osTicket-v1.15.8.zip</td>
    <td>"Upload" → "osTicket" in C:\inetpub\wwwroot</td>
    <td>Restart/Browse:80(http)</td>
    <td>Installer Loaded</td>
  </tr>
</table>

🔷 ***Enable PHP Extensions*** 

- Enable in PHP Manager:
  - `php_imap.dll`
  - `php_intl.dll`
  - `php_opcache.dll`
- Reload IIS and refresh the osTicket site.

 <table>
  <tr>
    <td><img width="200" height="150" alt="Screenshot 2024-10-05 at 2 55 20 PM" src="https://github.com/user-attachments/assets/88caf99b-1dd7-41c6-9439-12b3c605a7f1"><img width="200" height="150" alt="Screenshot 2024-10-05 at 10 54 20 AM" src="https://github.com/user-attachments/assets/4fdd508f-5005-40d8-9b77-0a825b255833"></td>
    <td><img width="200" height="150" alt="Screenshot 2024-10-05 at 10 55 13 AM" src="https://github.com/user-attachments/assets/a93d9f6f-3e3f-4084-8144-e6708b06ff06">
</td>
    <td><img width="200" height="150" alt="Screenshot 2024-10-05 at 10 56 34 AM" src="https://github.com/user-attachments/assets/5e455b46-8ae6-4689-a15c-ceb4f7bf0c2c"></td>
  </tr>
  <tr>
    <td>Step 1</td>
    <td>Step 2</td>
    <td>Step 3</td>
  </tr>
</table>

🔷 ***Configure osTicket Settings***

- Rename `ost-sampleconfig.php` to `ost-config.php` (C:\inetpub\wwwroot\osTicket\include\ost-config.php).
- Set permissions for `ost-config.php`:
  - Properties > Security > Advanced:
      - Disable inheritance → Remove All.
      - Grant Full Control to "Everyone."

 <table>
  <tr>
    <td><img width="200" height="150" alt="Screenshot 2024-10-05 at 11 06 00 AM" src="https://github.com/user-attachments/assets/8c20bf48-db0d-44b1-a0c2-4bee0bd7e746"><img width="200" height="150" alt="Screenshot 2024-10-05 at 11 07 15 AM" src="https://github.com/user-attachments/assets/cf6bc448-b69c-416d-ae13-c212c011b87d"></td>
    <td><img width="200" height="150" alt="Screenshot 2024-10-05 at 11 07 49 AM" src="https://github.com/user-attachments/assets/44da5dab-66fd-4007-a506-22ce5faca4e1"><img width="200" height="150" alt="Screenshot 2024-10-05 at 11 10 50 AM" src="https://github.com/user-attachments/assets/0d4ae01c-3268-41a0-b7ba-043388bfa711"></td>
    <td><img width="200" height="150" alt="Screenshot 2024-10-05 at 11 12 27 AM" src="https://github.com/user-attachments/assets/6926ad28-92f5-463b-b1a6-ce73eacb7cba"><img width="200" height="150" alt="Screenshot 2024-10-05 at 11 15 18 AM" src="https://github.com/user-attachments/assets/0b27648d-3ef2-4d94-b620-be7ce0c3ea2f"></td>
  </tr>
  <tr>
    <td>Step 1</td>
    <td>Step 2</td>
    <td>Step 3</td>
  </tr>
</table>

🔷 ***Finalize Installation***

- Launch **HeidiSQL**, create a session (`root/root`), and create a database named "osTicket."
- Finalize setup in the browser:
  - Helpdesk name, default email, username/password
  - Database: `osTicket`, Username: `root`, Password: `root`.
  - Click **Install Now!**

 <table>
  <tr>
    <td><img width="200" height="150" alt="Screenshot 2024-10-05 at 11 26 59 AM" src="https://github.com/user-attachments/assets/6aa0b23c-d7ec-44f0-b83c-501860f4034e"></td>
    <td><img width="200" height="150" alt="Screenshot 2024-10-05 at 11 32 51 AM" src="https://github.com/user-attachments/assets/406a6e04-2c3b-4fc5-9299-16c8271f4e81"><img width="200" height="150" alt="Screenshot 2024-10-05 at 11 34 11 AM" src="https://github.com/user-attachments/assets/4e9720cc-89c7-4935-891c-9267a7123bcd"></td>
    <td><img width="200" height="150" alt="Screenshot 2024-10-05 at 11 35 49 AM" src="https://github.com/user-attachments/assets/31f631d0-38cb-4861-8021-1a5340dd7f67"><img width="200" height="150" alt="Screenshot 2024-10-05 at 11 36 00 AM" src="https://github.com/user-attachments/assets/d0c345e4-c805-456f-a61d-1ed7ac7f14ae"></td>
    <td><img width="200" height="150" alt="Screenshot 2024-10-05 at 11 36 42 AM" src="https://github.com/user-attachments/assets/a8176c41-0c2c-4832-aa92-94880e2103d4"></td>
  </tr>
  <tr>
    <td>Step 1</td>
    <td>Step 2</td>
    <td>Step 3</td>
    <td>Step 4</td>
  </tr>
</table>
