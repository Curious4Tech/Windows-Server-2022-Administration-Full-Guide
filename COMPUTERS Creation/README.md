# How to Create Computers on Windows Server 2022

This guide walks you through the steps to **create computers** on **Windows Server 2022**, which can be used for managing **Active Directory (AD)** environments and assigning network resources.

## Prerequisites

- A **Windows Server 2022** machine with **administrator privileges**.
- An **Active Directory Domain Services (AD DS)** installed
- Basic knowledge of **Active Directory** and **Computer Management**.

---

## Step 1: Create a Computer in Active Directory

To create new computers, you’ll be using the **Active Directory Users and Computers** management tool.

1. **Open Active Directory Users and Computers**:

   - Go to the **Tools** menu in **Server Manager** and select **Active Directory Users and Computers**.
     
3. **Navigate to the Organizational Unit (OU)**:
   - In the **Active Directory Users and Computers** window, expand your domain, and navigate to the appropriate **Organizational Unit (OU)** where you want to create the new computer.Here we're going to use the default **Computers** OU in our domain.
     
   - Right-click on the **Computers** where you want to place the new computer, and then select **New > Computer**.

     
![image](https://github.com/user-attachments/assets/b59184f5-9e53-41ec-8ff8-fe08d39f8fa7)


4. **Create the Computer Object**:
   - In the **New Object – Computer** dialog:
   - **Computer name**: Enter the name of the computer (e.g., `Client01`), then click on **OK**.


![image](https://github.com/user-attachments/assets/4355a33d-8bb0-4be5-b8af-9217dc510cdd)

   - **Computer DNS name**: If needed, specify the DNS name (the default will be the same as the computer name).
   - Optionally, you can set the **user logon name** if you want the computer to be able to join the domain immediately. You can leave this blank for now.


![image](https://github.com/user-attachments/assets/7a3a2d37-6e01-4a6f-b69e-26a43a70305f)

---

## Step 2: Verify the Computer Creation

After the computer object is created, you should verify it in **Active Directory**.

1. **Verify in Active Directory Users and Computers**:
   - In the **Active Directory Users and Computers** window, go to the **Computers** where you created the computer object.
   - You should see the newly created **computer object** listed.
   - Right-click on the computer name and select **Properties** to verify settings such as **computer name** and **membership**.


![image](https://github.com/user-attachments/assets/0fea4dfa-63a7-475a-84ca-312545f9516d)

---

## Step 3: Join a Computer to the Domain

To add a new physical or virtual machine to the domain, follow these steps:

1. **Log into the Computer**:
   - Log into the newly created computer (if it's physical or virtual).

2. **Change the Computer's Domain**:
   - Right-click **This PC** on the desktop and select **Properties**.


![image](https://github.com/user-attachments/assets/010196df-df0b-4b13-937a-ac2d74652371)

   - Under **Computer name, domain, and workgroup settings**, click on **Rename this PC (Advanced)**.
   - In the **System Properties** window, click on **Change**.
   - Select **Domain** and enter the domain name (e.g., `yourdomain.local`).

   ![image](https://github.com/user-attachments/assets/b8d0fdcd-4f66-4263-b91e-5c7ab97b9b4a)

   - Enter the **domain admin credentials** when prompted and click on **OK**.

![image](https://github.com/user-attachments/assets/dd482dae-3294-4d95-ac85-4b165d4cec9c)


2. **Restart the Computer**:
   - Once successfully joined to the domain, a prompt will appear asking you to restart the computer. Click **OK**, then restart the computer.


![image](https://github.com/user-attachments/assets/e5ba4cb4-fb92-4a3a-954d-b267151c4b3d)


3. **Verify Domain Join**:
   - After the computer reboots, log in with the **domain credentials** to confirm it is properly joined to the domain.


![image](https://github.com/user-attachments/assets/f9b3843a-0505-468a-8d6a-5e5a53645085)

---

## Step 4: Additional Computer Configuration (Optional)

Now our computer has joined the domain.

![image](https://github.com/user-attachments/assets/f3a53d78-72b1-43d9-af0c-26a75e8b9351)

After the computer is created and joined to the domain, you may want to configure additional settings.

1. **Configure Group Policies**:
   - Apply **Group Policy Objects (GPOs)** to manage computer settings for security, network configuration, and software installation.

2. **Set Up Remote Desktop**:
   - Enable **Remote Desktop** on the computer if needed by going to **Control Panel > System and Security > System > Remote Settings**, then enabling **Allow remote connections to this computer**.

3. **Assign Roles or Resources**:
   - Configure roles (e.g., file server, application server) or assign network resources (e.g., shared folders, printers) to the new computer.

---

### Conclusion

You’ve successfully created a new computer in **Active Directory** and joined it to the domain in **Windows Server 2022**. This setup allows for easier management of network resources and computer configurations within your domain environment.
