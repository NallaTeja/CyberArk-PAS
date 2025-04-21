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
   - **IP Address**: `192.168.29.102`
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

