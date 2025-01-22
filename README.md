# Active-Directory-RMIT-Cybersecurity-Project
One of my Blue teaming labs from my [RMIT Cybersecurity Project](https://github.com/Kazu010101/RMIT-Cybersecurity-Project/blob/main/README.md)

## Objective

- Add a Domain Controller
- Promote the Windows Server to a Domain Controller
- Add a Windows 10 VM to the Domain


## Lab Setup

- Windows 10 Pro VM Installed
- Windows Server 2022 VM Installed
- Network Setting of both Windows Server and Windows 10 is 'internal'
- Change the Windows Server name by opening up the server manager Dashboard > Local Server > click the computer name > click Change > Input the name > click OK > Restart the Server
  
![ad1](https://github.com/user-attachments/assets/661c600c-ef0e-4214-94f5-6ff4915db4bb)

- Once restarted, the name change takes effect.

![ad2](https://github.com/user-attachments/assets/7f9502de-0b82-4a62-904d-d00bf7e89cf1)

- After the restart, configure the IP addressing of the server to:
- IP: 192.168.1.254 /24
- DGW: 192.168.1.1
- DNS: 192.168.1.254

This can be done by opening up the server manager Dashboard > Local Server > click the "IPv4 address assigned by DHCP, IPv6 enabled" > double click 'Ethernet'  > click Properties > double click "Internet Protocol Version 4 (TCP/IPv4)" > tick the "Use the following IP address" > Fill in the field as configured > click OK

![ad3](https://github.com/user-attachments/assets/4e02eb7c-239e-4247-b1c0-253ff85a2abe)

- Verify the IP addressing from the command prompt:

![ad4](https://github.com/user-attachments/assets/d7b24d26-051b-497a-a464-72f644d602ee)

## Add a Domain Controller 

We start by installing Active Directory Domain services (ADDS).
- Step 1: Open Server Manager > Roles Summary > Add roles and features > Click Next 
- Step 2: On the "Before you begin" screen, click Next
- Step 3: Choose Role-based or Feature-based installation > click Next 
- Step 4: Select the destination server on which the role will be installed "(Ensure the IP address displayed is that of the selected server)" > click Next

![ad5](https://github.com/user-attachments/assets/1d11c37d-742e-4a30-bc53-943a1ea2dba2)

- Step 5: Tick the roles of Active Directory Domain Services > click Next
- Step 6: The basic features required for ADDS are selected by default > click Add Features
- Step 7: On Select Features page > click Next
- Step 8: On ADDS page > click Next
  
![ad6](https://github.com/user-attachments/assets/71a2dd15-a91f-4887-a033-e4fa84a91799)

- Step 9: Confirm the installation selections > click Install
- Step 10: After the installation finish, close the window and restart the computer.
  
![ad7](https://github.com/user-attachments/assets/2ab75f2c-f8b7-4126-8101-724514724f52)

## Promote the Windows Server to a Domain Controller

*Note: The following actions can be performed only if the user belongs to the Domain Admins group.*

- Step 11: Click the notification flag next to the Manage menu > Select "Promote this server to a domain controller"
- Step 12: On the Deployment configuration page, tick the option "Add a new forest" > fill in the domain name > click Next
- Step 13: Provide a unique password for the Directory Services Restore Mode "(DSRM helps gain access to an environment if all domain administrator accounts lose access or in case of DC failure)" > click Next
- Step 14: On DNS Option, click Next
  
![ad8](https://github.com/user-attachments/assets/07130750-65e7-411e-b307-a44a85178923)

- Step 15: After the Netbios name appears > click Next
- Step 16: Confirm the location for ADDS database files, log files and SYSVOL > click Next
- Step 17: Review the selections > click Next
- Step 18: Click Install and the system will be rebooted after replication has taken place.
  
![ad9](https://github.com/user-attachments/assets/21784e8a-8fa3-4317-8121-99ce5ec1b225)

After system restart, ADDC is installed which can be noticed from the login page of the account XYZCOMPANY\Administrator. We can verify the health of the new domain controller by running dcdiag /v from the command line.

![ad11](https://github.com/user-attachments/assets/22f303fc-843b-4b72-b47f-c15523779810)

## Add a Windows 10 Pro VM to the Domain

