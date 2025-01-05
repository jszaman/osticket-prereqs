<p align="center">
<img src="https://i.imgur.com/SIOPg5j.png" alt="1"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>

This lab provides a step-by-step guide to installing osTicket, an open-source help desk ticketing system. It includes information on the prerequisites for installation and the installation process itself.

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute) 
- Remote Desktop (RDP)
- OsTicket 

<h2>Operating Systems Used </h2>

- Windows 10 Pro (22H2)

<h2>osTicket Installation Files</h2>

https://drive.google.com/drive/folders/1mKAD1ZaP1e3F0FInXuAlQ3Pcucz4Mb3O?usp=sharing

<h2>List of Prerequisites</h2>

 - Create a Resource Group
 - Create an Azure Virtual Machine
 - Install and enable IIS (Internet Information Services)
 - Install "PHPManagerForIIS_V1.5.0.msi"
 - Install "rewrite_amd64_en-US.msi"
 - Create the "C\PHP" directory
 - Extract "php-7.3.8-nts-Win32-VC15-x86.zip" to the "C\PHP" directory
 - Install "VC_redist.x86.exe"
 - Install "mysql-5.5.62-win32.msi"
 - Register PHP from within IIS
 - Install osTicket


<h2>Installation Steps</h2>

<p align="center">
<img src="https://i.imgur.com/jJAiw1z.png" height="80%" width="80%" alt="img"/>
</p>

Go to your Azure portal https://portal.azure.com/ and login. In your Azure home page, click the search bar and search for "resource group". Click "Resource groups".

<p align="center">
<img src="https://i.imgur.com/q30fcm3.png" height="80%" width="80%" alt="img"/>
</p>

Click the "Create" tab at the top left.

<p align="center">
<img src="https://i.imgur.com/G0iY3xD.png" height="80%" width="80%" alt="img"/>
</p>

Select your Azure subscription, we will name the resource group "RG-osTicket". Select "(US) West US 3" for the Region, and click the "Review + create" tab at the bottom left. 

<p align="center">
<img src="https://i.imgur.com/kaWmyCc.png" height="80%" width="80%" alt="img"/>
</p>

Click the notification tab at the top right and confirm that the resource group "RG-osTick" has been created.

<p align="center">
<img src="https://i.imgur.com/yOJUCM3.png" height="80%" width="80%" alt="img"/>
</p>

Click the search bar and search for "virtual machine". Click "Virtual machines".

<p align="center">
<img src="https://i.imgur.com/FFhfzEL.png" height="80%" width="80%" alt="img"/>
</p>

Click the "Create" tab at the top left and select "Azure virtual machine".

<p align="center">
<img src="https://i.imgur.com/rKd4Hxw.png" height="80%" width="80%" alt="img"/>
</p>

Select your Azure subsription, select the resource group we created earlier "RG-osTicket", name the virtual machine "vm-osticket", select (US) West US 3 for the region, select "No infrastructure redundancy required" for the availability options, select "Standard" for Security type, select "Windows 10 Pro, version 22H2 - x64 Gen2 (free eligible services)" for Image, leave VM architecture as defualt, select "Standard_D4s_v3 - 4 vcpus, 16 GiB memory" for the Size. We will use "labuser" as the username, and make sure you use a unique password.

NOTE: Write down your username and password, we will need it later.

Leave "Public inbound ports" and select inbound ports" as default. Check the licensing box and click the Networking tab at the top.

<p align="center">
<img src="https://i.imgur.com/aUVAOqk.png" height="80%" width="80%" alt="img"/>
</p>

The Virtual network (NIC), Subnet, and Public IP will automatically be created for us, so make sure they all say (new). Leave every thing as default, and click "Review + create" tab at the bottom left. 

<p align="center">
<img src="https://i.imgur.com/IWBDQZj.png" height="80%" width="80%" alt="img"/>
</p>

The "Validation pass" message indicates that all of the required information has been provided and that the VM can be created. Go ahead an click the "Create" tab at the bottom left.

<p align="center">
<img src="https://i.imgur.com/RNQ208q.png" height="80%" width="80%" alt="img"/>
</p>

The "Validation is in progress" message indicates that the Virtual machine is being created and configured. This process can take several minutes.

<p align="center">
<img src="https://i.imgur.com/BZxxbil.png" height="80%" width="80%" alt="img"/>
</p>

The message "Your deployment is complete" means that the Azure virtual machine (VM) has been successfully created and configured.

