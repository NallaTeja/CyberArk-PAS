![image](https://github.com/NallaTeja/MOP-PAS/assets/145950340/5bb71dcf-2196-4c58-91a4-ffed588eade7)


Here's a revised and corrected version of the installation process for CyberArk PSMP (Privileged Session Manager Proxy):

1. **Download PSMP 11.7 from Secure File Exchange (SFE) Portal:**
   - Visit [SFE Portal](https://support.cyberark/SFE/files.aspx).
   - https://support.cyberark.com/SFE/
   - Navigate to v11.7 > Latest > CorePAS.
   - Select "Privileged Session Manager SSH Proxy-Rls-11.7.zip" to download.

2. **Connect to PSMP Server and Authenticate:**
   - Connect to the PSMP server using the connection string:
     ```
     c11088@p1c11088%corp@TargetServer_IPaddress@pam-psmp.corp.xyz.com
     ```
   - Authenticate using SafeNet MobilePass token.

3. **Prepare PSMP Directory Structure:**
   ```bash
   sudo /sbin/kingme.sh
   cd /var
   mkdir PSMP
   ```

4. **Transfer Files:**
   - Copy the PSMP RPM file to the Linux machine (location: `/root/tmp`) via WinSCP from PVWA portal using your privileged account.
   - Copy the PSMP ZIP file to `/var/PSMP`.

5. **Set Permissions:**
   ```bash
   cd /var/PSMP
   chmod 777 PSMP_file_name
   ```

6. **Edit Vault.ini File:**
   ```bash
   vi vault.ini
   ```
   - Provide Vault IP and Vault name and save the file.

7. **Prepare PSMP Parameter File:**
   ```bash
   cd /var/PSMP
   cp psmpparms.sample /var/tmp/psmpparms
   vi /var/tmp/psmpparms
   ```
   - Edit `psmpparms` file:
     ```
     InstallationFolder=/var/PSMP
     AcceptCyberArkEULA=Yes
     ```

8. **Enable Security-Enhanced Linux (SELinux):**
   ```bash
   vi /etc/sysconfig/selinux
   ```
   - Set `SELINUX=enforcing`.

9. **Prepare Credential File:**
   ```bash
   cd /var/PSMP
   chmod 777 CreateCredFile
   ./CreateCredFile "user.ini"
   ```
   - Execute the script, provide Vault credentials, and press Enter.

10. **Install PSMP RPM File:**
    ```bash
    rpm -ivh CARKpsmp-11.07.0.12.x86_64.rpm
    ```
   - This RPM file will install PSMP service, PSMP AD bridging, along with other important configuration files and log files.

Ensure to follow these steps in the given order and pay attention to any important configurations or validations mentioned along the way.
