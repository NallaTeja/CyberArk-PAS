In order install HA Cluster we need 3 servers
These are the server Names SanDrive01, NodeA, NodeB.
Lets start with enabling 'Remote Desktop' from Server Manager -> Local Server. Doble click 'Disabled' option

![image](https://github.com/user-attachments/assets/815e00e2-e4ef-44c4-9e2a-d903d6434d07)

Under system properties goto Remote tab. Select 'Allow remote connections to this computer'. Uncheck 'Allow connections only from computers running RD with NLA'. Click 'Apply' and 'Ok'
![image](https://github.com/user-attachments/assets/5ffc68a6-fdfd-44e0-a236-6e248e7c1cf0)
Do the same steps for servers NodeA and NodeB

Set IP address, Go to 'Ethernet0' in Server manager. Double click 'Ethernet0' Go to IPv4 properties. 
Define IP address: 192.168.5.141
Subnet mask: 255.255.255.0
![SanDrive01 IP address](https://github.com/user-attachments/assets/47c1f3da-8e97-495b-95b1-bdd44ed13f27)