<p align="center">
<img src="https://i.imgur.com/oV6Qwyj.png" height="80%" width="80%" alt="img"/>
</p>

Click the search bar, and click "Virtual machines".

<p align="center">
<img src="https://i.imgur.com/O8O0QBq.png" height="80%" width="80%" alt="img"/>
</p>

Click the virtual machine we just created.

<p align="center">
<img src="https://i.imgur.com/wGfGhSB.png" height="80%" width="80%" alt="img"/>
</p>

Copy the Public IP address.

<p align="center">
<img src="https://i.imgur.com/gChFsZc.png" height="80%" width="80%" alt="img"/>
</p>

On your local computer search box, search for "remote desktop", and click "Open"

<p align="center">
<img src="https://i.imgur.com/dDYXiBF.png" height="80%" width="80%" alt="img"/>
</p>

Paste your VMs Public IP address you copied and click the "Connect" button.

<p align="center">
<img src="https://i.imgur.com/neUPf5p.png" height="80%" width="80%" alt="img"/>
</p>

Click "More choices" > "Use a different account", go ahead and login with the username and password you used when you created your virtual machine, and click "Ok". 

<p align="center">
<img src="https://i.imgur.com/2ZPAvQj.png" height="80%" width="80%" alt="img"/>
</p>

We've now loged into our virtual machine. Select "No" for the options and click the "Accept" button.

<p align="center">
<img src="https://i.imgur.com/eRw8ia9.png" height="80%" width="80%" alt="img"/>
</p>

Select the "Yes" button.

Copy this link https://drive.google.com/drive/folders/1mKAD1ZaP1e3F0FInXuAlQ3Pcucz4Mb3O?usp=sharing 

This link contains all the installation files we will need. We will open it up inside the virtual machine because it's much easier to deal with there.

<p align="center">
<img src="https://i.imgur.com/R9bRAnY.png" height="80%" width="80%" alt="img"/>
</p>

In your virtual machine, double-click the "Microsoft Edge" application to open it.

<p align="center">
<img src="https://i.imgur.com/ARKjwcV.png" height="80%" width="80%" alt="img"/>
</p>

Click "Search without your data" > "Don't allow" > "Confirm and continue" > "Continue without this data" > "Confirm and start browsing". 

<p align="center">
<img src="https://i.imgur.com/rk6m5EW.png" height="80%" width="80%" alt="img"/>
</p>

Paste the link you copied in the search bar and press the Enter key. We will come back to this page later.

We will now install and enable IIS

<p align="center">
<img src="https://i.imgur.com/xvSMNcH.png" height="80%" width="80%" alt="img"/>
</p>

NOTE: Internet Information Services (IIS) is a web server that osTicket runs on. Microsoft created IIS, and it can be used to host a wide variety of websites and web applications.

Right-click the Start Menu and click "Run".

<p align="center">
<img src="https://i.imgur.com/jXSncgO.png" height="80%" width="80%" alt="img"/>
</p>

Type "control" and click the "Ok" button.

<p align="center">
<img src="https://i.imgur.com/PArDvYE.png" height="80%" width="80%" alt="img"/>
</p>

Click "Programs".

<p align="center">
<img src="https://i.imgur.com/x2YcYev.png" height="80%" width="80%" alt="img"/>
</p>

Click "Turn Windows features on or off".

<p align="center">
<img src="https://i.imgur.com/yxo745J.png" height="80%" width="80%" alt="img"/>
</p>

Scroll to "Internet Information Services" and check the box; click the plus (+) to expand it. Expand "World Wide Web Services", expand "Application Development Features", go ahead and check "CGI".

<p align="center">
<img src="https://i.imgur.com/UuVvmoH.png" height="80%" width="80%" alt="img"/>
</p>

Collaps "Application Development Features" and expand "Common HTTP Features". Make sure all the boxes are checked, and click the "Ok" button. 

<p align="center">
<img src="https://i.imgur.com/LZ7RzhM.png" height="80%" width="80%" alt="img"/>
</p>

The image above shows that the IIS web services are being installed.

<p align="center">
<img src="https://i.imgur.com/Qx022SW.png" height="80%" width="80%" alt="img"/>
</p>

IIS is now installed, click the "Close" button.

<p align="center">
<img src="https://i.imgur.com/7Ijcz0x.png" height="80%" width="80%" alt="img"/>
</p>

To confirm if IIS was actually installed on our VM, open Microsoft Edge, search for "127.0.0.1" on the search bar, and click Enter.

