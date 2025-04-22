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
   - **IP Address**: `192.168.137.10`
   - **Subnet Mask**: `255.255.255.0`
   
   ![SanDrive01 IPe](https://github.com/user-attachments/assets/910206ff-bcd0-4ac2-96c7-468b76b89d83)

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
   - **IP Address**: `192.168.137.30`
   - **Subnet Mask**: `255.255.255.0`

![NodeA IP](https://github.com/user-attachments/assets/d4e48e3b-588a-447e-86dd-357d96c725f0)

2. Enable **Sharing** in **Public Properties**.

   ![Public Properties](https://github.com/user-attachments/assets/0cadca5e-7c3b-4ca4-affb-5249e2c43bcd)

3. **Uncheck all connection users** except IPv4 & IPv6.

   ![Uncheck Items](https://github.com/user-attachments/assets/0e1e4d8b-3423-44e7-9094-e5b9c350c673)

### **Step 3.5: Configure Private Network**
1. Define:
   - **IP Address**: `192.168.137.20`
   - **Subnet Mask**: `255.255.255.0`

![Private network](https://github.com/user-attachments/assets/46d9ab66-2ccd-46f8-b2ce-fd632158d129)

3. Change **Network Adapter** from **NAT** to **Custom: Specific Virtual Network** → **VMnet0**.

   ![Network Adapter Public](https://github.com/user-attachments/assets/5e89943c-3adc-4caa-b457-90e0b8f7ebe7)

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

![NodeB IP Public](https://github.com/user-attachments/assets/f9384596-6bf1-4363-afe3-e679b5ba826e)

3. **Uncheck all connection users** except IPv4 & IPv6.

### **Step 4.4: Configure Private Network**
1. Define:
   - **IP Address**: `192.168.138.40`
   - **Subnet Mask**: `255.255.255.0`

 ![NodeB IP Private](https://github.com/user-attachments/assets/5925bebf-4d00-4c74-95a8-75d66bb521f1)

---

## Open Windows firewall rule for all 3 servers, enable In & Out bound rules.
1. Inbound Rules
 - Open Windows firewall rule select 'Inbound Rules'. Under Actions select 'New Rule'.
![Program click Next](https://github.com/user-attachments/assets/c2bc9bac-08d3-4b49-b108-eadd94f2345e)

- Select 'All program' and click 'Next'
![New Firewall rule Inboudn all program](https://github.com/user-attachments/assets/1f53d577-291b-44b4-8965-3b99588f4f3f)

- Select "Allow the connection" and click 'Next'
![Allow the connection](https://github.com/user-attachments/assets/a021a3f4-027c-4497-a1b3-1dcd8aeb52e4)

- Profile allow all check box- Domain, Private, Public and click 'Next'. 
![Profile](https://github.com/user-attachments/assets/0a2d9c5e-fd32-48b1-91fb-7d65761835c2)

- Give any Name as per your request and click 'Finish'.
![Name](https://github.com/user-attachments/assets/bc29fd4f-ed70-4f95-988f-b8c5d56c0c83)


2. Repeate same steps for Outbound Rules

![Outbound Rules](https://github.com/user-attachments/assets/2e2e6f54-07dc-460d-82c5-713f960bd2aa)


- Do the ping test in command promt for connection test.

  ![cmd ping test result](https://github.com/user-attachments/assets/2a2a8e11-faf4-4c32-8daf-6c697ba3a62f)


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

### Creating "Quorm" Disk
1. Under **iSCSI Virtual Disk Name**, enter **Quorm**, then click **Next**.

![iSCSI Virtual Disk Name](https://github.com/user-attachments/assets/e1a04f16-c7b6-4376-ac26-d435c9a980ff)

3. Under **iSCSI Virtual Disk Size**, set **Size: 10 GB**, then click **Next**.

   ![iSCSI Virtual Disk Size](https://github.com/user-attachments/assets/ee4964c2-df34-4e02-bc1e-926dd5429b10)

4. Under **iSCSI Target**, select **New iSCSI Target**, then click **Next**.

   ![iSCSI Target](https://github.com/user-attachments/assets/97cba4b6-c26a-4273-9f59-3be82f55a83c)

5. Under **Target Name and Access**, enter **Quorm**, then click **Next**.

6. Under **Access Servers**, click **Add**, then:
   - Select **IP Address** from the dropdown.
   - Enter **NodeA (192.168.137.30)** and **NodeB (192.168.138.50)** (Public IP).

![Access Servers](https://github.com/user-attachments/assets/67f9f7e5-b9a8-45d5-b407-d7829a216f73)

8. After adding both Node servers, click **Next**.

   ![Added 2 node servers](https://github.com/user-attachments/assets/dbec581b-0f17-46bd-8c7c-9faad322332a)

9. Keep the default **Enable Authentication** settings, then click **Next**.
10. Under **Confirmation**, click **Create**, then **Close**.

![[Confirmation](https://github.com/user-attachments/assets/9859e08c-e36a-4ddc-815f-dcaf71177272)

![Result](https://github.com/user-attachments/assets/4d1140da-671d-4b2d-b475-d93d070cf301)

### Creating "Share" Disk
1. Right-click and select **New iSCSI Virtual Disk**.

   !New iSCSI Virtual Disk](https://github.com/user-attachments/assets/26da40c3-f774-49e8-8676-32097f8e780d)

2. Under **iSCSI Virtual Disk Location**, click **Next**.

   ![iSCSI Virtual Disk Location](https://github.com/user-attachments/assets/22955946-9861-4a43-8fa0-0026e7710250)

3. Under **iSCSI Virtual Disk Name**, enter **Share**, then click **Next**.

   ![iSCSI Virtual Disk Name](https://github.com/user-attachments/assets/0af241db-7b54-43da-a19f-f9a5e4a28f18)

4. Under **iSCSI Virtual Disk Size**, set **Size: 20 GB**, then click **Next**.

   ![iSCSI Virtual Disk Size 20](https://github.com/user-attachments/assets/5a3923e3-afc1-4d53-9274-4a34853d7228)

5. Under **iSCSI Target**, select **New iSCSI Target**, then click **Next**.

6. Under **Target Name and Access**, enter **Share**, then click **Next**.

  ![Target Name and Access share](https://github.com/user-attachments/assets/5cfd07ca-4276-4479-8138-07222f21349d)

7. Under **Access Servers**, click **Add**, then:
   - Select **IP Address** from the dropdown.
   - Enter **NodeA (192.168.137.30)** and **NodeB (192.168.138.50)** (Public IP).

  ![Access Servers](https://github.com/user-attachments/assets/283c1a7a-c1e8-4706-a6f1-9f473df8d199)

8. After adding both Node servers, click **Next**.

   ![Added node servers](https://github.com/user-attachments/assets/223aae2c-186d-40cb-80ec-c6335b7e7f22)

9. Keep the default **Enable Authentication** settings, then click **Next**.
10. Under **Confirmation**, click **Create**, then **Close**.

    ![Confirmation](https://github.com/user-attachments/assets/726c2397-bc2a-4003-83d0-b5080ddc6446)
    ![Result and close](https://github.com/user-attachments/assets/3d5c77b0-0974-4883-88ee-f93edc22040d)

---

Go to server NodeA, open server manager. Under Tools select 'iSCSI Initator'
![iSCSI Initator](https://github.com/user-attachments/assets/c5f9e671-31b0-4e82-bae0-6a8d57f9c6aa)

Service is not running, click 'Yes' button.
![image](https://github.com/user-attachments/assets/09213dd4-7b90-4caa-8f07-b3f969e91650)








