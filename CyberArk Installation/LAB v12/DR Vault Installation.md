Stop the privateArk server service
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/3c6d0995-bc8b-441e-a967-4514248cfcda)

![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/e1dc9fd9-3663-4f41-a60d-d13645c260f3)

Install the PADR component in primary vault.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/828cd88b-b6dc-4af8-a9e0-9fc730374ebc)

Setup the Cyberark Vault Disaster Recovery.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/34d7d513-0de1-4edd-97b2-f66aca521fc0)

Accept the License Agreement
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/40fddcd8-6245-4900-af1f-bc6355e195da)

Fill the user information.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/e288520f-6faa-4029-961a-dda3b0f9b44c)

Choose Destination Location
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/80381ed6-5dad-468c-b916-85b14a65a196)

User: **DR**
Password:
```
Tej@143
```
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/65a58c6d-77c9-47e8-a265-4f236aaab899)


Replicate Vault Details, Address ```192.168.5.129``` and Port ```1858```
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/a6927b47-ed21-4bbe-a39a-06bb75a918b7)

Finish the setup complete.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/e11f814c-9833-4b77-949c-5ce1aef3f2ca)

Check the logs and verfiy the replication complete. Run the PADR.exe file, open the PADR log file.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/744908ae-e8b7-4e4d-95c7-66ff1aea6311)

```
C:\Program Files (x86)\PrivateArk\PADR\Logs
```

![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/11de9334-e156-4cbd-9bf0-8fe43cc52081)

Also verfiy the PADR configuration file where **Failovermode = No**
```
C:\Program Files (x86)\PrivateArk\PADR\Conf
```

![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/5d0fa3bb-8e8d-41d1-9b4b-606ee2b28dda)

![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/9bdd3f06-4740-41ad-9be7-1d306fc4f623)
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/21b79174-41a1-4156-ad34-21f5e803d569)

# We gone test wheather DR is replicating the safes.
Open Primary Valut privateark client login as administrator. open Tools > Administrative Tools > Users and Groups on Server Valut. Select the New> User.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/a3787c49-db2d-4fea-b6db-5b0e59172bfe)

Give User Name and password
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/8849014f-91f8-40bf-b562-e25d43957d00)
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/4731d6b0-049e-4f78-b1a2-ddaf6d49b02e)

Create a new safe via PVWA UI in adminsitator credentials. 
Policies> Access Control > Add Safe
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/74904cc6-14af-471f-a613-74beadc45aa4)

![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/b6b9b2d5-d4cf-4a01-947c-27c8fe16798d)

Add Member in the safe.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/1908ba54-c1bf-4201-85e5-5df12e3659f0)

Verify the safe is created in primary vault
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/b8632172-5231-49b5-86b1-1fd881bfe729)

# Now we are going to test the automatic DR failover.
Step1: stop Primary vault privateark server service via privateark server.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/24c285a4-0469-4bec-97a8-01028dafddcf)

Step2: Log into the DRVault. Open powershell as administrator, run below commands. 
```
cd "C:\Program Files (x86)\PrivateArk\PADR"
```
```
Get-Content .\logs\padr.log -wait
```
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/4ebce1fb-6a06-41d0-b3b7-5afeabf9f84d)

After 5 attempts of failure, the data will be syncronized and DR failover will completed successfully.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/64c522e9-b056-4496-9dd0-7bb672b93cfc)

Login into the privateark client of DR vault check the replication.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/d3193044-c6f4-4c46-8d0c-22fd51216e7b)

The disaster recovery service got stopped. Privateark server service start running
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/fe1823e8-8cde-49c4-a9f7-5c3485f4f61a)

Login into the PVWA UI check the failover.
Before that we need to update DRvault IP address in **vault.ini** file 
```
C:\CyberArk\Password Vault Web Access\VaultInfo
```
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/f71b7606-b8f1-41a5-a177-b7de877c1dc2)

Do iisreset and check if you are able to login into the pvwa.
```
iisreset
```
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/4707e8c8-8e32-4aa7-b2cd-49585ee03d95)

Successfully able to access the pvwa as a administrator
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/01479224-8927-459d-9a50-be90771f93cc)


# Fall back from DRvault to Primary Vault. 

Stop the privateark server service
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/90040d0e-d43b-48fe-9ba1-85eab3861a37)
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/28c3a774-9558-462e-9322-ae6e6ef854a7)

Install the PADR component in primary vault.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/828cd88b-b6dc-4af8-a9e0-9fc730374ebc)