NOTE: "127.0.0.1" is the loopback address, which is a special IP address that maps to the local computer. It's essentially saying, "Try to load a webpage that's running off myself". So, it loaded the default IIS website, which confirms that the webservices are working.

If it loads a page like the one in the image above, it means the installation was successful.

<p align="center">
<img src="https://i.imgur.com/EppfODe.png" height="80%" width="80%" alt="img"/>
</p>

Next, we will download and install "PHPManagerForIIS_V1.5.0.msi".

Go back to the osTicket installation files web page, and click "PHPManagerForIIS_V1.5.0.msi".

<p align="center">
<img src="https://i.imgur.com/mgAXtVg.png" height="80%" width="80%" alt="img"/>
</p>

Click "Download".

<p align="center">
<img src="https://i.imgur.com/pCPkNq1.png" height="80%" width="80%" alt="img"/>
</p>

Disregard the warning and click "Download Anyway".

<p align="center">
<img src="https://i.imgur.com/cWtF26W.png" height="80%" width="80%" alt="img"/>
</p>

After it's downloaded, double-click "File Explore" in the taskbar.

<p align="center">
<img src="https://i.imgur.com/7b7NSYM.png" height="80%" width="80%" alt="img"/>
</p>

Click "Downloads" and double-click "PHPManagerForIIS_V1.5.0". PHPManagerForIIS_V1.5.0 installation window will pop up. Click "Next", select "I Agree" and click "Next" > "Close".

Close File Explorer.

<p align="center">
<img src="https://i.imgur.com/YLRxOsU.png" height="80%" width="80%" alt="img"/>
</p>

If you can't download any of the files, click the down arrow in the search bar, select "continue allowing automatic downloads of multiple files", and click "Done".

Go back to the osTicket installation files web page and download "rewrite_amd64_en-US.msi" just as we did for "PHPManagerForIIS_V1.5.0".

NOTE: The "rewrite_amd64_en-US.msi" allows osTicket to use URL rewriting. URL rewriting is a technique that allows us to change the way that URLs are displayed to users.

<p align="center">
<img src="https://i.imgur.com/GXvIgT5.png" height="80%" width="80%" alt="img"/>
</p>

After it's downloaded, click "File Explore" in the taskbar. Double-click "rewrite_amd64_en-US", check the license agreement box, and click "Next" > "Install" > "Finish".

<p align="center">
<img src="https://i.imgur.com/CwWRA0w.png" height="80%" width="80%" alt="img"/>
</p>

Let's create the "C\PHP" directory.

Open File Explorer, click "This PC" and double-click "Windows C:". 

<p align="center">
<img src="https://i.imgur.com/JbiNrb7.png" height="80%" width="80%" alt="img"/>
</p>

In "Windows C:", right-click on an empty space, click "New", click "Folder".

<p align="center">
<img src="https://i.imgur.com/glMjIz4.png" height="80%" width="80%" alt="img"/>
</p>

Create a folder called "PHP"

<p align="center">
<img src="https://i.imgur.com/x53XakV.png" height="80%" width="80%" alt="img"/>
</p>

Next let's download "php-7.3.8-nts-Win32-VC15-x86.zip".

Dowload it just as we did for previous files.

<p align="center">
<img src="https://i.imgur.com/NcnbWFZ.png" height="80%" width="80%" alt="img"/>
</p>

Go back to File Explorer and right-click "php-7.3.8-nts-Win32-VC15-x86.zip". Click "Extract All".

<p align="center">
<img src="https://i.imgur.com/v5ctOpy.png" height="80%" width="80%" alt="img"/>
</p>

Click "Browse" > "This PC" and double-click "Windows C:", 

<p align="center">
<img src="https://i.imgur.com/QfA1eWV.png" height="80%" width="80%" alt="img"/>
</p>

Select "PHP" by clicking it once. Click the "Select Folder" button.

<p align="center">
<img src="https://i.imgur.com/ULRSYUq.png" height="80%" width="80%" alt="img"/>
</p>

After selecting "PHP", click "Extract". Close File Explorer

<p align="center">
<img src="https://i.imgur.com/Ab8XqyG.png" height="80%" width="80%" alt="img"/>
</p>

Next, let's download and install "VC_redist.x86.exe".

NOTE: "VC_redist.x86.exe" provides C++ runtime libraries (libraries that provide basic functionality for C++ programs, such as memory management, input/output, and string manipulation) that are required for osTicket to run

