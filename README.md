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




## Result

