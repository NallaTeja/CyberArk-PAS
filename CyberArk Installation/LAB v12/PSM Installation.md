Step 1: Defined IP address, Added to domain controller. Changed the computer name.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/848bd012-6ea8-414f-81ec-83221ea88209)

Step 2: Installing **Pre-Requisites** in powershell set the execution policy bypass & select **Yes**
C:\Users\Administrator\Downloads\Privileged Session Manager-Rls-v12.0.2\InstallationAutomation

``Set-ExecutionPolicy bypass -scope process``

![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/a24d5bfb-4da2-4af3-a7a9-dce5ea102fe8)

Execute following cmd
``.\Execute-Stage.ps1 "C:\Users\Administrator\Downloads\Privileged Session Manager-Rls-v12.0.2\InstallationAutomation\Prerequisites\PrerequisitesConfig.xml"``
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/5156a798-9e0b-4c53-b4ca-9e2dbb45a075)

Step 3: Run the setup as administrator and install.

![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/31b3aea5-ef76-46b9-973a-5fc6290fc601)
