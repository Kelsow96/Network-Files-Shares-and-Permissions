<h1> Network Files Shares and Permissions </h1>

<img src="https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/3fd62a28-23c1-4c08-b8dd-d4c5173b4110" width="400" />

<h2> What are Network Files Shares and Permissions? </h2>

Network File Shares and Permissions manage and control access to files and directories over a network. This includes setting up who can view, modify, or execute files, ensuring secure and organized collaboration, and managing resources.

<h2> Overview </h2>

In this lab, we'll create sample file shares on a Domain Controller with various permissions, such as read-only and read/write access for different user groups. We'll then test access to these shares using a normal user account, create a new security group for accountants, assign permissions to a specific folder for this group, and verify access rights for a user within that group.

<h2> Environments and Technologies Used: </h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Domain Controller (DC-1)
- Client Machine (Client-1)
- Active Directory
- Security Groups
- File Sharing
- Permissions Management

<h2> Operating Systems Used: </h2>

- Windows 10
- Windows Server 2022

<h2> List of Prerequisites: </h2>

- Azure Account/Subscription
- Virtual Machines ([DC-1 and Client-1](https://github.com/Kelsow96/-Implementing-Active-Directory-On-Premises-in-Azure)) from previous tutorial and have Client-1 joined to the domain.

<h2> High-Level Steps: </h2>

1. Create Sample Folders:
- Log into the Domain Controller (DC-1) as a domain admin.
- Create four folders on the C:\ drive: read-access, write-access, no-access, and accounting.

2. Set Permissions for "Domain Users" Group:
    - Grant "Read" permission to the read-access folder for the "Domain Users" group.
    - Grant "Read/Write" permission to the write-access folder for the "Domain Users" group.
    - Grant "Read/Write" permission to the no-access folder for the "Domain Admins" group.

3. Test Access as Normal User:
    - Log into a client machine (Client-1) as a normal user.
  - Attempt to access the shared folders (read-access, write-access, no-access) from the DC-1 server.

4. Create "ACCOUNTANTS" Security Group:
    - On DC-1, create a new security group named "ACCOUNTANTS" in Active Directory.

5. Assign Permissions to "ACCOUNTANTS" Group:
    - Grant "Read/Write" permission to the accounting folder for the "ACCOUNTANTS" group.

6. Test Access with "ACCOUNTANTS" Group:
    - Attempt to access the accounting folder from Client-1 as a user not initially part of the "ACCOUNTANTS" group (should fail).
    - Add the user to the "ACCOUNTANTS" group in Active Directory.
    - Retry accessing the accounting folder from Client-1 (should succeed).

<h2> Steps: </h2>

1. Create Sample Folders:
- Log into the Domain Controller (DC-1) as a domain admin.

![image](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/bdd9632e-0848-4882-a292-36c57a7d4199)

- Create four folders on the C:\ drive: read-access, write-access, no-access, and accounting.
    - Right-click the Windows Logo at the bottom left and select "File Explorer". Within the File Explorer window, select "This PC" from there double click "Windows (C:)". Now right-click and select "New Folder". Name it "read-access". Now we'll do the same steps to create the folders "write-access", "no-access" and "accounting".

![Capture](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/634365a0-665e-4e8a-b743-9f92da2ebbfe)
![Capture](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/430d6462-d58e-4190-9a24-82c5147d4114)
![Capture](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/a806f65a-21da-44fb-9a1c-fe752ad23a71)
![image](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/9d92b07f-ce9d-4bb5-94c0-a651cff5a625)
![Capture](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/b0004916-016e-4166-a2a6-551cf1166150)
<br>
</br>

2. Set Permissions for "Domain Users" Group:
- Grant "Read" permission to the read-access folder for the "Domain Users" group.
    - Right-click the read-access folder and select "Properties". Within the read-access Properties Window, navigate to the "Sharing" tab and select "Share". Within the Network access window, type "Domain Users" and select "Add". Once confirmed select "Share and then in the next window select "Done"

![Capture](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/2bda560c-1cbb-493f-ab81-8005f3505664)
![Capture](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/fafa05ea-a43a-44cd-9a62-01070b070efc)
![Capture](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/a23ed2af-dd06-4ff1-a569-09aaa59dccd6)
![Capture](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/64a44eae-1365-4d9c-92dd-7666eca3e6be)

- Grant "Read/Write" permission to the write-access folder for the "Domain Users" group.
    - Right-click the write-access folder and select "Properties". Within the write-access Properties Window, navigate to the "Sharing" tab and select "Share". Within the Network access window, type "Domain Users" and select "Add". Once added, select the drop-down menu underneath "Permission Level" and select "Read/Write". Once confirmed select "Share and then in the next window select "Done".

![Capture](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/04110bb1-cde7-4ba4-bda8-6701b48f7ef8)

  
- Grant "Read/Write" permission to the no-access folder for the "Domain Admins" group.
    - Right-click the no-access folder and select "Properties". Within the no-access Properties Window, navigate to the "Sharing" tab and select "Share". Within the Network access window, type "Domain Admins" and select "Add". Once added, select the drop-down menu underneath "Permission Level" and select "Read/Write". Once confirmed select "Share and then in the next window select "Done".

![image](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/853d6949-e188-493e-a28f-0767cc467ad7)
<br>
</br>

3. Test Access as Normal User:
- Log into a client machine (Client-1) as a normal user.
    - We'll use the user "sut.vaw" from when we created our random users in a previous lab to log into Client-1

![image](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/6713d75a-c989-435f-bf89-f2c8c4336884)
![image](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/aa9b3928-e714-4b83-89ff-3a82104cfe2a)
  
- Attempt to access the shared folders (read-access, write-access, no-access) from the DC-1 server.
    - In the search bar at the bottom, we'll type \\\\dc-1. We should see all the folders that we created from DC-1. We should be able to access the read-access folder, but we shouldn't be able to create any new documents because we don't have permissions to do so. We should be able to access and create new documents within the write-access folder because we have permission to do so. If we try to access the no-access folder, we should fail.
 
![image](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/601e910e-b5a1-49e1-b15a-ada22a045340)
![image](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/d65de10e-2cba-41d7-aef4-cfb4e2899b83)
![image](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/c6849cf7-762d-4a15-bb38-6969dc4fe47d)
![image](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/bab7f459-0c66-4857-85d3-b2ed724d03f2)
![image](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/8e0fce5c-7cfb-48e3-982c-e45cf37e0592)
<br>
</br>

4. Create "ACCOUNTANTS" Security Group:
- On DC-1, create a new security group named "ACCOUNTANTS" in Active Directory.
    - Within ADUC right-click mydomain.com, navigate to "New and select "Group". Type "ACCOUNTANTS" within the Group Name text box. Select "OK"

![Capture](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/738cfcbd-b404-400d-8989-9bb36f0bd3e2)
![image](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/645d39d6-95b0-4a79-8378-c53caf245d2b)
![Capture](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/4b06c2f1-fafd-47ba-aa3a-fc78fc3e14ca)
<br>
</br>

5. Assign Permissions to "ACCOUNTANTS" Group:
- Grant "Read/Write" permission to the accounting folder for the "ACCOUNTANTS" group.
    - Navigate back to the C: drive, Right-click the accounting folder and select "Properties". Within the accounting Properties Window, navigate to the "Sharing" tab and select "Share". Within the Network access window, type "ACCOUNTANTS" and select "Add". Once added, select the drop-down menu underneath "Permission Level" and select "Read/Write". Once confirmed select "Share and then in the next window select "Done".

![Capture](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/8c7387ea-0d4e-441b-9eb6-96b141cfc51c)
<br>
</br>

6. Test Access with "ACCOUNTANTS" Group:
- Attempt to access the accounting folder from Client-1 as a user not initially part of the "ACCOUNTANTS" group (should fail).
    - Back in Client navigate to \\\\dc-1. We should now see the accounting folder. When we try to access it, it fails because we don't have permission.
    
![image](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/68de2d1e-93d9-42bc-919e-991e51d222ee)
![image](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/65d43999-24db-44f4-a4fd-22b15b0416f2)

- Add the user to the "ACCOUNTANTS" group in Active Directory.
    - In ADUC within DC-1, right-click the "ACCOUNTANTS" Security Group and select "Properties". Within the ACCOUNTANTS Properties Window, navigate to "Members" and select "ADD". Within the text box, we'll type our user "sut.vaw". Select "OK" and then "Apply" in the ACCOUNTANTS Properties Window.

![Capture](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/b5c94cda-677d-4e07-a6f0-1d4050144252)
![Capture](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/e87b7228-db1b-44d4-aa9f-7e69c408fe58)
![image](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/6a5e1761-f49d-4238-ace7-7d66b08e7513)
![Capture](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/4699f2e5-df4c-40ac-9a15-835e7d9d6bb5)

- Retry accessing the accounting folder from Client-1 (should succeed).
    - We will need to log out of Client-1 with our user and log back in as them to get the new permissions and groups assigned to them before we can access the folder. Once logged back in navigate to \\\\dc-1 and we should be able to access the "accounting" folder. We should also be able to create documents within the folder. This is because we added the user to the ACCOUNTANTS security group which is the only group able to access the accounting folder since we gave them permission to do so.

![image](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/437988a5-1067-47f6-a2ea-f5ca34fa6420)
![image](https://github.com/Kelsow96/Network-Files-Shares-and-Permissions/assets/169297569/09a5b4d4-c98d-4141-8046-74d6e80173ff)
<br>
</br>

<h2> Summary </h2>

In conclusion, we successfully created and configured sample folders with specific permissions on the Domain Controller (DC-1). We established the "read-access", "write-access", "no-access", and "accounting" folders and set appropriate permissions for the "Domain Users" and "Domain Admins" groups. We tested access permissions using a normal user account on a client machine (Client-1), verifying the correct read/write capabilities. Additionally, we created an "ACCOUNTANTS" security group in Active Directory, assigned it the necessary permissions for the "accounting" folder, and validated access by adding a user to the group and confirming their ability to interact with the folder as intended. This process ensures proper folder access control and security management within the domain.
