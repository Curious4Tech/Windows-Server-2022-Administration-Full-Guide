# How to Create Computers on Windows Server 2022

This guide walks you through the steps to **create computers** on **Windows Server 2022**, which can be used for managing **Active Directory (AD)** environments and assigning network resources.

## Prerequisites

- A **Windows Server 2022** machine with **administrator privileges**.
- Basic knowledge of **Active Directory** and **Computer Management**.

---

## Step 1: Open Active Directory Users and Computers

To create new computers, you’ll be using the **Active Directory Users and Computers** management tool.

1. **Open Server Manager**:
   - Click the **Start** button and open **Server Manager**.

2. **Install Active Directory Domain Services (AD DS)** (If not installed):
   - In **Server Manager**, click on **Add Roles and Features**.
   - Follow the wizard to install **Active Directory Domain Services**. This step will require you to promote the server to a domain controller if it's not already done.
   - Once the installation is complete, reboot the server if needed.

3. **Open Active Directory Users and Computers**:
   - After installation, go to the **Tools** menu in **Server Manager** and select **Active Directory Users and Computers**.

---

## Step 2: Create a Computer in Active Directory

Now, you'll create a new computer object in **Active Directory**.

1. **Navigate to the Organizational Unit (OU)**:
   - In the **Active Directory Users and Computers** window, expand your domain, and navigate to the appropriate **Organizational Unit (OU)** where you want to create the new computer.
   - Right-click on the **OU** where you want to place the new computer, and then select **New > Computer**.

2. **Create the Computer Object**:
   - In the **New Object – Computer** dialog:
     - **Computer name**: Enter the name of the computer (e.g., `Server01`).
     - **Computer DNS name**: If needed, specify the DNS name (the default will be the same as the computer name).
     - Optionally, you can set the **user logon name** if you want the computer to be able to join the domain immediately. You can leave this blank for now.
   - Click **Next**.

3. **Assign a Computer Account**:
   - The next dialog will allow you to set additional options for the computer account, such as joining the computer to a domain.
     - To allow a computer to join a domain, check the box labeled **This is a domain computer** and enter the necessary details.
   - Click **Next**, then click **Finish** to create the computer.

---

## Step 3: Verify the Computer Creation

After the computer object is created, you should verify it in **Active Directory**.

1. **Verify in Active Directory Users and Computers**:
   - In the **Active Directory Users and Computers** window, go to the **OU** where you created the computer object.
   - You should see the newly created **computer object** listed.
   - Right-click on the computer name and select **Properties** to verify settings such as **computer name** and **membership**.

---

## Step 4: Join a Computer to the Domain

To add a new physical or virtual machine to the domain, follow these steps:

1. **Log into the Computer**:
   - Log into the newly created computer (if it's physical or virtual).

2. **Change the Computer's Domain**:
   - Right-click **This PC** on the desktop and select **Properties**.
   - Under **Computer name, domain, and workgroup settings**, click on **Change settings**.
   - In the **System Properties** window, click on **Change**.
   - Select **Domain** and enter the domain name (e.g., `yourdomain.local`).
   - Enter the **domain admin credentials** when prompted.

3. **Restart the Computer**:
   - Once successfully joined to the domain, a prompt will appear asking you to restart the computer. Click **OK**, then restart the computer.

4. **Verify Domain Join**:
   - After the computer reboots, log in with the **domain credentials** to confirm it is properly joined to the domain.

---

## Step 5: Additional Computer Configuration (Optional)

After the computer is created and joined to the domain, you may want to configure additional settings.

1. **Configure Group Policies**:
   - Apply **Group Policy Objects (GPOs)** to manage computer settings for security, network configuration, and software installation.

2. **Set Up Remote Desktop**:
   - Enable **Remote Desktop** on the computer if needed by going to **Control Panel > System and Security > System > Remote Settings**, then enabling **Allow remote connections to this computer**.

3. **Assign Roles or Resources**:
   - Configure roles (e.g., file server, application server) or assign network resources (e.g., shared folders, printers) to the new computer.

---

## License

This guide is licensed under the [MIT License](LICENSE).

---

### Conclusion

You’ve successfully created a new computer in **Active Directory** and joined it to the domain in **Windows Server 2022**. This setup allows for easier management of network resources and computer configurations within your domain environment.
