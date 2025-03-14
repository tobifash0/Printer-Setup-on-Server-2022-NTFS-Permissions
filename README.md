# Overview : Lab 12 Printer Setup on Server 2022, NTFS Permissions
This repository documents my home lab focused on Printer Setup on Server 2022 and NTFS Permissions using VirtualBox. The lab explores configuring printers on a Windows Server 2022 machine, setting up shared printers for network use, and managing NTFS file permissions to control access to shared resources.

## Objectives

- Printer Setup on Server 2022: Learn how to install and configure printers on Windows Server 2022 and share them with network users.
- NTFS Permissions: Understand how to set and manage NTFS file permissions for controlling access to shared resources on the server.
- Printer Sharing: Configure printer sharing and permissions to ensure that only authorized users can access and print to the shared printers.

## Documentation
In this home lab, we will focus on how to install and configure network printers, as well as explore file and printer security through NTFS permissions.

Let's open up Server Manager on our Windows Server 2022 VM. Select Manage → Add Roles and Features.

<br> 

![image](https://github.com/user-attachments/assets/ae3552af-13a2-49ec-82ef-232db5e98126)

<br> 

1. Select Next until you reach Select Server Roles, then click on Print and Document Services. Select Add Features, then click Next.

<br> 

<img width="673" alt="Screenshot 2025-03-14 at 6 52 16 AM" src="https://github.com/user-attachments/assets/512c9ea3-2e1f-47e0-9109-e5345edec631" />

<br> 

2. For Role Services, it shows the different service installations, such as options for using Internet Printing Services or UNIX-based computers for LPD printing. In this case, we will focus on Print Server. Select Next, then click Install.

<br> 

<img width="679" alt="Screenshot 2025-03-14 at 6 53 31 AM" src="https://github.com/user-attachments/assets/35bd6e19-d0cd-403a-bc77-396612839434" />

<br> 

3. Once the installation is complete, we can verify that the printing services are installed by reopening Server Manager. We should notice that Print Services appears on the left side.

<br> 

![image](https://github.com/user-attachments/assets/730dc309-d5b6-4f2f-8a7b-b7b4b58956c6)

<br>

4. Lets open up “Tools” → “Print Management”

<br> 


![image](https://github.com/user-attachments/assets/5f1cfe6b-780f-4cdd-8b72-d6abf81e97b9)

<br>

5. In Print Management, we can see the different drivers, printers, ports, and the server "Server2022 (local)" for our Desktop2 computer.

<br>


![image](https://github.com/user-attachments/assets/d441d97e-06f5-4115-8cdd-641cb70682da)

<br>

6. Now lets create a printer, right-click then “Add Printer..”.

<br> 


![image](https://github.com/user-attachments/assets/f99c21e2-bf37-4f07-bc40-9fae21b1eab9)

<br>

7. Select “Add a new printer using an existing port:”

<br>

![image](https://github.com/user-attachments/assets/768ffdc4-a0fc-43c4-8d44-308f13f216b9)

<br> 
8. Then select “Install a new driver”.

<br>

![image](https://github.com/user-attachments/assets/00927368-945a-4131-97e4-0d2550ceb9e5)

<br> 

9. Here, we will select any driver. I will select "Microsoft MS-XPS Class Driver 2", then click Next.

<br>

![image](https://github.com/user-attachments/assets/1e4af155-526a-4af2-aa9d-ddda3b77aaec)

<br> 

10. Make sure to uncheck "Share this printer," then click Next and finally select Finish.

<br>


![image](https://github.com/user-attachments/assets/251e267f-a3d9-47c9-ae72-a3a43beb348d)

<br>

11. Now, when we look into the properties of our new printer, we can see the different settings we can configure. For example, if we wanted to list the printer in Active Directory for another user to install, we could do that in the Sharing tab. We will enable this in just a bit.

<br> 


![image](https://github.com/user-attachments/assets/92423c93-302f-4ad0-9209-118af4bde493)

<br> 

12. We can also see the different ports available for the printer in the Ports tab.

<br> 


![image](https://github.com/user-attachments/assets/f43b0dcf-aafc-4c46-94bc-25b3c9a28ab0)

<br> 


13. Lets look into the “Security” tab in the properties of our printer. Here we want to remove the users “EVERYONE” and limit certain users to have access to our printer. Click on “Advance”

<br> 

![Screenshot 2025-03-14 at 6 39 39 AM](https://github.com/user-attachments/assets/de640b40-3cac-430b-9f28-9c8486bb90fb)



<br> 


14. Select "Everyone", then click Remove.

<br>

![Screenshot 2025-03-14 at 6 40 25 AM](https://github.com/user-attachments/assets/78bc40a0-f608-4405-afbe-d7f4dc81dcef)

<br> 

15. Now, let's add HR to the permissions by clicking on Add, then Select a principal → type in "HR", and select OK. For basic permissions, we will only allow HR to Print, then click OK → Apply, and finally OK.

<br>

![Screenshot 2025-03-14 at 6 41 11 AM](https://github.com/user-attachments/assets/9137d4e9-a1f6-46a2-8414-c109a0a5a36b)

<br> 

16. Now, we can see in the Security tab that HR is a member of this security group, and it shows the permissions HR has for this printer. This printer should also automatically show up for anyone in the HR group.

<br> 

![Screenshot 2025-03-14 at 6 47 25 AM](https://github.com/user-attachments/assets/1cf2efea-0301-48ee-8af8-66414bb8734e)

<br> 

17. Now, let's list this printer in the directory. Click on the Sharing tab, then enable "Share this printer" and "List in the directory", and click Apply.

<br>

![image](https://github.com/user-attachments/assets/7250f0a3-f550-4cbf-8f4e-737a56c484d0)

<br> 

18. Let's verify that by going to Active Directory Users and Computers, right-clicking on the domain tobifash.com, selecting "Find", then selecting the dropdown under "Find:" and choosing "Printers".

<br> 

<img width="661" alt="Screenshot 2025-03-14 at 7 03 48 AM" src="https://github.com/user-attachments/assets/999e5c05-8bac-42af-9a77-1321bd29e9bc" />

<br> 

19. Click on "Find Now", and our printer should show up in the directory.

<br> 

![Screenshot 2025-03-14 at 6 49 18 AM](https://github.com/user-attachments/assets/07a2a417-d623-4e43-a589-4b2974f64cb2)


<br> 

20. Now that the printer is in the directory, let's log into Desktop2 as Bob and install the printer from the directory. Open up Control Panel on Desktop2 → View Devices and Printers → Add Printer. The scan will search for the printer in the directory. Select Next, then Finish.

<br> 

![image](https://github.com/user-attachments/assets/3ba83642-237f-4110-973d-ac09592a2dc8)

<br> 

![Screenshot 2025-03-14 at 6 51 00 AM](https://github.com/user-attachments/assets/3e1e8b50-e179-401d-b442-6254c2cbbc55)


<br>

21. Congratulations! We have successfully added a printer on our Server 2022 domain and explored file and printer security through NTFS permissions for effective access control.

👉 [Next Lab 13 : Understanding Tickets Using Spiceworks](https://github.com/tobifash0/Understanding-Tickets-Using-Spiceworks)