Go back to osTicket installation files web page and download "VC_redist.x86.exe". After it's downloaded, open File Explore, click on "Downloads", and double-click "VC_redist.x86.exe" to start the installation. Check the license agreement box and click "Install" > "Close".

<p align="center">
<img src="https://i.imgur.com/XcQxsWt.png" height="80%" width="80%" alt="img"/>
</p>

Next, we will download and install "mysql-5.5.62-win32.msi". 

Go back to osTicket installation files web page and download "mysql-5.5.62-win32.msi". Open File Explore, click on "Downloads", and double-click "mysql-5.5.62-win32.msi". Click "Next", check the license agreement box and click "Next" > "Typical install" > "Install" > "Finish".

<p align="center">
<img src="https://i.imgur.com/kN9pc0l.png" height="80%" width="80%" alt="img"/>
</p>

Now, we will configure MySQL. Click "Next" > "Standard Configuration" > "Next" > "Next".

Let's set up our root username and password. Our password will be "Password1". Click "Next" > "Execute" > "Finish".

<p align="center">
<img src="https://i.imgur.com/e4dJEyJ.png" height="80%" width="80%" alt="img"/>
</p>

Let's register PHP from within IIS

Search for "iis" in the search box, click "Run as administrator".

<p align="center">
<img src="https://i.imgur.com/lOf0OGk.png" height="80%" width="80%" alt="img"/>
</p>

Double-click "PHP Manager".

<p align="center">
<img src="https://i.imgur.com/o3D5FBm.png" height="80%" width="80%" alt="img"/>
</p>

Click "Register new PHP version" and click the three dots (...). Double-click "PHP"

<p align="center">
<img src="https://i.imgur.com/jS0jGP6.png" height="80%" width="80%" alt="img"/>
</p>

Select "php-cgi", and click "Open" > "Ok".

<p align="center">
<img src="https://i.imgur.com/s7e5CeS.png" height="80%" width="80%" alt="img"/>
</p>

Reload IIS Manager by clicking "vm-osticket" in the left pane, and click "Restart" in the right pane.

<p align="center">
<img src="https://i.imgur.com/khxs2mx.png" height="80%" width="80%" alt="img"/>
</p>

Let's install osTicket. Go back to the osTicket Installation Files web page and download "osTicket-v1.15.8.zip".

Open two File Explorer windows For the first window, double-click "This PC" > "Windows C:" > "inetpub" > "wwwroot".

For the second window, click "Downloads", double-click "osTicket-v1.15.8", and drag the "upload" folder to the "wwwroot" folder in the first File Explorer window.

<p align="center">
<img src="https://i.imgur.com/YEM4gWa.png" height="80%" width="80%" alt="img"/>
</p>

Let's rename the "upload" folder to "osTicket". 

Right-click the "upload" folder and click "Rename".

<p align="center">
<img src="https://i.imgur.com/5OcDCzB.png" height="80%" width="80%" alt="img"/>
</p>

It has now been renamed "osTicket". Reload IIS like we did earlier.

<p align="center">
<img src="https://i.imgur.com/hGZjJPc.png" height="80%" width="80%" alt="img"/>
</p>

In IIS Manager, expand "Sites" > "Default Web Sites" and click "osTicket".

<p align="center">
<img src="https://i.imgur.com/G2Jbwjx.png" height="80%" width="80%" alt="img"/>
</p>

The osTicket installer web page will pop up.

<p align="center">
<img src="https://i.imgur.com/FWEQqm2.png" height="80%" width="80%" alt="img"/>
</p>

Go back to IIS Manager. In "osTicket", double-click "PHP Manager".

<p align="center">
<img src="https://i.imgur.com/xVcDM8E.png" height="80%" width="80%" alt="img"/>
</p>

Click "Enable or disable an extention".

<p align="center">
<img src="https://i.imgur.com/6aqTQCo.png" height="80%" width="80%" alt="img"/>
</p>

Click "php_imap.dll", and click "Enable". Do the same for "php_intl.dll" and "php_opcache.dll".

<p align="center">
<img src="https://i.imgur.com/HFYozQP.png" height="80%" width="80%" alt="img"/>
</p>

Refresh the osTicket Installer web page and make sure some of the recommended extentions are marked green, like the image above.

<p align="center">
<img src="https://i.imgur.com/MUcoVdV.png" height="80%" width="80%" alt="img"/>
</p>

