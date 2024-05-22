Disable all the protocols. only enable the TCP/IPv4 protocol version
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/d56b2f67-b5af-460b-9ef7-5f0f6dd0ead0)
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/ed380242-cb44-45d8-91ed-927174db68bf)

Install the .Net framework 4.8 or latest version. & Microsoft VS x64 & x86
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/625f54fd-bd6a-4f64-b2f1-a062eabad22c)

Go to Server file. Run the set up as administrator.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/e3e04327-83b6-4c59-96b4-e9a5c0e25527)

Setup program click next
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/38ef4c46-12f1-4964-ab42-93f6c592218b)

Accept the license agreement, click yes
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/34d22c97-6d22-497e-9344-f6d1eb05532c)

Give User information like Name and company
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/2b02815b-8ef5-4ff0-a477-e8a8461cdf9d)

Select vault mode as 'Standalone Vault Installation'
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/88a62b7b-578e-42c0-a1c4-1657766b3020)

Select folder where setup will install files.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/6380ecf5-a294-440a-9fd3-a7df802e79b7)

Choose folder for storing the safes.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/311e485e-3e4d-4a1f-bfa5-0f06c815c784)

Enter License .xml file path
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/911d334e-a874-4032-9ff4-d930b1f9ca13)

Enter Operator CD path.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/452b80f8-1648-407e-83b0-e581a1b691e3)

Configure remote control Agent i.e, PVWA server IP ~192.168.5.130~ and password ~Tej@143~.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/06a68fd5-0207-41c0-b5a7-139811d18c52)

Uncheck the ~"Distribute vaults"~. we are installing RabbitMQTM. 
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/120c55cd-a77b-4f72-beb9-c5616e29d813)

Vault server machine hardening
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/6d1723b4-cf65-4c8d-a2d6-d960a9e5aa53)

Select the program folder, click Next. The Digital Vault Machine Hardening starts after some time private ark database setup will intall .
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/fa92be0d-2391-400c-a469-24298085b9c9)
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/c0c8e580-071e-419a-bc5a-6f2816379dd0)
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/0fd1a15d-7d22-4292-a0f0-a5123d629981)

Set built-in Users Passwords. Master Account Password: P@ssw0rd123 Administrator Account Password: Secur1tyP@ss
Note:- Use complex passwords with a mixture of numeric and mixed case characters. By default, the password must contain at least one numeric character and 5 mixed case characters

![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/c2735ddb-8de1-4bbf-bbc0-f5975ed764d5)

After successful install the system will restart.

Now start the client set up installation as a adminsitrator.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/eb028733-e0a5-429e-b625-6e6ab57da02b)

Setup the privarteArk Client
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/8566d4fc-b3ad-4df4-bd3d-f23ee69b9480)

Accept the License Agreement
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/55759066-d74b-44fe-9b34-c3c746d54d1f)

Fill the user information
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/4e7c7679-d33f-40cb-a215-68ecc677827d)

Choose the setup intallation path of PrivateArk client
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/c2436314-7a57-4795-8bbf-436db62e34a5)

Select client setup type
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/2dfe98d8-e739-45da-adf0-ecc63d23149c)

Select the program folder
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/0102767f-1d35-45d6-abce-8a2b50ceccce)

Define the PrivateArk vault
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/a9044107-1202-42d0-9a7b-5c086d3424b8)

![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/cc501682-877a-4635-9352-82246071ff28)

Setup Complete.  click yes for restart.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/fdad2b1c-eced-4f16-bacb-e0c3f96ed604)

# Validation
1. Log into the privateArk client. Following safe will be created.
Notification Engine, System, VaultInternal
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/8f8d4232-1b22-4b99-8562-d3fa692e2d02)

2. Check the services are running

![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/8c6d6612-28c5-4d0f-92af-8a4e10b46e51)
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/d5658617-46e1-470b-9636-8a84e39fb708)