Setup the Cyberark Vault Disaster Recovery.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/34d7d513-0de1-4edd-97b2-f66aca521fc0)

Accept the License Agreement
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/40fddcd8-6245-4900-af1f-bc6355e195da)

Fill the user information.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/e288520f-6faa-4029-961a-dda3b0f9b44c)

Choose Destination Location
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/80381ed6-5dad-468c-b916-85b14a65a196)

Replicate User details

User: **DR**
Password:
```
Tej@143
```
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/65a58c6d-77c9-47e8-a265-4f236aaab899)


Replicate Vault Details, Address and Port.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/4b5432a2-d49b-49b1-a879-116d8f2fbcbf)

Setup Complete, restart the server.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/9b55c1ee-06a8-4208-9c05-3e2fdc3a7ff7)

Log into the DR vault server and change the DR user password which need to be matched with primary vault.

![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/b2842eca-82a5-4ca2-ab47-6b0e80f47e8d)

![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/db1301ab-9faf-45da-b081-6fda98a04595)

![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/04cbc030-cc09-476a-b12b-b5b539a3370d)




PVWA system health. we can see the all components Primary & DR vault and other commonents.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/7625ff2e-c887-4aa5-b7df-42e50cff114b)



# Index
- [Install Prerequisistes](#step-1-:-Install-Prerequisites)
- [Client Setup](#step-9-start-client-setup)
- [DR Setup Vault](#installation-of-dr-vault)
- [Failover Test](#validation)
  
# CyberArk Disaster Recovery Vault Installation Guide

## Step-by-Step Instructions

### Step 1: Install Prerequisistes
Install .NET Framework 4.8 or the latest version.
Install Microsoft Visual Studio x64 and x86.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/625f54fd-bd6a-4f64-b2f1-a062eabad22c)

### Step 2: Configure Network Protocols

- **Disable all protocols** except for **TCP/IPv4**.

![Disable Protocols](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/d56b2f67-b5af-460b-9ef7-5f0f6dd0ead0)
![Enable TCP/IPv4](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/ed380242-cb44-45d8-91ed-927174db68bf)


### [Step 3: Run Server Setup]

- Navigate to the server file.
- Run the setup as **Administrator**.

![Run Setup](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/e3e04327-83b6-4c59-96b4-e9a5c0e25527)

### Step 4: Setup Wizard

- Click **Next** in the setup program.

![Click Next](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/38ef4c46-12f1-4964-ab42-93f6c592218b)

- Accept the license agreement and click **Yes**.

![Accept License](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/34d22c97-6d22-497e-9344-f6d1eb05532c)

- Provide user information (Name and Company).

![User Information](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/2b02815b-8ef5-4ff0-a477-e8a8461cdf9d)

- Select **Vault Mode** as **Standalone Vault Installation**.

![Standalone Vault](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/88a62b7b-578e-42c0-a1c4-1657766b3020)

- Choose the installation folder.

![Installation Folder](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/6380ecf5-a294-440a-9fd3-a7df802e79b7)

- Select the folder for storing the safes.

![Storage Folder](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/311e485e-3e4d-4a1f-bfa5-0f06c815c784)

- Enter the license `.xml` file path.

![License Path](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/911d334e-a874-4032-9ff4-d930b1f9ca13)

- Enter the operator CD path.

![Operator CD Path](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/452b80f8-1648-407e-83b0-e581a1b691e3)

### Step 5: Configure Remote Control Agent

- Configure the remote control agent (PVWA server IP: `192.168.5.130` and password: `Tej@143`).

![Remote Control Agent](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/06a68fd5-0207-41c0-b5a7-139811d18c52)

- Uncheck **Distribute Vaults** (RabbitMQTM will be installed).

![Uncheck Distribute Vaults](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/120c55cd-a77b-4f72-beb9-c5616e29d813)

### Step 6: Vault Server Machine Hardening

- Select the program folder and click **Next**. Digital Vault Machine Hardening will start, followed by the installation of the Private Ark Database Setup.

![Hardening Start](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/fa92be0d-2391-400c-a469-24298085b9c9)
![Private Ark Setup](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/c0c8e580-071e-419a-bc5a-6f2816379dd0)
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/0fd1a15d-7d22-4292-a0f0-a5123d629981)

### Step 7: Set Built-in Users Passwords

- Set the following passwords:
  - Master Account Password: `P@ssw0rd123`
  - Administrator Account Password: `Secur1tyP@ss`

**Note:** Use complex passwords with a mixture of numeric and mixed case characters. By default, the password must contain at least one numeric character and 5 mixed case characters

![Set Passwords](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/c2735ddb-8de1-4bbf-bbc0-f5975ed764d5)

### Step 8: Restart System

- After successful installation, the system will restart.

### [Step 9: Start Client Setup](#step-9-start-client-setup)

- Run the client setup installation as **Administrator**.

![Client Setup](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/eb028733-e0a5-429e-b625-6e6ab57da02b)

- Set up the PrivateArk Client.

![PrivateArk Client](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/8566d4fc-b3ad-4df4-bd3d-f23ee69b9480)

- Accept the license agreement.

![Accept License](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/55759066-d74b-44fe-9b34-c3c746d54d1f)

- Fill in user information.

![User Information](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/4e7c7679-d33f-40cb-a215-68ecc677827d)

- Choose the setup installation path of PrivateArk client.

![Installation Path](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/c2436314-7a57-4795-8bbf-436db62e34a5)

- Select the client setup type.

![Setup Type](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/2dfe98d8-e739-45da-adf0-ecc63d23149c)

- Select the program folder.

![Program Folder](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/0102767f-1d35-45d6-abce-8a2b50ceccce)

- Define the PrivateArk Vault.

![Define Vault](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/a9044107-1202-42d0-9a7b-5c086d3424b8)

- Click **Yes** for restart upon setup completion.

![Setup Complete](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/fdad2b1c-eced-4f16-bacb-e0c3f96ed604)

## [Validation](#validation)

1. **Log into the PrivateArk Client:** Ensure the following safes are created: Notification Engine, System, VaultInternal.

![Created Safes](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/8f8d4232-1b22-4b99-8562-d3fa692e2d02)

2. **Check Services:** Verify that the services are running.

![Check Services](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/8c6d6612-28c5-4d0f-92af-8a4e10b46e51)
![Check Services](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/d5658617-46e1-470b-9636-8a84e39fb708)

## Pre-Installation Check for DR Vault

- **System Health:**

![System Health](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/00e073ff-8660-46d9-9260-5ab6e0ba6e2e)

- **PrivateArk Safe:**

![PrivateArk Safe](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/c93c22cd-6095-47da-a7d2-9fd1495d967f)

## [Installation of DR Vault](#installation-of-dr-vault)

1. **Log into the Primary Vault:**
   - Open the PrivateArk client, update the DR user, uncheck the **Disable user** for the DR user profile, and update the password to `Tej@143`.

2. **Stop the PrivateArk Server Service:**

![Stop Service

](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/3c6d0995-bc8b-441e-a967-4514248cfcda)
![Stop Service](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/e1dc9fd9-3663-4f41-a60d-d13645c260f3)

3. **Install the PADR Component in Primary Vault:**

![Install PADR](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/828cd88b-b6dc-4af8-a9e0-9fc730374ebc)

4. **Setup the CyberArk Vault Disaster Recovery:**

![Setup DR](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/34d7d513-0de1-4edd-97b2-f66aca521fc0)

5. **Accept the License Agreement:**

![Accept License](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/40fddcd8-6245-4900-af1f-bc6355e195da)

6. **Fill the User Information:**

![User Information](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/e288520f-6faa-4029-961a-dda3b0f9b44c)

7. **Choose Destination Location:**

![Destination Location](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/80381ed6-5dad-468c-b916-85b14a65a196)

- **User:** `DR`
- **Password:** `Tej@143`

![DR User](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/65a58c6d-77c9-47e8-a265-4f236aaab899)

8. **Replicate Vault Details:**
   - Address: `192.168.5.129`
   - Port: `1858`

![Replicate Vault](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/a6927b47-ed21-4bbe-a39a-06bb75a918b7)

9. **Finish Setup and Verify Logs:**

![Setup Complete](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/e11f814c-9833-4b77-949c-5ce1aef3f2ca)

10. **Run PADR.exe File and Verify Log File:**
    - Check the logs and verify the replication is complete.
    - Path: `C:\Program Files (x86)\PrivateArk\PADR\Logs`

![PADR Logs](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/11de9334-e156-4cbd-9bf0-8fe43cc52081)

11. **Verify PADR Configuration File:**
    - Ensure `Failovermode = No`
    - Path: `C:\Program Files (x86)\PrivateArk\PADR\Conf`

![PADR Config](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/5d0fa3bb-8e8d-41d1-9b4b-606ee2b28dda)

## [Test DR Replication](#test-dr-replication)

1. **Create a New User:**
   - Open Primary Vault PrivateArk client.
   - Login as administrator.
   - Navigate to Tools > Administrative Tools > Users and Groups on Server Vault.
   - Select New > User.
   - Provide username and password.

![Create User](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/a3787c49-db2d-4fea-b6db-5b0e59172bfe)
![User Credentials](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/8849014f-91f8-40bf-b562-e25d43957d00)
![Create User](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/4731d6b0-049e-4f78-b1a2-ddaf6d49b02e)

2. **Create a New Safe via PVWA UI:**
   - Login with administrator credentials.
   - Navigate to Policies > Access Control > Add Safe.
   - Add member in the safe.

![Add Safe](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/74904cc6-14af-471f-a613-74beadc45aa4)
![Safe Details](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/b6b9b2d5-d4cf-4a01-947c-27c8fe16798d)
![Add Member](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/1908ba54-c1bf-4201-85e5-5df12e3659f0)
![Verify Safe](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/b8632172-5231-49b5-86b1-1fd881bfe729)

## [Test Automatic DR Failover](#test-automatic-dr-failover)

1. **Stop Primary Vault PrivateArk Server Service:**

![Stop Service](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/24c285a4-0469-4bec-97a8-01028dafddcf)

2. **Log into DR Vault and Run Commands:**
   - Open PowerShell as administrator.
   - Navigate to the PADR directory and monitor the logs.
   - Commands:
     ```
     cd "C:\Program Files (x86)\PrivateArk\PADR"
     Get-Content .\logs\padr.log -wait
     ```

![Run Commands](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/4ebce1fb-6a06-41d0-b3b7-5afeabf9f84d)

3. **Verify DR Failover:**
   - After 5 attempts of failure, data synchronization completes, and DR failover is successful.

![Failover Success](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/64c522e9-b056-4496-9dd0-7bb672b93cfc)
![DR Vault](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/d3193044-c6f4-4c46-8d0c-22fd51216e7b)

4. **Verify PVWA UI Access:**
   - Update `vault.ini` file with DR vault IP address.
   - Path: `C:\CyberArk\Password Vault Web Access\VaultInfo`
   - Run `iisreset` and check access.

![Update Vault.ini](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/f71b7606-b8f1-41a5-a177-b7de877c1dc2)
![iisreset](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/4707e8c8-8e32-4aa7-b2cd-49585ee03d95)
![PVWA Access](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/01479224-8927-459d-9a50-be90771f93cc)

## [Fall Back from DR Vault to Primary Vault](#fall-back-from-dr-vault-to-primary-vault)

1. **Stop the PrivateArk Server Service:**

![Stop Service](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/90040d0e-d43b-48fe-9ba1-85eab3861a37)
![Stop Service](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/28c3a774-9558-462e-9322-ae6e6ef854a7)

2. **Install the PADR Component in Primary Vault:**

![Install PADR](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/828cd88b-b6dc-4af8-a9e0-9fc730374ebc)

3. **Setup the CyberArk Vault Disaster Recovery:**

![Setup DR](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/34d7d513-0de1-4edd-97b2-f66aca521fc0)

4. **Accept the License Agreement:**

![Accept License](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/40fddcd8-6245-4900-af1f-bc6355e195da)

5. **Fill the User Information:**

![User Information](https://github.com/NallaTeja/C

yberArk-PAS/assets/145950340/e288520f-6faa-4029-961a-dda3b0f9b44c)

6. **Choose Destination Location:**

![Destination Location](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/80381ed6-5dad-468c-b916-85b14a65a196)

7. **Replicate User Details:**
   - **User:** `DR`
   - **Password:** `Tej@143`

![DR User](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/65a58c6d-77c9-47e8-a265-4f236aaab899)

8. **Replicate Vault Details:**

![Replicate Vault](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/4b5432a2-d49b-49b1-a879-116d8f2fbcbf)

9. **Setup Complete and Restart Server:**

![Setup Complete](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/9b55c1ee-06a8-4208-9c05-3e2fdc3a7ff7)

10. **Log into DR Vault and Change DR User Password:**
    - Ensure the DR user password matches with the primary vault.

![Change Password](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/b2842eca-82a5-4ca2-ab47-6b0e80f47e8d)
![Password Change](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/db1301ab-9faf-45da-b081-6fda98a04595)
![Password Match](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/04cbc030-cc09-476a-b12b-b5b539a3370d)

11. **Verify PVWA System Health:**
    - Ensure all components, including the Primary and DR vault, are functioning properly.

![System Health](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/7625ff2e-c887-4aa5-b7df-42e50cff114b)

By following these steps, you can ensure a smooth installation and failover process for CyberArk's Disaster Recovery Vault.
