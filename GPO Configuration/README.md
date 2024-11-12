# How to Create Group Policy Objects (GPOs) on Windows Server 2022

This guide provides a step-by-step process for **creating Group Policy Objects (GPOs)** on **Windows Server 2022**. GPOs are used to manage and configure operating system settings, security options, and applications across a network.

## Prerequisites

- A **Windows Server 2022** machine with **administrator privileges**.
- An **AD DS** role installed and configured.
- Familiarity with **Active Directory** and **Group Policy** concepts.

---

## Step 1: Open the Group Policy Management Console (GPMC) 

The **Group Policy Management Console (GPMC)** is the central tool for creating and managing GPOs.

1. **Open Server Manager**:
   - Click the **Start** button and open **Server Manager**.

2. **Install the Group Policy Management Feature (if not already installed)**:
   - In **Server Manager**, click **Add roles and features**.
   - Select **Role-based or feature-based installation**, then click **Next**.
   - On the **Select features** page, check the box next to **Group Policy Management**.
   - Click **Next**, and then **Install** if it's not already installed.

3. **Open GPMC**:
   - After installation, click the **Start** button, type **Group Policy Management**, and press **Enter**.
   - This will open the **Group Policy Management Console**.

![image](https://github.com/user-attachments/assets/4a995f62-d55f-48be-8b87-e43fa279a67c)

---

## Step 2: Create a New Group Policy Object (GPO)

Once the GPMC is open, you can create a new GPO.

1. **Navigate to the Domain**:
   - In **Group Policy Management**, expand the forest and domain nodes in the left pane to locate your domain.

2. **Create a New GPO**:
   - Right-click on the **Group Policy Objects** node under your domain and select **New**.


![image](https://github.com/user-attachments/assets/8ddc4423-652c-4702-a81a-29af72142385)


   - Enter a **name** for the GPO (e.g., **Custom Security Settings**).
   - Click **OK** to create the new GPO.


![image](https://github.com/user-attachments/assets/9cbf4670-759c-4c02-baa5-fb6ce6279081)

---

## Step 3: Edit the GPO

After creating the GPO, you need to edit it to apply specific settings.

1. **Right-click the GPO**:
   - Right-click the newly created GPO and select **Edit**.


![image](https://github.com/user-attachments/assets/8d415170-aa09-4e0d-b027-66f5ac6b3026)


2. **Configure the Settings**:
   - The **Group Policy Management Editor** will open. This editor allows you to configure both **Computer Configuration** and **User Configuration** settings.
     - **Computer Configuration**: Settings that apply to computers (e.g., security settings, software installation).
     - **User Configuration**: Settings that apply to user accounts (e.g., desktop settings, folder redirection).
   - Navigate through the sections in the **Editor** and configure the settings you require. For example:
     - **Security Settings**: Under **`Computer Configuration > Policies > Windows Settings > Security Settings>Account Policies>Password Policy`**, you can configure password policies, user rights assignments, etc.
  
   ![image](https://github.com/user-attachments/assets/6bd5d16e-87a1-41da-8afa-3f891d37fe34)

     - **Software Settings**: Under **`User Configuration > Policies > Software Installation`**, you can configure desktop settings, start menu options, etc. Right-click on the empty space, then click **`New`** and then click on **`package`**. Follow the wizard to complete the configuration.

![image](https://github.com/user-attachments/assets/1d8f31d7-7c3b-4732-b75b-6ad39388fcdc)

   
3. **Apply the Changes**:
   - After configuring the desired settings, close the **Group Policy Management Editor**.

---

## Step 4: Link the GPO to an Organizational Unit (OU) or Domain

Now that the GPO is created and configured, you need to apply it by linking it to an **Organizational Unit (OU)** or the entire **domain**.

1. **Link the GPO**:
   - In the **Group Policy Management Console**, right-click on the **OU** or **domain** where you want the GPO to apply.
   - Select **Link an Existing GPO**.


![image](https://github.com/user-attachments/assets/3af52d70-3dff-4940-bf72-530422e2b318)


2. **Select the GPO**:
   - In the **Select GPO** dialog, select the GPO you created (e.g., **Custom Security Settings**) and click **OK**.


![image](https://github.com/user-attachments/assets/2f1ab568-c0e5-4463-850b-c5ca648e614c)


---

## Step 5: Force Group Policy Update

To apply the new GPO immediately, you can force a group policy update on the client machines.

1. **Force Update on the Server**:
   - Open **Command Prompt** on the server and type the following command:
     ```bash
     gpupdate /force
     ```


![image](https://github.com/user-attachments/assets/87981000-10f1-4780-9cf4-8d86dd10b063)


2. **Force Update on Client Machines**:
   - On client machines, open **Command Prompt** and type the following command:
     ```bash
     gpupdate /force
     ```

This will immediately apply the new policy settings.

---

## Step 6: Verify the GPO Application

After applying the GPO, it’s important to verify that it is correctly applied to the target machines or users.

1. **Use Group Policy Results (GPResult)**:
   - Open **Command Prompt** on the target machine and type the following command:
     ```bash
     gpresult /r
     ```
   - This will display the current group policies applied to the machine and user.


![image](https://github.com/user-attachments/assets/040b78dc-37b7-49d4-a969-4c950c9d61b8)


2. **Use Group Policy Modeling**:
   - In **Group Policy Management**, right-click on **Group Policy Modeling** under your domain and select **Group Policy Modeling Wizard**.
   - Follow the wizard to simulate how the GPO will be applied to a specific user or machine.


![image](https://github.com/user-attachments/assets/ec04dba0-3bbc-4d4d-8635-753f904cb6e0)


---

## Additional Notes

- **GPO Precedence**: If multiple GPOs are linked to an OU, the order in which they are applied is determined by the link order. You can adjust this order in the **Group Policy Management Console** by using the **Up** and **Down** buttons in the **Linked Group Policy Objects** section.
- **GPO Inheritance**: By default, GPOs are inherited from parent OUs to child OUs. You can block inheritance at a specific level if needed by right-clicking on an OU and selecting **Block Inheritance**.

---
### Conclusion

You’ve successfully created, configured, and linked a Group Policy Object (GPO) on **Windows Server 2022**. This allows you to manage and enforce a wide range of policies across your network.
