Defined IP address, Added to domain controller. Changed the computer name.
-
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/848bd012-6ea8-414f-81ec-83221ea88209)

Installing **Pre-Requisites** in powershell set the execution policy bypass & select **Yes**
C:\Users\Administrator\Downloads\Privileged Session Manager-Rls-v12.0.2\InstallationAutomation
-
``Set-ExecutionPolicy bypass -scope process``

![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/a24d5bfb-4da2-4af3-a7a9-dce5ea102fe8)

Execute following cmd
``.\Execute-Stage.ps1 "C:\Users\Administrator\Downloads\Privileged Session Manager-Rls-v12.0.2\InstallationAutomation\Prerequisites\PrerequisitesConfig.xml"``
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/5156a798-9e0b-4c53-b4ca-9e2dbb45a075)
-
Run the setup as administrator and install.

![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/31b3aea5-ef76-46b9-973a-5fc6290fc601)

Click ``Yes``
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/e98594c1-80da-40ae-b520-2f122ee0b2d8)

Click ``Next``
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/7b921609-ae26-423f-b73a-9e8375d33c5f)

Click ``Yes``
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/d038ea05-012e-4169-b3ff-0f3456a557cf)

Give the basic info and Click ``Next``
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/33537eaf-7f01-4995-8aad-2fa5c4626a87)

Click ``Next``
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/274b38bb-f6af-4451-ad41-be2eabdd7410)

Recording folder will be created. Click ``Next``
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/f283cf61-85fd-4b07-836b-19e5f796e8fb)

Give a PVWAconfig file safe name. Click ``Next``
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/7c3e9ac1-d31c-4856-8e00-e4680845d0f3)
-
Give Vault Connection Detail. Click ``Next``
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/e773b4fd-2760-48be-ad2b-d3899d1bffa3)
-

Give Vault credentials Administrator and Password. Click ``Next``
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/195681ee-c8b9-4be4-9bed-ccad0a6cc1e8)
-
Give Protocol and host name for API gateway communication
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/4ad6d89d-b090-4036-bcf0-43c5f8c683e8)
-
Don't enable PKI. Click ``Next``
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/32b6f1b2-34d0-41c6-a1ed-93990c33265b)

PSM Hardening will be done. Click ``Next``
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/39145fbf-9a45-45df-b535-d7c2320c9e9f)

Restart the server. PSM service will be running
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/8ad0c450-8dab-45cf-b7c2-c75215e746fc)

Open PVWA console check the system health check connections
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/b3489558-7b32-4362-ae75-b64e1bc83065)

Check the PSM services. **CyberArk Privileged Session Manager**
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/d5f123b2-28fc-422c-a08c-85fa510be931)
