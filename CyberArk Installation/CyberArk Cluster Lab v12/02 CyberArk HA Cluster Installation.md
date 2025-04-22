# CyberArk HA Cluster Installation Guide

## Required Servers
To install a CyberArk HA Cluster, the following three servers are needed:
- **SanDrive01**
- **NodeA**
- **NodeB**

---

## Step 1: Enabling Remote Desktop
1. Open **Server Manager** → **Local Server**.
2. Double-click the **Disabled** option next to Remote Desktop.

   ![Remote Desktop](https://github.com/user-attachments/assets/815e00e2-e4ef-44c4-9e2a-d903d6434d07)

3. In **System Properties**, go to the **Remote** tab.
4. Select **Allow remote connections to this computer**.
5. Uncheck **Allow connections only from computers running RD with NLA**.
6. Click **Apply** and **OK**.

   ![System Properties Remote](https://github.com/user-attachments/assets/5ffc68a6-fdfd-44e0-a236-6e248e7c1cf0)

7. Repeat these steps for **NodeA** and **NodeB**.

---

## Step 2: Configuring SanDrive01 Network
1. Open **Server Manager**.
2. Locate **Ethernet0**.
3. Open **IPv4 Properties**.
4. Set:
   - **IP Address**: `192.168.5.141`
   - **Subnet Mask**: `255.255.255.0`

   ![SanDrive01 IP](https://github.com/user-attachments/assets/47c1f3da-8e97-495b-95b1-bdd44ed13f27)

---

## Step 3: Configuring NodeA Network

### **Step 3.1: Add Network Adapter**
1. Open **Network Adapter Settings**.
2. Click **Add**, select **Network Adapter**, then **Finish**.

   ![Network Adapter Setup](https://github.com/user-attachments/assets/a45062cb-1f3d-4fa1-bef1-a8111ffb8db0)

### **Step 3.2: Assign VMnet0**
1. Under **Network Adapter 2**, set:
   - **Custom: Specific Virtual Network** → **VMnet0**.

   ![Adapter Custom](https://github.com/user-attachments/assets/e5a54752-5770-4181-9f74-522cecc00c21)

### **Step 3.3: Rename Ethernet Interfaces**
1. Rename **Ethernet0** → **Public**.
2. Rename **Ethernet1** → **Private**.

   ![Rename Ethernet](https://github.com/user-attachments/assets/16a7b1f3-ac5c-4f86-ae3c-7c351f47f30f)
   ![Renamed Successfully](https://github.com/user-attachments/assets/2fb73ec2-5632-4ec0-a7f0-7da592b8317c)

### **Step 3.4: Configure Public Network**
1. Define:
   - **IP Address**: `192.168.137.2`
   - **Subnet Mask**: `255.255.255.0`

   ![NodeA IP](https://github.com/user-attachments/assets/1d495781-a34a-4fd1-93f6-1eda1dd472ab)

2. Enable **Sharing** in **Public Properties**.

   ![Public Properties](https://github.com/user-attachments/assets/0cadca5e-7c3b-4ca4-affb-5249e2c43bcd)

3. **Uncheck all connection users** except IPv4 & IPv6.

   ![Uncheck Items](https://github.com/user-attachments/assets/0e1e4d8b-3423-44e7-9094-e5b9c350c673)

### **Step 3.5: Configure Private Network**
1. Define:
   - **IP Address**: `192.168.137.1`
   - **Subnet Mask**: `255.255.255.0`

   ![Private network](https://github.com/user-attachments/assets/cbcd67d1-88af-4232-9c71-59a859bb6060)

2. Change **Network Adapter** from **NAT** to **Custom: Specific Virtual Network** → **VMnet0**.

   ![Network Adapter Public](https://github.com/user-attachments/assets/5e89943c-3adc-4caa-b457-90e0b8f7ebe7)

---

### ⚠ **Production Environment Considerations**
1. **Disable Internet connection sharing** in Public properties.
2. **Uncheck all connection users** except IPv4 & IPv6.
3. Ensure **public and private networks** are correctly assigned.

   ![Network Connections](https://github.com/user-attachments/assets/2d21ce36-2299-460f-8779-960fce1664fe)

---

## Step 4: Configuring NodeB Network

### **Step 4.1: Ensure Same Subnet**
1. Repeat the **same steps** for **NodeB**, ensuring:
   - Public and Private are set to **VMnet0**.
   - IP addresses are correctly assigned.

   ![NodeB same subnet](https://github.com/user-attachments/assets/80a9a7cc-b17d-49c8-b10e-eed96b420e92)

### **Step 4.2: Rename Network Interfaces**
1. Rename **Ethernet0** → **Public**, **Ethernet1** → **Private**.

   ![Rename Ethernet](https://github.com/user-attachments/assets/395d0c94-9cc4-4e1e-ae6b-ab7e1e25a56c)

### **Step 4.3: Configure Public Network**
1. Define:
   - **IP Address**: `192.168.138.1`
   - **Subnet Mask**: `255.255.255.0`

   ![NodeB IP Public](https://github.com/user-attachments/assets/1be89968-250c-4acd-9c82-75c808659bbc)

2. **Uncheck all connection users** except IPv4 & IPv6.

### **Step 4.4: Configure Private Network**
1. Define:
   - **IP Address**: `192.168.138.2`
   - **Subnet Mask**: `255.255.255.0`

   ![NodeB IP Private](https://github.com/user-attachments/assets/f7e542b4-c98a-43d5-b5de-8e42a2e884b8)

---

## Note:

Now, **pinging other servers** may not be possible due to firewall rules.  
To allow communication between servers, **Inbound & Outbound firewall rules** need to be enabled after **Vault installation hardening**.

---
# iSCSI Target Server Setup Guide

## Step 1: Accessing the Server
1. Go to your **SanDrive01** or **database server**.
2. Open **Server Manager**.
3. Select **Add roles and features**, then click **Next**.

   ![Add role](https://github.com/user-attachments/assets/5d51aebb-6645-4a0f-987d-19ad40cb00fb)

## Step 2: Installation Type
1. Select **Role-based or feature-based installation**.
2. Click **Next**.

   ![Installation Type](https://github.com/user-attachments/assets/063c3669-ce23-4b87-a49d-4be4f771a7fc)

## Step 3: Server Selection
1. Choose **Select a server from the server pool**.
2. Click **Next**.

   ![Server Selection](https://github.com/user-attachments/assets/c7feb4a9-195f-4990-89de-8f81f06a4f9c)

## Step 4: Server Role Selection
1. Select **File and Storage Services** (1 to 12 installed).
2. Under **File and iSCSI Services**, select **iSCSI Target Server**.
3. Click **Add features** and proceed by clicking **Next** twice (skip the Features section).

   ![Server Role](https://github.com/user-attachments/assets/a0d348cd-c317-4077-9283-fdc98c4128af)

## Step 5: Confirmation and Installation
1. Review selections and click **Install**.
2. After the installation completes, click **Close**.

   ![Confirmation](https://github.com/user-attachments/assets/14579130-9008-4738-8059-9068199e1d6b)

## Step 6: Creating iSCSI Virtual Disks
1. In **Server Manager**, navigate to **File and Storage Services > iSCSI**.
2. Click **Start the New iSCSI Virtual Disk Wizard**, then click **Next**.

   ![iSCSI Virtual Disk location](https://github.com/user-attachments/assets/4cfcb795-606e-4db9-b6fb-65f3d8346434)

### Creating "Quorum" Disk
1. Under **iSCSI Virtual Disk Name**, enter **Quorum**, then click **Next**.

   ![iSCSI Virtual Disk Name](https://github.com/user-attachments/assets/f81cfd0f-a5a0-472d-9f2c-627d63459fa0)

2. Under **iSCSI Virtual Disk Size**, set **Size: 10 GB**, then click **Next**.

   ![iSCSI Virtual Disk Size](https://github.com/user-attachments/assets/ee4964c2-df34-4e02-bc1e-926dd5429b10)

3. Under **iSCSI Target**, select **New iSCSI Target**, then click **Next**.

   ![iSCSI Target](https://github.com/user-attachments/assets/97cba4b6-c26a-4273-9f59-3be82f55a83c)

4. Under **Target Name and Access**, enter **Quorum**, then click **Next**.

   ![Target Name](https://github.com/user-attachments/assets/8a10f66c-5b77-4aae-b64b-5107df43f5d2)

5. Under **Access Servers**, click **Add**, then:
   - Select **IP Address** from the dropdown.
   - Enter **NodeA (192.168.137.2)** and **NodeB (192.168.138.1)** (Public IP).

   ![Access Servers](https://github.com/user-attachments/assets/6dd41928-cdfe-4496-9d49-b8ea1aba457d)

6. After adding both Node servers, click **Next**.

   ![Added 2 node servers](https://github.com/user-attachments/assets/dbec581b-0f17-46bd-8c7c-9faad322332a)

7. Keep the default **Enable Authentication** settings, then click **Next**.
8. Under **Confirmation**, click **Create**, then **Close**.

   ![Confirmation](https://github.com/user-attachments/assets/a093abd2-5095-4d5c-be32-101af719ead3)
   ![Result](https://github.com/user-attachments/assets/4d1140da-671d-4b2d-b475-d93d070cf301)

### Creating "Shared" Disk
1. Right-click and select **New iSCSI Virtual Disk**.

   ![New iSCSI Virtual Disk](https://github.com/user-attachments/assets/9278ab52-b33b-4933-aa26-b51bb6f9f604)

2. Under **iSCSI Virtual Disk Location**, click **Next**.

   ![iSCSI Virtual Disk Location](https://github.com/user-attachments/assets/22955946-9861-4a43-8fa0-0026e7710250)

3. Under **iSCSI Virtual Disk Name**, enter **Shared**, then click **Next**.

   ![iSCSI Virtual Disk Name shared](https://github.com/user-attachments/assets/ca68f0ff-2729-458e-975f-2ebcd6dc650a)

4. Under **iSCSI Virtual Disk Size**, set **Size: 20 GB**, then click **Next**.

   ![iSCSI Virtual Disk Size 20](https://github.com/user-attachments/assets/5a3923e3-afc1-4d53-9274-4a34853d7228)

5. Under **iSCSI Target**, select **New iSCSI Target**, then click **Next**.

   ![New iSCSI Target](https://github.com/user-attachments/assets/289198f2-9eff-4f5f-a083-2750199e33c8)

6. Under **Target Name and Access**, enter **Shared**, then click **Next**.

   ![Target Name and Access shared](https://github.com/user-attachments/assets/2c407adf-49cd-464a-b84c-cd10b4af5c79)

7. Under **Access Servers**, click **Add**, then:
   - Select **IP Address** from the dropdown.
   - Enter **NodeA (192.168.137.2)** and **NodeB (192.168.138.1)** (Public IP).

   ![Access Servers](https://github.com/user-attachments/assets/5cabc33c-bd4a-4f18-96dd-d17315345d7e)

8. After adding both Node servers, click **Next**.

   ![Added node servers](https://github.com/user-attachments/assets/223aae2c-186d-40cb-80ec-c6335b7e7f22)

9. Keep the default **Enable Authentication** settings, then click **Next**.
10. Under **Confirmation**, click **Create**, then **Close**.

    ![Confirmation](https://github.com/user-attachments/assets/41fb71c3-5aab-46a7-8f11-2f97830ab5ca)
    ![Result and close](https://github.com/user-attachments/assets/3d5c77b0-0974-4883-88ee-f93edc22040d)

---

