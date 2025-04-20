# VMware Virtual Machine Setup Guide

## Step 1: Open VMware and Create a New Virtual Machine
1. Open **VMware**.
2. Go to **File** → Click **New Virtual Machine**.
3. Select **Custom** and click **Next**.

![Custom](https://github.com/user-attachments/assets/da37d9bd-89dc-4206-b8cb-ee341ffdfb9f)

---

## Step 2: Configure VM Hardware Compatibility
1. Choose the desired **VM Hardware Compatibility**.
2. Click **Next**.

![VM Hardware Compatibility](https://github.com/user-attachments/assets/ef9883b5-85bc-43c2-9d86-328ae8460ee1)

---

## Step 3: Guest OS Installation
1. Select **"I will install the operating system later"**.
2. Click **Next**.

![Guest OS Installation](https://github.com/user-attachments/assets/1c6a011a-4c3a-4819-9448-9e6c739120ad)

---

## Step 4: Choose Guest OS
1. Select **Microsoft Windows** as the **Guest Operating System**.
2. Choose **Windows Server 2016** as the version.
3. Click **Next**.

![Guest Operating System](https://github.com/user-attachments/assets/e5b1c73b-83fb-49ce-99d2-fc5f20f5a18d)

---

## Step 5: Name the Virtual Machine
1. Enter a name for the virtual machine.
2. Click **Next**.

![Name the virtual Machine](https://github.com/user-attachments/assets/d7ac6488-9bb1-424d-aebe-3978ec71daf2)

---

## Step 6: Select Firmware Type
1. Choose **BIOS** as the **Firmware Type**.
2. Click **Next**.

![Firmware](https://github.com/user-attachments/assets/1b1c9db2-19b4-4f8b-b340-b555fd3d57bb)

---

## Step 7: Configure Hardware Resources
- **Processor**: Select based on system capabilities (**Example: 1 Processor**).
- **Memory**: Set the required amount (**Example: 1024 MB**).

![Processor Configuration](https://github.com/user-attachments/assets/ee95776f-eccc-4ecd-bbad-688683d1f20c)

![Memory for the VM](https://github.com/user-attachments/assets/a283dedd-e494-4125-9a08-07d4503ed6bc)

---

## Step 8: Configure Network
1. Choose **NAT** as the network type.
2. Click **Next**.

![Network Type](https://github.com/user-attachments/assets/74f02bea-7bc3-4b20-94cb-c84f96c82d06)

---

## Step 9: Select I/O Controller
1. Choose **LSI Logic SAS** as the controller type.
2. Click **Next**.

![I/O controller typer](https://github.com/user-attachments/assets/ff441eb1-d044-42dc-ab10-7c06b1a451bf)

---

## Step 10: Select Disk Type and Storage
- **Disk Type**: Select **NVMe**.
- **Disk Storage**: Choose **"Create a new virtual disk"**.
- **Disk Capacity**: Set to **20 GB**, stored as a **single file**.

![Disk type](https://github.com/user-attachments/assets/f03f489b-d7f1-4fbb-9186-3bf51011df68)

![Disk](https://github.com/user-attachments/assets/36089e68-1c18-46db-83c8-b438fb4464eb)

![Specify Disk capacity](https://github.com/user-attachments/assets/f44e203d-45ed-465d-af84-cff9407fb875)

---

## Step 11: Finalize and Create VM
1. Keep the default disk file name.
2. Click **Next**.
3. Click **Finish** to create the VM.

![Ready to create VM](https://github.com/user-attachments/assets/ce6f1ece-2680-4483-932d-98d7bcae9680)

---

## Step 12: Edit VM Settings (Optional)
1. In VMware Home, select **Node_A**.
2. Click **Edit virtual machine settings**.

---

### Step 13: Enable Shared Folders
1. Go to the **Options** tab.
2. Enable **Share Folders** as 'Always Enable.'
3. Check **Map as network drive in Windows guests.**
4. Click **Add** and then **Next**.

   ![Edit virtual machine settings](https://github.com/user-attachments/assets/d1bb40d8-ae43-42bb-b1af-ee0f122e026f)

5. Name the shared folder and browse the host path. Click **Next**.

   ![Name the share folder](https://github.com/user-attachments/assets/5a0cb530-8d9a-48ab-bd97-bf3652daf770)

6. Specify shared folder attributes:
   - Check **Enable this share.**
   - Click **Finish.**

   ![image](https://github.com/user-attachments/assets/48916e41-5c85-493e-a832-00bae89e6a3f)

7. Click **OK** to enable shared folders.

   ![enabling the sharefolders](https://github.com/user-attachments/assets/1887099a-0337-4420-ada7-2672cc96b606)

---

### Step 14: Mount ISO File
1. Go to **Edit virtual machine settings** under the **Hardware** tab.
2. Select **CD/DVD (SATA)**.
3. Browse to the ISO file path (e.g., `C:\Users\Dell\Downloads\Windows_Server_2016_Datacenter_EVAL_en-us_14393_refresh.ISO`) and click **OK**.
   ![ISO image file](https://github.com/user-attachments/assets/8850d546-a9ed-4bcf-8537-126b77aeffb2)

---

### Step 15: Power on the Virtual Machine
1. Power on the Virtual Machine.

   ![Power on](https://github.com/user-attachments/assets/da6328e3-9572-41d7-ae93-e276ab9f1592)

2. In Windows Setup, adjust settings:
   - Change **Time and Currency format** to **English (India)** and click **Next.**
   ![Time and currency format](https://github.com/user-attachments/assets/a1217a6e-f693-4fcb-9693-fb323ba4ab7f)

3. Click **Install Now** to proceed.

   ![Install now](https://github.com/user-attachments/assets/9e90c30a-f96f-4966-862d-b7721b32f088)

---

### Step 16: Select the Operating System
1. Choose **Windows Server 2016 Datacenter Evaluation (Desktop Experience)** and click **Next.**
   ![OS you want to install](https://github.com/user-attachments/assets/16fab979-3288-43c9-a987-471039b1fc61)

2. Accept the license terms:
   - Check the box **I accept the license terms.**
   - Click **Next.**

   ![Applicable notices and license terms](https://github.com/user-attachments/assets/39b24666-e5e4-4c4b-97d4-d04e6f5d34ea)

3. Select **Custom: Install Windows Only (Advanced).**
   ![Custom: Install windows only](https://github.com/user-attachments/assets/6c82afa2-1c0e-4c40-adc1-7270780e6ede)

4. Allocate 20 GB for the drive and click **Next.**

   ![where do you want to install windows](https://github.com/user-attachments/assets/6e23e0c2-6460-4ba0-99e6-4a9edc1e2763)

---

### Step 17: Complete Installation and Configuration
1. Wait for the installation to finish. The system will restart.
   ![Installing Windows status](https://github.com/user-attachments/assets/639ee8a5-e59f-4de0-8f6f-a61666a4233f)
   ![Getting ready](https://github.com/user-attachments/assets/607ddaa8-8d04-4d41-8ef9-032a8ecd871c)

2. Customize settings:
   - Username: **Administrator.**
   - Password: **Tej@143!!**
   - Click **Finish.**

3. Press **Ctrl+Alt+Delete** or use the Enter option to unlock.
   ![Ctrl+Alt+Delete to unlock](https://github.com/user-attachments/assets/626be5fa-37e1-440f-a5f5-bef0b53b626c)

4. Enter the Administrator password set earlier.
   ![administrator password](https://github.com/user-attachments/assets/f8cf2d1f-3353-4554-9f23-62d36f96e901)

---

### Step 18: Install VMware Tools
1. Go to the **VM** tab and select **Install VMware Tools**.
2. Double-click the DVD to begin installation.
   ![Install VMware tools](https://github.com/user-attachments/assets/38a66f52-0c0b-464e-ae5f-c1146d4b36ce)

3. Follow the setup prompts:
   - Click **Next** to proceed with installation.

     ![VMware tools 12.3](https://github.com/user-attachments/assets/ca193e90-b210-483c-b83b-aa0ad727be12)
   - Choose **Complete Setup** and click **Next**.

     ![Choose setup type](https://github.com/user-attachments/assets/f616094b-9565-476a-b3e7-78b3114c8901)

4. Click **Install** to finalize the installation.

   ![install](https://github.com/user-attachments/assets/8b7c3812-1193-45f1-b7e6-1f5a734017f4)

5. Skip the restart option by clicking **No**.

   ![Restart no](https://github.com/user-attachments/assets/16c85daa-585b-41de-b5e7-329eda1cb6b6)

---

### Step 19: Configure Computer Name
1. Open the **Server Manager** application.
2. Go to the **Local Server** option.
3. Double-click on the computer name (e.g., **WIN-7VTB3NJT655**) to access system properties.

   ![change computer name](https://github.com/user-attachments/assets/79701098-164d-4066-a87f-a26931a0e9bd)

4. Click **Change** to rename the computer (e.g., **Node_A**). Click **OK** twice and **Close**.

   ![Close the system properties](https://github.com/user-attachments/assets/3af9af58-8687-4115-90af-e0b5096611ce)

5. Skip the restart by clicking **Restart Later**.

   ![restart later](https://github.com/user-attachments/assets/59a68d4e-062f-421e-884f-4820d6fbbf03)

---

### Step 20: Update Windows
1. Search for **Windows Updates** in the taskbar.
2. Select **Check for Updates**.
   ![Check for windows updates](https://github.com/user-attachments/assets/8e52f8d5-e5aa-493d-99a7-92eea354120e)

3. Wait for updates to download and install automatically.
   ![Windows updates Downloading](https://github.com/user-attachments/assets/2100b823-8611-4010-afed-339b7e537fff)
   ![Windows updates Installing](https://github.com/user-attachments/assets/6b8a8aaf-922f-4b3a-96ec-cd3a75c6a489)

4. Restart the system once updates are completed.
   - **Method 1:**
   ![image](https://github.com/user-attachments/assets/782708ce-790c-4e29-82af-b2612e5974c5)

   - **Method 2:**
   ![Other Unplanned](https://github.com/user-attachments/assets/7bea4f15-1d58-4c0b-bd92-b77d1b88a9d1)
