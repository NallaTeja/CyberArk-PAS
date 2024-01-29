## Index

### Use Cases

1. [Adding Users to "Vault Admins" Group in PrivateArk Client](#adding-users-to-vault-admins-group-in-privateark-client)
2. [Triggering a Full Replication on DR Vault (DR Replication)](#triggering-a-full-replication-on-dr-vault-dr-replication)
3. [Performing a Manual DR Failover](#performing-a-manual-dr-failover)




---

**SOP #001** 
### Adding cyberark Engineer/Administrators to "Vault Admins" Group in PrivateArk Client

---

## Introduction:
Adding users to the "Vault Admins" group in the PrivateArk Client grants them administrative privileges within the CyberArk Vault. This guide provides step-by-step instructions for adding users to the "Vault Admins" group.

## Steps:

1. **Log-in to PrivateArk Client:**
   - Launch the PrivateArk Client application.

2. **Navigate to Users and Groups:**
   - Go to `Tools` > `Administrative Tools` > `Users and Groups`.

3. **Locate "Vault Admins" Group:**
   - Under the 'System' section, locate the "Vault Admins" group. This group contains users with administrative privileges.

4. **Select "Update" Option:**
   - Click on the "Update" button associated with the "Vault Admins" group.

5. **Add Users:**
   - In the dialog box that appears, add the network IDs of the users you want to add to the "Vault Admins" group.

6. **Save Changes:**
   - After adding users, save the changes.

7. **Verify Users Addition:**
   - Verify that the added users are now listed within the "Vault Admins" group.

## Additional Notes:
- Users added to the "Vault Admins" group will have elevated privileges within the CyberArk Vault, including the ability to manage and administer vault resources.
- Exercise caution when granting administrative privileges to users, as they will have access to sensitive vault data and configurations.


---

**SOP #002**
### Triggering a Full Replication on DR Vault (DR Replication)

---

Article: https://cyberark.my.site.com/s/article/00005115
Article Number: 000004199
## Introduction
In some cases, it may be necessary to trigger a full replication on the Disaster Recovery (DR) Vault server to resolve issues with replication. This guide provides step-by-step instructions on how to perform a full replication on the DR Vault.

## Step-by-step instructions
### 1. Stop PrivateArk Server Service:
   - On the DR Vault machine, ensure that the PrivateArk Server service is stopped.

### 2. Edit PADR.ini File:
   - Navigate to the DR installation folder (usually located at `C:\Program Files (x86)\PrivateArk\PADR`).
   - Open the `PADR.ini` file.

### 3. Modify PADR.ini:
   - Within the `PADR.ini` file, do the following:
     i. Set the following parameter:
        ```
        Failovermode=no
        ```
     ii. Delete the following parameters:
        ```
        NextBinaryLogNumberToStartAt
        LastDataReplicationTimestamp
        ```
     iii. Save the file.

### 4. Restart CyberArk Vault Disaster Recovery Service:
   - Restart the CyberArk Vault Disaster Recovery service.

### 5. Verify Replication:
   - Check the `PADR.log` file to ensure that a full replication was carried out successfully.

## Additional Notes:
- Triggering a full replication on the DR Vault may resolve issues with replication and ensure data consistency between the primary and DR Vaults.

---

### Performing a Manual DR Failover
**SOP #003**

---

Article: https://cyberark.my.site.com/s/article/How-to-perform-a-manual-DR-Failover
Article Number: 000004249
## Introduction
Performing a manual Disaster Recovery (DR) failover ensures the continuity of CyberArk Vault operations in the event of a disaster. This guide outlines step-by-step instructions to execute a manual DR failover process.

## Step-by-step Instructions
### On the DR Vault Server:

1. **Stop CyberArk Vault Disaster Recovery Service:**
   - Stop the CyberArk Vault Disaster Recovery service. For HA Vaults, use the Cluster management console.

2. **Navigate to PADR Directory:**
   - Navigate to `\Program Files (x86)\PrivateArk\PADR`.

3. **Modify padr.ini:**
   - Open `padr.ini` and add the following line:
     ```ini
     ActivateManualFailover=Yes
     ```

4. **Start CyberArk Vault Disaster Recovery Service:**
   - Start the CyberArk Vault Disaster Recovery service. For HA Vaults, use the Cluster management console.

5. **Verify Failover:**
   - Check the `padr.log` located in `\Program Files (x86)\PrivateArk\PADR` to confirm failover completion. The following lines indicate a successful failover:
     ```
[03/05/2018   09:53:24.939546]    ::    ITADB399I Using encryption algorithms: Advanced Encryption Standard (AES), 256 bit, RSA (2048 bit), SHA2-512 (Protocol Integrity), SHA2-512 (Files Integrity).
[03/05/2018   09:53:26.003988]    ::    ITADM114I Successfully connected to Database, Database id 0.
[03/05/2018   09:53:26.021747]    ::    PADR0103I Failover process started.
[03/05/2018   09:53:26.022375]    ::    GetPADRWorkingDirectory returned [C:\Program Files (x86)\PrivateArk\PADR]
[03/05/2018   09:53:26.022417]    ::    GetPADRWorkingDirectory returned [C:\Program Files (x86)\PrivateArk\PADR]
[03/05/2018   09:53:26.029175]    ::    PADR0024I Synchronizing vault data and metadata.
[03/05/2018   09:53:26.186176]    ::    PADR0025I Failover process ended successfully.
[03/05/2018   09:53:26.186216]    ::    PADR0067I Starting Vault service.
[03/05/2018   09:53:30.653166]    ::    PADR0017I Failover completed, PADR service is shutting down.
[03/05/2018   09:53:30.830770]    ::    PADR0022I Disaster Recovery service terminated
     ```

6. **Update Vault.ini (if necessary):**
   - If testing component server functionality during the failover test, ensure that the Vault.ini file for each component server contains the IP address of the DR Vault Server.
--- The Vault.ini contains only the IP address of the DR Vault Server
or
--- The IP address of the DR Vault Server is listed first.
----- Note: Modifying the Vault.ini will require restarting the service relevant to the Component Server (CPM, PSM, PVWA, etc.)
 
When the failover test is complete, confirm that any changes made have been reverted.

### Post-failover Tasks:

1. **Revert Changes (if applicable):**
   - If changes were made during the failover test, revert them to their original state.

2. **Return DR Vault to DR Ready State:**
   - Stop the Vault Server using the PrivateArk Server Administration Console (For HA Vault, use the Cluster Administrator) and confirm that the Cyberark Event Notification Engine service has been stopped via the services.msc console.
   - Set the “FailoverMode” variable in \Program Files (x86)\Privateark\padr\padr.ini to No. 
   - Delete the following two entries in the padr.ini: NextBinaryLogNumberToStartAt, LastDataReplicationTimestamp 
   - Start “CyberArk Disaster Recovery service” 
   - Check \Program Files (x86)\Privateark\padr\padr.log to make sure replication is successful from Production Vault to DR Vault.

## Additional Notes:
- In HA configurations: HA vaults should be restored from failover using solution 3466, "What Are the Steps to Initiate Replication to an HA DR cluster?"
