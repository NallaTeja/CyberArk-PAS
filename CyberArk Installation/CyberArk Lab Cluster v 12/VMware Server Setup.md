# VMware Virtual Machine Setup Guide

## Step 1: Open VMware and Create a New Virtual Machine
1. Open **VMware**.
2. Go to **File** → Click **New Virtual Machine**.
3. Select **Custom** and click **Next**.

![Custom](https://github.com/user-attachments/assets/da37d9bd-89dc-4206-b8cb-ee341ffdfb9f)

## Step 2: Configure VM Hardware Compatibility
1. Choose the desired **VM Hardware Compatibility**.
2. Click **Next**.

![VM Hardware Compatibility](https://github.com/user-attachments/assets/ef9883b5-85bc-43c2-9d86-328ae8460ee1)

## Step 3: Guest OS Installation
1. Select **"I will install the operating system later"**.
2. Click **Next**.

![Guest OS Installation](https://github.com/user-attachments/assets/1c6a011a-4c3a-4819-9448-9e6c739120ad)

## Step 4: Choose Guest OS
1. Select **Microsoft Windows** as the **Guest Operating System**.
2. Choose **Windows Server 2016** as the version.
3. Click **Next**.

![Guest Operating System](https://github.com/user-attachments/assets/e5b1c73b-83fb-49ce-99d2-fc5f20f5a18d)

## Step 5: Name the Virtual Machine
1. Enter a name for the virtual machine.
2. Click **Next**.

![Name the virtual Machine](https://github.com/user-attachments/assets/d7ac6488-9bb1-424d-aebe-3978ec71daf2)

## Step 6: Select Firmware Type
1. Choose **BIOS** as the **Firmware Type**.
2. Click **Next**.

![Firmware](https://github.com/user-attachments/assets/1b1c9db2-19b4-4f8b-b340-b555fd3d57bb)

## Step 7: Configure Hardware Resources
- **Processor**: Select based on system capabilities (**Example: 1 Processor**).
- **Memory**: Set the required amount (**Example: 1024 MB**).

![Processor Configuration](https://github.com/user-attachments/assets/ee95776f-eccc-4ecd-bbad-688683d1f20c)

![Memory for the VM](https://github.com/user-attachments/assets/a283dedd-e494-4125-9a08-07d4503ed6bc)

## Step 8: Configure Network
1. Choose **NAT** as the network type.
2. Click **Next**.

![Network Type](https://github.com/user-attachments/assets/74f02bea-7bc3-4b20-94cb-c84f96c82d06)

## Step 9: Select I/O Controller
1. Choose **LSI Logic SAS** as the controller type.
2. Click **Next**.

![I/O controller typer](https://github.com/user-attachments/assets/ff441eb1-d044-42dc-ab10-7c06b1a451bf)

## Step 10: Select Disk Type and Storage
- **Disk Type**: Select **NVMe**.
- **Disk Storage**: Choose **"Create a new virtual disk"**.
- **Disk Capacity**: Set to **20 GB**, stored as a **single file**.

![Disk type](https://github.com/user-attachments/assets/f03f489b-d7f1-4fbb-9186-3bf51011df68)

![Disk](https://github.com/user-attachments/assets/36089e68-1c18-46db-83c8-b438fb4464eb)

![Specify Disk capacity](https://github.com/user-attachments/assets/f44e203d-45ed-465d-af84-cff9407fb875)

## Step 11: Finalize and Create VM
1. Keep the default disk file name.
2. Click **Next**.
3. Click **Finish** to create the VM.

![Ready to create VM](https://github.com/user-attachments/assets/ce6f1ece-2680-4483-932d-98d7bcae9680)

## Step 12: Edit VM Settings (Optional)
1. In VMware Home, select **Node_A**.
2. Click **Edit virtual machine settings**.

![Edit virtual machine settings](https://github.com/user-attachments/assets/d1bb40d8-ae43-42bb-b1af-ee0f122e026f)

---
**Note**: Adjust the settings based on your system capabilities and requirements.
