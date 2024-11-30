<h1>Overview : Lab 12 Printer Setup on Server 2022, NTFS Permissions</h1>

This repository documents my home lab focused on **Printer Setup on Server 2022** and **NTFS Permissions** using **VirtualBox**. The lab explores configuring printers on a Windows Server 2022 machine, setting up shared printers for network use, and managing NTFS file permissions to control access to shared resources. 

 <h1>Objectives</h1>

- **Printer Setup on Server 2022:** Learn how to install and configure printers on Windows Server 2022 and share them with network users.
- **NTFS Permissions:** Understand how to set and manage NTFS file permissions for controlling access to shared resources on the server.
- **Printer Sharing:** Configure printer sharing and permissions to ensure that only authorized users can access and print to the shared printers.

<h1> Documentation</h1>

In this home lab, we will focus on how to install and configure network printers, as well as explore file and printer security through NTFS permissions.

Let's open up **Server Manager** on our **Windows Server 2022** VM. Select **Manage** → **Add Roles and Features**.



1. <p align="center">
   <img src="https://i.imgur.com/WQZTWKw.png" height="80%" width="80%" alt="Disk Sanitization Steps 1"/>
   <br />
   <br />
</p>

Select Next until you reach Select Server Roles, then click on Print and Document Services. Select Add Features, then click Next.


2. <p align="center">
   <img src="https://i.imgur.com/gQd6b1I.png" height="80%" width="80%" alt="Disk Sanitization Steps 2"/>
   <br />
   <br />
</p>

For Role Services, it shows the different service installations, such as options for using Internet Printing Services or UNIX-based computers for LPD printing. In this case, we will focus on Print Server. Select Next, then click Install.

3. <p align="center">
   <img src="https://i.imgur.com/TDU9KzX.png" height="80%" width="80%" alt="Disk Sanitization Steps 3"/>
   <br />
   <br />
</p>



4. <p align="center">
   <img src="https://i.imgur.com/7WpZ5B1.png" height="80%" width="80%" alt="Disk Sanitization Steps 4"/>
   <br />
   <br />
</p>

Once the installation is complete, we can verify that the printing services are installed by reopening Server Manager. We should notice that Print Services appears on the left side.

5. <p align="center">
   <img src="https://i.imgur.com/fpPYPFL.png" height="80%" width="80%" alt="Disk Sanitization Steps 5"/>
   <br />
   <br />
</p>

Lets open up “Tools” → “Print Management”

6. <p align="center">
   <img src="https://i.imgur.com/Io8lfNl.png" height="80%" width="80%" alt="Disk Sanitization Steps 6"/>
   <br />
   <br />
</p>

In Print Management, we can see the different drivers, printers, ports, and the server "Server2022 (local)" for our Desktop2 computer.

7. <p align="center">
   <img src="https://i.imgur.com/hoCsKZi.png" height="80%" width="80%" alt="Disk Sanitization Steps 7"/>
   <br />
   <br />
</p>

Now lets create a printer, right-click then “Add Printer..”.

8. <p align="center">
   <img src="https://i.imgur.com/FhUnte4.png" height="80%" width="80%" alt="Disk Sanitization Steps 8"/>
   <br />
   <br />
</p>

Select “Add a new printer using an existing port:”

9. <p align="center">
   <img src="https://i.imgur.com/eVun6T7.png" height="80%" width="80%" alt="Disk Sanitization Steps 9"/>
   <br />
   <br />
</p>

 Then select “Install a new driver”.

10. <p align="center">
    <img src="https://i.imgur.com/2Pj6cLW.png" height="80%" width="80%" alt="Disk Sanitization Steps 10"/>
    <br />
    <br />
</p>

Here, we will select any driver. I will select "Microsoft MS-XPS Class Driver 2", then click Next.

11. <p align="center">
    <img src="https://i.imgur.com/sHFlt3e.png" height="80%" width="80%" alt="Disk Sanitization Steps 11"/>
    <br />
    <br />
</p>

Make sure to uncheck "Share this printer," then click Next and finally select Finish.

12. <p align="center">
    <img src="https://i.imgur.com/xNCzyAz.png" height="80%" width="80%" alt="Disk Sanitization Steps 12"/>
    <br />
    <br />
</p>



