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

- Enable Internet Information Services (IIS)
- Instal Web Platform Installer
- Install MySQL and set a Username and Password
- Install C++ Redistributable
- Configure Permissions and Install osTicket

<h2>Installation Steps</h2>

<p>
<img src="https://imgur.com/YHNlQDW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
This tutorial begins assuming you have a Microsoft Azure subscription. If not head to <a href="https://azure.microsoft.com/en-us/pricing/?ef_id=_k_Cj0KCQjw2ou2BhCCARIsANAwM2EU4uXax4Eaa7Ic5UN6DCUf05-caFCKE7RS9Ur1nSbbOUBDKAhS7okaAr-AEALw_wcB_k_&OCID=AIDcmm5edswduu_SEM__k_Cj0KCQjw2ou2BhCCARIsANAwM2EU4uXax4Eaa7Ic5UN6DCUf05-caFCKE7RS9Ur1nSbbOUBDKAhS7okaAr-AEALw_wcB_k_&gad_source=1&gclid=Cj0KCQjw2ou2BhCCARIsANAwM2EU4uXax4Eaa7Ic5UN6DCUf05-caFCKE7RS9Ur1nSbbOUBDKAhS7okaAr-AEALw_wcB">this link</a> and set up a free account using the circle green "try for free" button
</p>
<br />

<p>
<img src="https://imgur.com/qsrF2RC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, we will set up our virtual machine or VM using the Microsoft Azure portal. Essentially a VM is a virtual computer that acts like a real computer but is completely run in another computer's operating system. For security purposes, we will use this instead of our device. First in the search bar at the top of your screen, type Resource Group and name it "osTicket" It is good practice to make resource groups in Azure for management. Next, create a VM with at least 2-4 vCPUs or virtual CPUs and set the image to Windows 10 as that's the operating system we will use today. If you get confused  copy the settings I have in the image above
</p>
<br />

<p>
<img src="https://imgur.com/Pl27uHQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now, we need a way to access our newly created virtual machine. On a Windows computer, head to the search bar and look for Remote Desktop Connection, and enter your public IPv4 address. For Mac Users go to the app store and download "Microsoft Remote Desktop" It functions about the same as RDC just with slightly different features
</p>
<br />
<p>
<img src="https://imgur.com/NiJtewn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After connecting to our VM we have to enable Internet Information Services or IIS, this means our virtual machine can exchange web content with users, host static websites, etc. Head to the Control Panel then select "Programs" and then "Programs and Features" Now look through the list and check the "Internet Information Services" box
</p>
<p>
<img src="https://imgur.com/nZLLrlF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Once we've enabled IIS, we can start downloading everything we need to get osTicket up and running properly <a href="https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6"> Here is a Link </a> to all of the material. Start with the Microsoft Web Platform Installer 
</p>
<p>
<img src="https://imgur.com/65Z1vq8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
We're now going to download MySQL and the x86 version of PHP I installed the version seen in the Google Drive (7.3.8) on my first attempt of this lab on my Mac but after redoing it on a Windows PC i had some error codes, changing to an older version of PHP as shown here may help
</p>
<p>
<img src="https://imgur.com/bShEjFw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Finally, download osTicket. Then extract and copy the "upload" folder into c:\inetpub\wwwroot. Lastly rename the folder to osTicket  
</p>

<p>
Now below i will post screenshots of the final steps. Here we are just enabling and assigning permissions and opening our web server. Starting with your IIS manager go to Sites > Default > osTicket Then double click on PHP manager and select "disable or enable an extension", enable "php_intl.dll" & "php_opcache.dll" then go back to the default website and reset the web server. Pressing Browse *80 will open the osTicket Webserver. Go into your file explorer and follow this path. c:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php rename the file to c:\inetpub\wwwroot\osTicket\include\ost-config.php and then assign permissions to ost-config.php Disable inheritance->Removeall New Permissions->Everyone->all
</p>
<p>
<img src="https://imgur.com/N5kMZi2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://imgur.com/zmGRQm2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://imgur.com/jsDwP2s.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<h1>We've now finished installing osTicket! Now if everything was done correctly, you can continue to set up osticket to your liking through the browser. </h1>

<p>to clean up and try this lab over again, you follow these steps Clean up Delete: C:\inetpub\wwwroot\osTicket\setup Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php Login to the osTicket Admin Panel (http://localhost/osTicket/scp/login.php). Its recommended to keep passwords for everything consistent but its good practice to sign up with everything as if you were doing it in real life. </p>
