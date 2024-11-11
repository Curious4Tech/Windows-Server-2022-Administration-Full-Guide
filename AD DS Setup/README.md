# How to Set Up Active Directory Domain Services (AD DS) on Windows Server 2022

This guide provides instructions for installing and configuring **Active Directory Domain Services (AD DS)** on **Windows Server 2022**. AD DS allows you to create and manage a domain, centralizing user and computer management within a network.

---

## Prerequisites

- A **Windows Server 2022** machine with **administrator privileges**.
- A **static IP address** assigned to your server (see previous guide on setting a static IP).
- DNS server configured (can be set up during AD DS installation).

---

## Step 1: Install Active Directory Domain Services

1. **Open Server Manager**:
   - Click the **Start** button and open **Server Manager**.

2. **Add Roles and Features**:
   - In **Server Manager**, click on **Manage** at the top-right and select **Add Roles and Features**.
   - The **Add Roles and Features Wizard** will open.

![image](https://github.com/user-attachments/assets/ec963e24-cf20-47cf-bbfc-c064f448a57a)


3. **Select Installation Type**:
   - Choose **Role-based or feature-based installation** and click **Next**.

![image](https://github.com/user-attachments/assets/ff48e18b-74ff-4468-a8df-319186cf2d2a)


4. **Select Destination Server**:
   - Ensure your current server is selected and click **Next**.

5. **Select Server Roles**:
   - In the **Roles** list, check **Active Directory Domain Services**.
     
![image](https://github.com/user-attachments/assets/da9d401e-33d5-43f6-9f6d-a32bd4dd3523)

   - A pop-up window will appear asking to add additional features. Click **Add Features**.

![image](https://github.com/user-attachments/assets/024bbeac-8d3a-4f1a-b3e4-690ca12ed53d)

   - Click **Next** to proceed.

6. **Add Features**:
   - You can leave the default features selected. Click **Next**.

7. **AD DS Information**:
   - Review the information about AD DS and click **Next**.

8. **Confirm Installation**:
   - Review your selections, then click **Install**.
   - The installation process may take a few minutes. Once it’s complete, do not close the wizard as you’ll need it to promote the server to a domain controller.

   
![image](https://github.com/user-attachments/assets/d5d76f66-437e-4457-bcea-06ed56e11781)

---

## Step 2: Promote the Server to a Domain Controller

1. **Promote to Domain Controller**:
   - Once AD DS is installed, click the **Promote this server to a domain controller** link in the wizard.

![image](https://github.com/user-attachments/assets/d4a18161-3c2c-4def-92b0-32e1ed9d8a01)


2. **Deployment Configuration**:
   - Choose **Add a new forest** and enter your desired **Root domain name** (e.g., `example.com`).
   - Click **Next**.

     
![image](https://github.com/user-attachments/assets/bf7e0cf2-aa28-4492-b2a9-ce4857300b34)


3. **Domain Controller Options**:
   - Choose the **Forest functional level** and **Domain functional level** (default to Windows Server 2022).
   - Ensure **Domain Name System (DNS) server** is checked.
   - Enter a **Directory Services Restore Mode (DSRM) password** and click **Next**.


![image](https://github.com/user-attachments/assets/6faf3bc6-f24a-4942-b424-2db693099be8)


4. **DNS Options**:
   - A warning may appear about a DNS delegation; you can safely ignore this for now and click **Next**.


![image](https://github.com/user-attachments/assets/e87773fa-61ae-4f95-ab8d-b088677883e3)

 
5. **Additional Options**:
   - The **NetBIOS domain name** should be automatically generated based on your domain name. Click **Next**.

6. **Paths**:
   - Specify the locations for the **Database**, **Log files**, and **SYSVOL** folders or leave them at their default paths. Click **Next**.

7. **Review Options**:
   - Review your configurations. Click **Next** to begin the **prerequisite check**.

8. **Install AD DS**:
   - Once the prerequisite check is complete, click **Install** to promote the server.
   - The server will automatically restart once the installation is complete


![image](https://github.com/user-attachments/assets/d6b1f712-af31-48bb-87db-bf8dc5a33f05)

---

## Step 3: Verify the AD DS Installation

After your server reboots, log back in to verify that AD DS is set up and functioning properly.

1. **Check Server Manager**:
   - Open **Server Manager**. You should see a new option labeled **AD DS** in the left-hand menu.
   - Click on **AD DS** to verify the health and functionality of the Active Directory services.


![image](https://github.com/user-attachments/assets/bf09270e-7327-4460-9dba-f59aae3d05f4)

---

## Additional Notes

- **Static IP**: Ensure your server has a static IP address for consistent network identification.
- **DNS Configuration**: The server is now also acting as a DNS server for the domain.

---
### Conclusion

You have successfully installed and configured **Active Directory Domain Services (AD DS)** on **Windows Server 2022**. Your server is now a **Domain Controller** capable of managing user accounts, permissions, and security policies across your network.
