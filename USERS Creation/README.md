# How to Create Users on Windows Server 2022

This guide provides step-by-step instructions on how to create **users** on **Windows Server 2022**.

## Prerequisites

- **Windows Server 2022** machine with **administrator privileges**.
- Basic knowledge of **User Management** and **Active Directory** (if using AD).

---

## Step 1: Create a Local User Account

If you're not using Active Directory (AD), you can create local user accounts.

1. **Open Server Manager**:
   - Click the **Start** button and open **Server Manager**.

2. **Open Computer Management**:
   - In **Server Manager**, click **Tools** in the top-right corner, then select **Computer Management**.

3. **Navigate to Local Users and Groups**:
   - In the **Computer Management** window, expand **Local Users and Groups**.
   - Click on **Users**.

4. **Create a New User**:
   - In the right-hand pane, right-click and select **New User**.

5. **Fill in User Information**:
   - In the **New User** window, fill in the following details:
     - **User Name**: Enter the username.
     - **Full Name**: Enter the full name (optional).
     - **Description**: Enter a description (optional).
     - **Password**: Enter a password. Ensure that the password meets the server's security policy.
     - **Confirm Password**: Re-enter the password.

6. **Set Password Options**:
   - Choose from the following options:
     - **User must change password at next logon**: This forces the user to change their password when they first log in.
     - **User cannot change password**: This prevents the user from changing their password.
     - **Password never expires**: This ensures that the password doesn’t expire (use with caution).
     - **Account is disabled**: This option can be checked if you want to create a user without enabling their account immediately.

7. **Create the User**:
   - After filling out the necessary information and selecting the desired options, click **Create**.

8. **Close the New User Window**:
   - Once the user is created, click **Close** to exit the window.

---

## Step 2: Add User to Groups (Optional)

You can add the newly created user to specific groups to grant them certain permissions.

1. **Navigate to the User Properties**:
   - In the **Local Users and Groups** > **Users** section, right-click the user and select **Properties**.

2. **Add to Groups**:
   - In the **User Properties** window, go to the **Member Of** tab.
   - Click **Add** to add the user to a group (e.g., **Administrators**, **Users**, or any custom groups you’ve created).
   - Type the group name and click **OK** to add the user to that group.

3. **Apply Changes**:
   - Click **OK** to apply the changes and close the window.

---

## Step 3: Create Users via PowerShell (Alternative Method)

You can also create users through **PowerShell**, which is helpful for bulk creation or automation.

1. **Open PowerShell**:
   - Right-click the **Start** button and select **Windows PowerShell (Admin)**.

2. **Create a New User**:
   - Run the following command to create a new user:
     ```powershell
     New-LocalUser "Username" -FullName "Full Name" -Description "User Description" -Password (ConvertTo-SecureString "Password123!" -AsPlainText -Force)
     ```
   - Replace `"Username"`, `"Full Name"`, and `"Password123!"` with your desired values.

3. **Add User to a Group**:
   - To add the user to a specific group, use the following command:
     ```powershell
     Add-LocalGroupMember -Group "Group Name" -Member "Username"
     ```
   - Replace `"Group Name"` with the group (e.g., `Administrators`, `Users`) and `"Username"` with the username you created.

---

## Step 4: Create Users in Active Directory (If Using AD)

If you're using **Active Directory (AD)**, follow these steps to create users within your domain.

1. **Open Active Directory Users and Computers**:
   - In **Server Manager**, click on **Tools**, then select **Active Directory Users and Computers**.

2. **Navigate to Organizational Unit (OU)**:
   - In the **Active Directory Users and Computers** window, navigate to the desired **Organizational Unit (OU)** or **Users** folder.

3. **Create a New User**:
   - Right-click the folder or OU, select **New** and then **User**.

4. **Fill in User Information**:
   - In the **New Object – User** window, provide the following details:
     - **First Name**: Enter the user’s first name.
     - **Last Name**: Enter the user’s last name.
     - **User logon name**: Enter the username (e.g., `jdoe`).

5. **Set Password**:
   - Enter the password for the user.
   - Choose the password options (e.g., **User must change password at next logon**).

6. **Create the User**:
   - Click **Next**, then **Finish** to create the user in Active Directory.

---

## Step 5: Test the User Account

To ensure the account is created correctly, try logging in with the newly created user credentials.

1. **Test the User Login**:
   - Log off the current session and try logging in with the **new user’s credentials** to verify that the account works as expected.

---

## Additional Notes

- **User Groups**: Adding users to specific groups determines their access permissions. Ensure you understand the purpose of each group and grant the user the appropriate access level.
- **Active Directory**: If you’re managing multiple users across a domain, Active Directory simplifies user management and centralizes control over user access.

---

## License

This guide is licensed under the [MIT License](LICENSE).

---

### Conclusion

You’ve successfully created users on **Windows Server 2022**, whether via local accounts, PowerShell, or Active Directory. Managing user accounts is an essential part of server administration, and now you have the tools to efficiently create and manage them.
