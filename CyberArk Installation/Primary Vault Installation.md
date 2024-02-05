# CyberArk Vault Installation Documentation v12.0 Guide
---
[Installation Guide](https://docs.cyberark.com/pam-self-hosted/12.0/en/Content/PASIMP/Install-the-CyberArk-Vault-Normal-Installation.htm?tocpath=Installation%7CInstalling%20the%20PAS%C2%A0Solution%7CManual%20Installation%7CEnterprise%20Password%20Vault%7CInstall%20the%20CyberArk%20Vault%7CInstall%20the%20CyberArk%20Vault%20Server%7C_____1)

---

Run the **setup** as an `Administrator`

![image](https://github.com/NallaTeja/MOP-PAS/assets/145950340/88496c81-3095-4bbb-a8d8-a4accff5e750)

Click `Next`

![image](https://github.com/NallaTeja/MOP-PAS/assets/145950340/3696476b-5074-425b-a7f1-ab511d2ea194)

Select `Yes`

![image](https://github.com/NallaTeja/MOP-PAS/assets/145950340/c71e6c32-b3fa-4e59-8562-1f6169b5d369)

Enter the User Name and Company Name. 
Click `Next`

![image](https://github.com/NallaTeja/MOP-PAS/assets/145950340/bf302caf-4099-43bb-963c-8e5250e25a10)

Select **Standalone Vault Installation**

![image](https://github.com/NallaTeja/MOP-PAS/assets/145950340/1ec290ae-6e58-49f2-99ce-8b1f8e31049d)

Keep Default **PrivateArk** file location. Click `Next`

![image](https://github.com/NallaTeja/MOP-PAS/assets/145950340/d7d33ff4-8d51-464d-9c01-8cebed057797)

Keep Default **Safe** file location. Click `Next`

![image](https://github.com/NallaTeja/MOP-PAS/assets/145950340/3bdcd48d-0ed7-45e0-8e8f-42b344c9cf94)

Browse to the **License** folder and Click `Next`

![image](https://github.com/NallaTeja/MOP-PAS/assets/145950340/c57d25b1-7566-4272-8da3-eb2dd05e3aab)

Browse to the **Operator CD** folder and Click `Next`

![image](https://github.com/NallaTeja/MOP-PAS/assets/145950340/252bca1d-9c20-4dc1-8c89-daebdf4e9ff4)

You can `skip` it or Configure the **Remote Control Agent** (Enter PVWA IP and Password). Click `Next`

![image](https://github.com/NallaTeja/MOP-PAS/assets/145950340/e70d7501-59fc-4070-89f0-1b15ec268225)

Click `Next` **Distributed Vaults for PSM**

![image](https://github.com/NallaTeja/MOP-PAS/assets/145950340/0968c6a7-b4f7-4345-a397-9f4fedba34d8)

Click `Next` **Vault Server Machine Hardening** Starts

![image](https://github.com/NallaTeja/MOP-PAS/assets/145950340/2b710e57-96e4-4732-a420-0d435eef8ccb)

**Select Program Folder** and Click `Next`

![image](https://github.com/NallaTeja/MOP-PAS/assets/145950340/72712d6b-9eb4-4478-b9d9-45d31cc1f912)

Set up Master and Administrator Account. Click Next

Master Account Password: **P@ssw0rd123**
Administrator Account Password: **Secur1tyP@ss**

```
Note:- Use complex passwords with a mixture of numeric and mixed case characters. By default, the password must contain at least one numeric character and 5 mixed case characters
```

![image](https://github.com/NallaTeja/MOP-PAS/assets/145950340/6a32eea2-74fc-47b9-b865-c8fc1d23fc9a)

---
### **CAVaultManager database**
```plaintext
04/02/2024 16:52:37 ITADB399I Using encryption algorithms: Advanced Encryption Standard (AES), 128 bit, RSA (2048 bit), SHA2-512 (Protocol Integrity), SHA2-512 (Files Integrity).
04/02/2024 16:52:38 ITADM114I Successfully connected to Database, Database id 0.
04/02/2024 16:52:41 CAVLT005I Vault database schema created.
04/02/2024 16:52:41 ITAQS031I Object cache is loaded.
04/02/2024 16:52:41 CAVLT007I Vault initial data created.
04/02/2024 16:52:41 Entered Method CADALHardenVaultDBUsers
04/02/2024 16:52:41 Before Creating MySQL Replication Users for '' and localhost
04/02/2024 16:52:41 Enter Method AddPrivilegesToReplicationUser 'ReplicationUser'@'%'
04/02/2024 16:52:41 After adding privileges to replication use
04/02/2024 16:52:41 Enter Method AddPrivilegesToReplicationUser 'ReplicationUser'@'127.0.0.1'
04/02/2024 16:52:41 After adding privileges to replication use
04/02/2024 16:52:41 After Creating MySQL Replication Users
04/02/2024 16:52:41 CAVLT051I Vault database access users created successfully.
04/02/2024 16:52:41 CAVLT013I Vault database creation completed successfully.
04/02/2024 16:58:21 ITADB399I Using encryption algorithms: Advanced Encryption Standard (AES), 128 bit, RSA (2048 bit), SHA2-512 (Protocol Integrity), SHA2-512 (Files Integrity).
04/02/2024 16:58:22 ITADM114I Successfully connected to Database, Database id 0.
04/02/2024 16:58:22 Entering Secure DB Procedure
04/02/2024 16:58:22 Entering Check Vault DB Status
04/02/2024 16:58:22 CA_VAULT database already created
04/02/2024 16:58:22 CAVLT132E Password for user Administrator is invalid. Reason: ITAPW001E Password is too similar to the User name.
04/02/202

Vault server file has been successfuly installed.

Install Client Server

Run the setup as a Administrator.
![image](https://github.com/NallaTeja/MOP-PAS/assets/145950340/f1842c25-e75f-4925-ac5c-ac3ddab62e21)

Click `Next`.
![image](https://github.com/NallaTeja/MOP-PAS/assets/145950340/5e8c86a0-c68c-4ab3-a3e2-63b2fe9603aa)

Click `Yes`.
![image](https://github.com/NallaTeja/MOP-PAS/assets/145950340/014fe257-0fad-45b4-b2dd-8a23d970bb98)

Click Ok.
![image](https://github.com/NallaTeja/MOP-PAS/assets/145950340/bf931876-ca62-4f34-b4db-edc1d14b7c9f)

Server Address: 192.168.32.130
Default User Name: administrator
Password: Secur1tyP@ss
![image](https://github.com/NallaTeja/MOP-PAS/assets/145950340/9aaf0d4e-7d0a-420c-a6f1-6cd360076f18)

Click Ok
![image](https://github.com/NallaTeja/MOP-PAS/assets/145950340/41345454-3b3f-4e93-a6cd-7b97ce2b480c)

Restart the VM. Client server installed successfully.
![image](https://github.com/NallaTeja/MOP-PAS/assets/145950340/437d2862-68cd-42a4-89c2-55507ecac7f9)

Access the PrivateArk 

![image](https://github.com/NallaTeja/MOP-PAS/assets/145950340/8fc71272-14fb-480c-834b-ea00edac9389)