13. <p align="center">
    <img src="https://i.imgur.com/6ZVsb0L.png" height="80%" width="80%" alt="Disk Sanitization Steps 13"/>
    <br />
    <br />
</p>

Now, when we look into the properties of our new printer, we can see the different settings we can configure. For example, if we wanted to list the printer in Active Directory for another user to install, we could do that in the Sharing tab. We will enable this in just a bit.

14. <p align="center">
    <img src="https://i.imgur.com/K5Fhp82.png" height="80%" width="80%" alt="Disk Sanitization Steps 14"/>
    <br />
    <br />
</p>

We can also see the different ports available for the printer in the Ports tab.

15. <p align="center">
    <img src="https://i.imgur.com/lM77ZRE.png" height="80%" width="80%" alt="Disk Sanitization Steps 15"/>
    <br />
    <br />
</p>

Lets look into the “Security” tab in the properties of our printer. Here we want to remove the users “EVERYONE” and limit certain users to have access to our printer. Click on “Advance”

16. <p align="center">
    <img src="https://i.imgur.com/Xamq2T0.png" height="80%" width="80%" alt="Disk Sanitization Steps 16"/>
    <br />
    <br />
</p>

Select "Everyone", then click Remove.

17. <p align="center">
    <img src="https://i.imgur.com/1hH0eRv.png" height="80%" width="80%" alt="Disk Sanitization Steps 17"/>
    <br />
    <br />
</p>

Now, let's add HR to the permissions by clicking on Add, then Select a principal → type in "HR", and select OK. For basic permissions, we will only allow HR to Print, then click OK → Apply, and finally OK.

18. <p align="center">
    <img src="https://i.imgur.com/MyWbFL9.png" height="80%" width="80%" alt="Disk Sanitization Steps 18"/>
    <br />
    <br />
</p>

Now, we can see in the Security tab that HR is a member of this security group, and it shows the permissions HR has for this printer. This printer should also automatically show up for anyone in the HR group.

19. <p align="center">
    <img src="https://i.imgur.com/dm3Ak0s.png" height="80%" width="80%" alt="Disk Sanitization Steps 19"/>
    <br />
    <br />
</p>

Now, let's list this printer in the directory. Click on the Sharing tab, then enable "Share this printer" and "List in the directory", and click Apply.

20. <p align="center">
    <img src="https://i.imgur.com/XoOV1UZ.png" height="80%" width="80%" alt="Disk Sanitization Steps 20"/>
    <br />
    <br />
</p>

Let's verify that by going to Active Directory Users and Computers, right-clicking on the domain SimoTech.com, selecting "Find", then selecting the dropdown under "Find:" and choosing "Printers".

21. <p align="center">
    <img src="https://i.imgur.com/0MTOYbX.png" height="80%" width="80%" alt="Disk Sanitization Steps 21"/>
    <br />
    <br />
</p>



22. <p align="center">
    <img src="https://i.imgur.com/SzROBgh.png" height="80%" width="80%" alt="Disk Sanitization Steps 22"/>
    <br />
    <br />
</p>

Click on "Find Now", and our printer should show up in the directory.

23. <p align="center">
    <img src="https://i.imgur.com/lK0aF2Y.png" height="80%" width="80%" alt="Disk Sanitization Steps 23"/>
    <br />
    <br />
</p>

Now that the printer is in the directory, let's log into Desktop2 as Bob and install the printer from the directory. Open up Control Panel on Desktop2 → View Devices and Printers → Add Printer. The scan will search for the printer in the directory. Select Next, then Finish.

24. <p align="center">
    <img src="https://i.imgur.com/57wqkqt.png" height="80%" width="80%" alt="Disk Sanitization Steps 24"/>
    <br />
    <br />
</p>


25. <p align="center">
    <img src="https://i.imgur.com/H1IpjR7.png" height="80%" width="80%" alt="Disk Sanitization Steps 25"/>
    <br />
    <br />
</p>

Congratulations! We have successfully added a printer on our Server 2022 domain and explored file and printer security through NTFS permissions for effective access control.

 👉 [Next Lab 13 : Understanding Tickets Using Spiceworks](https://github.com/Simokid/Understanding-Tickets-Using-Spiceworks/blob/main/README.md)
