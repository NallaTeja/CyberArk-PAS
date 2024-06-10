I have changed the Server name to ADDC001 & rebooted the VM. 

Network Protocol IPv4 configuration

![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/06f2f551-2c19-49cf-90c1-b0bad4458c94)

# Phase 1: Install Domain controller services

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
![CORPDEVLAB](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/d111b848-3cfe-41a0-b972-9c0ddefa84e2)

# Phase 2: Install Certification Service 

Open Server Manager, Manage> Add Roles and features

![Add Roles and features](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/460078e0-b667-455e-8220-b960c8aa2352)

Click 3 times 'Next'. go to 'Server Roles' add 'Active directory certificate services'

![server role ADCS](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/a7296cd9-4aff-4042-95d9-fdf2150c2a3a)


Click 3 times 'Next'. Under Role Services select "Certification authority and certification Authority web enrollment". 

![role services](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/607a093a-dcc9-4c7b-ad63-be7bc172b5ed)

Click 3 times 'Next'. Under Confirmation, select 'install'.

![confirm installation](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/40496e23-7308-4dea-8cb4-41e37de8b931)

Go to server manager notification click on "Configure Active Directory Certificate services on the destination server "

![SM notification](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/8f4e28cc-f4d2-4241-bd2e-e830f7c9364a)

![Credentials](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/2e0f04eb-1ed5-4f52-874b-2d4bf6582310)

Role services, select CA & CA web enrollment

![role services2](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/f931298d-60e7-40b9-8408-71e9e0dde643)

Type of setup: `Enterprise CA`

![Enterprise CA](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/eee11cc7-ed93-4914-8579-119087a8996f)

CA type: Root CA

![Root CA](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/75a8c160-f083-4949-a92b-585fdf485ab9)

The type of the private key is create a new PK.

![Private Key](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/2a399092-3c38-4966-af2b-a04551b23005)

Specify the cryptographic options: Keylength= `2048` & hash algorithm certificate issued by `SHA256`

![cryptographic for CA](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/1f10ac32-7154-4f80-a66d-aabc7c73fae4)

CA Name

![CA Name](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/0f534db6-150c-4828-890c-4cbdae9fdde1)

Validity period 5 years

![Validity period](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/5166061e-96f5-4f76-8902-fea050b96974)

CA database locations

![CA database](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/40bbfee1-e0a6-4677-866e-327b1aa296e5)

Review the CA details and click on 'Configure'.

![Configure](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/90478237-4cc3-4503-acc1-058ca7a57656)

![Result](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/dc1c732d-7fc7-4b86-943a-4183df33765b)

# Phase 3: Verify certification website and internet access

Open 'Internet Information services Manager'

![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/eee2f63c-50a7-4c75-9c95-9205501d408c)

Open the certsrv> browser

![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/e637ac9c-8f3e-49d3-a6ef-4e50a9f59f14)

ADCS browser

![ADCS browser](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/4776fadc-d812-4c18-aacc-20bdc7cae139)

Check the internet Access

![internet](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/7f4b5e8f-0343-4943-b6a9-ef1b07ef7aa7)

check the DNS servers `127.0.0.1`

![DNS servers](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/8599a4ea-4b04-4cfc-a70d-c7d1c4eec023)





