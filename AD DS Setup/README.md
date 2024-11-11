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

3. **Select Installation Type**:
   - Choose **Role-based or feature-based installation** and click **Next**.

4. **Select Destination Server**:
   - Ensure your current server is selected and click **Next**.

5. **Select Server Roles**:
   - In the **Roles** list, check **Active Directory Domain Services**.
   - A pop-up window will appear asking to add additional features. Click **Add Features**.
   - Click **Next** to proceed.

6. **Add Features**:
   - You can leave the default features selected. Click **Next**.

7. **AD DS Information**:
   - Review the information about AD DS and click **Next**.

8. **Confirm Installation**:
   - Review your selections, then click **Install**.
   - The installation process may take a few minutes. Once it’s complete, do not close the wizard as you’ll need it to promote the server to a domain controller.

---

## Step 2: Promote the Server to a Domain Controller

1. **Promote to Domain Controller**:
   - Once AD DS is installed, click the **Promote this server to a domain controller** link in the wizard.

2. **Deployment Configuration**:
   - Choose **Add a new forest** and enter your desired **Root domain name** (e.g., `example.com`).
   - Click **Next**.

3. **Domain Controller Options**:
   - Choose the **Forest functional level** and **Domain functional level** (default to Windows Server 2022).
   - Ensure **Domain Name System (DNS) server** is checked.
   - Enter a **Directory Services Restore Mode (DSRM) password** and click **Next**.

4. **DNS Options**:
   - A warning may appear about a DNS delegation; you can safely ignore this for now and click **Next**.

5. **Additional Options**:
   - The **NetBIOS domain name** should be automatically generated based on your domain name. Click **Next**.

6. **Paths**:
   - Specify the locations for the **Database**, **Log files**, and **SYSVOL** folders or leave them at their default paths. Click **Next**.

7. **Review Options**:
   - Review your configurations. Click **Next** to begin the **prerequisite check**.

8. **Install AD DS**:
   - Once the prerequisite check is complete, click **Install** to promote the server.
   - The server will automatically restart once the installation is complete.

---

## Step 3: Verify the AD DS Installation

After your server reboots, log back in to verify that AD DS is set up and functioning properly.

1. **Check Server Manager**:
   - Open **Server Manager**. You should see a new option labeled **AD DS** in the left-hand menu.
   - Click on **AD DS** to verify the health and functionality of the Active Directory services.

2. **Open Active Directory Administrative Tools**:
   - Open the **Tools** menu in **Server Manager** and select **Active Directory Users and Computers**.
   - You should see your domain listed in the left-hand pane. You can now create **Organizational Units (OUs)**, **Users**, **Groups**, and **Computers**.

---

## Additional Notes

- **Static IP**: Ensure your server has a static IP address for consistent network identification.
- **DNS Configuration**: The server is now also acting as a DNS server for the domain.

---
### Conclusion

You have successfully installed and configured **Active Directory Domain Services (AD DS)** on **Windows Server 2022**. Your server is now a **Domain Controller** capable of managing user accounts, permissions, and security policies across your network.
