I have changed the Server name to ADDC001 & rebooted the VM. 

Network Protocol IPv4 configuration

![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/06f2f551-2c19-49cf-90c1-b0bad4458c94)

Open Server Manager, Manage> Add Roles and features

![Add Roles and features](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/460078e0-b667-455e-8220-b960c8aa2352)

Click 3 times 'Next'. go to 'Server Roles' add DNS Services, Web servers (IIS), Active Directory Domain Services & Federation services

![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/69ef64b4-4673-4582-8589-e77b38ae5e4e)

Click 7 times 'Next'. go to 'Confirmation'. Click 'Install'

![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/e63ce619-df91-4f93-8998-db95416dbd03)

Go to server manager notification click on "Promote this server to a domain Controller"
![Promote domain Controller](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/06b9c671-3217-4952-bede-f7456dc00153)

Select "Add a new forest" and give root domain name: `corp.devlab.com`

![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/27b316ab-c32a-4986-8859-3f6583fcabfc)

Set the Directory Services restore Mode (DSRM) password (pwd: `Tej@143`)

![DSRM](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/634e1136-6c05-42f4-8808-0eb21df065ba)

DNS Options, Click 'Next'.

![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/e99ceb55-d4b0-4d52-b6ae-afbd38afb5f4)

Set NetBIOS domain name: `CORPDEVLAB`

![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/fac7ce5f-38ec-4b94-be44-2e14c5f6729a)

Paths, Click 'Next'.

![Paths](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/b8dfac2a-3c53-4a81-9be8-4d715bd09868)

Review Options, Click 'Next'.

![Review Options](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/7c37fbd2-f765-45f5-a702-53f45f209450)

Prerequisites check, There are some warning messages showing, but we can safely ignore them for lab environment. Click 'Install'.

![Prerequisites check](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/6b995a99-a8cd-42df-8af0-9feb9d8d48bb)
![Signed out](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/4670b1af-9823-463b-85db-45e9ab855c3e)


