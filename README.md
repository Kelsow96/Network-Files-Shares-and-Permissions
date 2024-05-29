<h1> Network Files Shares and Permissions </h1>

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