Open File Explorer, click "This PC", double-click "Windows C:" > "inetpub" > "wwwroot" > "osTicket" > "include". Rename "ost-sampleconfig.php" to "ost-config.php"

<p align="center">
<img src="https://i.imgur.com/uJN26pK.png" height="80%" width="80%" alt="img"/>
</p>

Right-click "ost-config.php", and click "Properties".

<p align="center">
<img src="https://i.imgur.com/owJKXTl.png" height="80%" width="80%" alt="img"/>
</p>

Click "Security" > "Advanced" > "Disable inheritance" > "Remove all inherited permissions from this object".

<p align="center">
<img src="https://i.imgur.com/pb2scVQ.png" height="80%" width="80%" alt="img"/>
</p>

Click "Add" > "Select a principle", and type "Everyone" in the box. Click "Check Names" and click "Ok".

<p align="center">
<img src="https://i.imgur.com/WXR19cL.png" height="80%" width="80%" alt="img"/>
</p>

Check "Full control" and click "Ok". 

<p align="center">
<img src="https://i.imgur.com/15bPhpW.png" height="80%" width="80%" alt="img"/>
</p>

Click "Ok".

<p align="center">
<img src="https://i.imgur.com/kaLrzEi.png" height="80%" width="80%" alt="img"/>
</p>

Go back to osTict Installation Files web page and download "HeidiSQL_12.3.0.6589_Setup.exe.docx".

NOTE: "HeidiSQL_12.3.0.6589_Setup.exe.docx" allows us to connect to our SQL server.

Go to "Downloads" folder and double-click HeidiSQL_12.3.0.6589_Setup" to install it.

Select "I accept the agreement", and click "next" > "Next" > "Next" > "Next" > "Install" > "Finish" > "Skip". A new window will pop up.

<p align="center">
<img src="https://i.imgur.com/geYJqYI.png" height="80%" width="80%" alt="img"/>
</p>

We are going to create a new connection to the database in this window.

Click "New", type in your username and password (Password1), and click "Open". This is the password we used when we created the "MySQL Server".

<p align="center">
<img src="https://i.imgur.com/bFoGNDs.png" height="80%" width="80%" alt="img"/>
</p>

We are now connected to MySQL Server.

<p align="center">
<img src="https://i.imgur.com/mOqxUUC.png" height="80%" width="80%" alt="img"/>
</p>

Let's go ahead and create a new database

Right-click "Unamed" and click "Create new" > "Database" 

<p align="center">
<img src="https://i.imgur.com/09oU3t5.png" height="80%" width="80%" alt="img"/>
</p>

Name your database "osTicket" and click "Ok".

<p align="center">
<img src="https://i.imgur.com/Zk5zNaq.png" height="80%" width="80%" alt="img"/>
</p>

As you can see from the image above, the osTicket database has now been created. Minimize the window

<p align="center">
<img src="https://i.imgur.com/e7Ilkyv.png" height="80%" width="80%" alt="img"/>
</p>

Go back to the osTicket Installation web page and click "Continue". Fill in the information, and make sure you use "root" as your username and "Password1" as your password. Click "Install".

<p align="center">
<img src="https://i.imgur.com/I0c3qWC.png" height="80%" width="80%" alt="img"/>
</p>

osTicket has now been installed.

<p align="center">
<img src="https://i.imgur.com/tdj0ZE1.png" height="80%" width="80%" alt="img"/>
</p>

Let's do some clean up. Open File Explorer, click "This PC", double-click "Windows C: > "inetpub" > "wwwroot" > "osTicket", right-click the "setup" folder, and click "delete".

<p align="center">
<img src="https://i.imgur.com/0VW416o.png" height="80%" width="80%" alt="img"/>
</p>

We will now set the permissions for the "ost-config.php" file to "Read only"

Open File Explorer, click "This PC" and double-click "Windows C: > "inetpub" > "wwwroot" > "osTicket" > "include". Right-click "ost-config.php", and click "Properties".

<p align="center">
<img src="https://i.imgur.com/Lap4wOb.png" height="80%" width="80%" alt="img"/>
</p>

Click "Security" > "Advanced", and select Everyone. Click "Edit", uncheck "Full control, Modify, Write", and click "Ok".

<p align="center">
<img src="https://i.imgur.com/Lap4wOb.png" height="80%" width="80%" alt="img"/>
</p>

Click "Apply", and click "Ok".

<p align="center">
<img src="https://i.imgur.com/ZsRVbQD.png" height="80%" width="80%" alt="img"/>
</p>

Click "Ok"















