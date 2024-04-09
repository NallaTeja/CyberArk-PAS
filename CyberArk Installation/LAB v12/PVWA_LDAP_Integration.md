Create PAM AD groups and users in OU
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/551fda40-e19c-4e9f-97d8-bac39ae41994)
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/522cad9c-ee08-4513-9caf-115d626365b6)
Note: While creating the users "User Logon Name" will be the network ID for authentication. 
Following error code fill be prompted if OU details are incorrect AD server.
ITATS528E Authentication failure for user <username> from station: <IP_Address> (code: -110)
ITALD002E Failed to perform LDAP operation.(reason connection failed to all hosts of "domain name" ldap directory 
ITATS527E User or Group "Network ID" has not been defined (Station: "IP_Address")

1.We are going to download CA certificate from Domain Controller server and import into vault server.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/eb9287b1-59b3-426a-b6b3-f63e2d89c6ba)
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/b584be2a-53e5-477a-9078-8f038580f2d8)
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/45302054-69f8-40f4-9900-fb64ecacd9e4)
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/52d99203-0364-43b0-bb41-e6ed8499e1c5)
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/0e24af56-2735-4c30-b4f8-634b4bd0bc3b)
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/3e9a7745-2d50-4f96-addc-a734b077ceec)
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/e329276d-9c1e-4a94-9d93-dff53eecc815)


2. Verify the certificate is installed in vault server.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/5394aa50-5ec7-4fee-806c-55f5abda906b)
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/0c087a83-9236-40a1-a18c-a3312410db8a)
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/70c6f91a-c518-4a39-b7c3-24b68c74285e)
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/59dad3ea-6a5c-44d3-9205-cd7bad48a71b)
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/b9af7af0-9528-4ec8-b767-508e51c92fae)
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/045d8a63-22ab-4dad-b4a3-20772e5aaed1)


3. Add DC host IP address into vault host file.
File path  ```C:\Windows\System32\drivers\etc```
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/c8b88c34-6176-444c-8645-75da3682e87f)
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/85a87bdb-ee74-457f-8aaa-044a9fed3724)

```
# Active Directory Domain controller Host IP address, FQDNS and DNS.
192.168.5.128 ADDC01.corp.devlab.com ADDC01
```
4. Log-In as Administrator in PVWA console. GO to **user provisioning** Select **LDAP Integration** Create **New Domain**
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/273d7d18-0028-4943-8ff2-e9ff2ef6be76)


5. Enter the Domain detail.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/5bcf626f-a891-411e-936a-1340792760c3)


6. Select the DC and continue. Note: Port 636 is Defined
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/5d6aa85b-de79-495b-aa11-90e80eac547d)
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/57b711f2-be5a-420e-95f8-8a8008fae7cf)

7. Define all the directorys mapping
Vault Admins
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/a5d95af6-eaa6-42c8-8957-2df0ab06804c)
Safe Managers
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/7e60994c-9432-4748-9d06-7c45e4ed53e5)
Auditors
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/78272ac1-5768-4c15-ac52-2e1fbe11646c)
Users
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/2cc7b045-9b2b-4cc6-8540-2d5d84d30139)

8. Save the summary 
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/af4f1851-b37d-48e8-ae36-acd0e482dee4)

9. Validate the LDAP. Login as a user with networkt ID "TN007".
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/4453968c-f2dc-4842-90f7-0314880588c1)
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/dfdc4c27-6e1e-4b17-ac4a-fed173135c72)


