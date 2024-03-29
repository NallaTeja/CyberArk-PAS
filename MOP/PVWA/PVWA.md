Index use cases and PVWA related SOP
#001 PVWA – How to Create or Update Credential Files (Credfile) Manually (Version 12.1.1 and Above ONLY)

#001 PVWA – How to Create or Update Credential Files (Credfile) Manually (Version 12.1.1 and Above ONLY)
Article: https://cyberark.my.site.com/s/article/PVWA-How-can-I-create-or-update-the-credential-files-credfile-for-the-PVWA-manually-VERSION-12-1-1-and-above-ONLY
Article Number: 000018324

## Step-by-step instructions
**IMPORTANT NOTE:** This article is for version 12.1.1 ONLY. If you are on version 12.1.0 or below, please follow this [article](#) instead.

1. **Stop IIS on PVWA Server:**
   - Stop IIS to proceed with the manual credential file update.
   - Open Command Prompt as Administrator.
   - Run the following command to stop IIS:
     ```
     iisreset /stop
     ```
2. **Log in to PrivateArk Client:**
   - Log in to PrivateArk Client as "Administrator" or a user with "Manage Users" privileges in the root location.

3. **Navigate to Users and Groups:**
   - Go to Menu "Tools->Administrative Tools->Users and Groups".

4. **Update PVWAAppUser:**
   - Select "PVWAAppUser" and click "Update".
     - Make sure to select the correct PVWAAppUser. Check C:\CyberArk\Password Vault Web Access\credfiles > appuser.ini for verification.

5. **Set New Password for PVWAAppUser:**
   - Specify a new, random password in the "Password" field under the "Authentication Tab". Repeat it and click "OK".

6. **Activate Trusted Net Areas:**
   - Click the "Trusted Net Areas" button and ensure the "State" is set to "Active". If inactive, click "Activate" to change the state to active. Remember/write down the password set for later use.

7. **Update PVWAGWUser:**
   - Select "PVWAGWUser" and click "Update".
     - Ensure to select the correct PVWAGWUser. Check C:\CyberArk\Password Vault Web Access\credfiles > gwuser.ini for verification.

8. **Set New Password for PVWAGWUser:**
   - Specify a new, random password in the "Password" field under the "Authentication Tab". Repeat it and click "OK".

9. **Activate Trusted Net Areas:**
   - Similar to step 6, ensure the "State" is set to "Active". Remember/write down the password set for later use.

10. **Open Administrative Command Line:**
    - On the PVWA Server, open an administrative command line and navigate to "C:\CyberArk\Password Vault Web Access\Env".
     ```
     cd C:\CyberArk\Password Vault Web Access\Env
     ```
11. **Run Command for AppUser:**
    - Run the command:
      ```
      CreateCredFile.exe appuser.ini Password /Username PVWAAppUser /Password {Enter_password} /AppType PVWAApp /ExePath "c:\windows\system32\inetsrv\w3wp.exe" /EntropyFile /DPAPIMachineProtection​
      ```

12. **Run Command for GWUser:**
    - Run the command:
      ```
      CreateCredFile.exe gwuser.ini Password /Username PVWAGWUser /Password {Enter_password} /AppType PVWAApp /ExePath "c:\windows\system32\inetsrv\w3wp.exe" /EntropyFile /DPAPIMachineProtection
      ```

13. **Move Files to CredFiles Directory:**
    - Newly created Credfiles and EntopyFiles located in "C:\CyberArk\Password Vault Web Access\Env"
    - File names "appuser.ini", "gwuser.ini", "gwuser.ini.entropy", "appuser.ini.entropy".
    - Move the newly created CredFiles and EntropyFiles to "C:\CyberArk\Password Vault Web Access\CredFiles".

14. **Start IIS:**
    - Start IIS (and its dependent services like ) on the PVWA machine.
    - Dependent services names World Wide Web Publishing Service (W3SVC), Windows Process Activation Service (WAS), Windows Remote Management (WS-Management), HTTP SSL, Windows Event Log, CyberArk Credential Provider Service
   - Run the following command to start IIS:
     ```
     iisreset /start
     ```
15. **Verify PVWA Access:**
    - Ensure you can access the PVWA using your web browser.

