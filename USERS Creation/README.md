# How to Create and Manage Users in Active Directory on Windows Server 2022

This guide provides instructions on how to add users in **Active Directory (AD)** on **Windows Server 2022**.

## Prerequisites

- **Windows Server 2022** with **Active Directory Domain Services (AD DS)** installed.
- Administrator privileges to manage users in Active Directory.

---

## Step 1: Open Active Directory Users and Computers

1. **Open Server Manager**:
   - Click on the **Start** button and select **Server Manager**.

2. **Access AD DS**:
   - In **Server Manager**, go to the **Tools** menu at the top-right corner.
   - Select **Active Directory Users and Computers** from the drop-down list.


![image](https://github.com/user-attachments/assets/459d9fd7-eee4-4050-bd5e-1b6ffd50cd7b)

---

## Step 2: Navigate to the Organizational Unit (OU)

1. In **Active Directory Users and Computers**, locate the **Organizational Unit (OU)** where you want to create the user.
   - By default, you can create users in the **Users** container.
   - You may also create your own OU for specific groups of users (e.g., **Employees**, **IT Department**, etc.).

2. Right-click the OU (e.g., **Users**) where you want to add the user, and select **New > User**.


![image](https://github.com/user-attachments/assets/cd17fa5f-ed91-4994-8e57-0f1ec3644de3)

---

## Step 3: Create a New User Account

1. **Enter User Details**:
   - In the **New Object - User** dialog, fill in the following fields:
     - **First name**: Enter the user's first name.
     - **Initials** (optional): Enter the user's initials.
     - **Last name**: Enter the user's last name.
     - **Full name**: This field auto-populates but can be edited if necessary.
     - **User logon name**: This will be the username used for logging in (e.g., `jdoe`).

2. Click **Next** to proceed.

![image](https://github.com/user-attachments/assets/8a1f969e-c9f7-4e83-8cd6-f1c811d47651)

3. **Set Password**:
   - Enter a password for the new user in the **Password** and **Confirm password** fields.
   - Select the appropriate password options:
     - **User must change password at next logon** (recommended for security).
     - **User cannot change password**.
     - **Password never expires**.
     - **Account is disabled** (for accounts not yet ready for use).
   - Click **Next** to continue.


![image](https://github.com/user-attachments/assets/377636dd-4141-4629-80c6-01c0e1d8a912)


4. **Finish**:
   - Review the details and click **Finish** to create the new user account.

![image](https://github.com/user-attachments/assets/d8fe3504-c204-4fac-8833-149a713dc1b3)

---

## Step 4: Configure Additional User Properties (Optional)

Once the user account is created, you may want to configure additional properties.

1. **Right-click** the newly created user account and select **Properties**.

2. **Common Properties to Configure**:
   - **General**: Modify contact details such as phone number and email.
   - **Account**: Set logon hours, account expiration, and logon workstations.
   - **Profile**: Configure user profile paths, logon scripts, and home folder paths.
   - **Organization**: Specify job title, department, and company.

3. Click **OK** to save any changes.

---

## Step 5: Test the New User Account

1. **Log Out** or use a different device to log in with the new account.
2. Enter the **username** and **password** for the new user account.
3. Ensure that the user is prompted to change their password if you selected that option during setup.

---

## Additional Notes

- **Organizational Units**: Creating OUs can help you manage users by grouping them logically, which is useful for setting group policies.
- **Security**: Regularly review user permissions and follow best practices for password policies.
---

## Additional Notes

- **User Groups**: Adding users to specific groups determines their access permissions. Ensure you understand the purpose of each group and grant the user the appropriate access level.
- **Active Directory**: If you’re managing multiple users across a domain, Active Directory simplifies user management and centralizes control over user access.

---

### Conclusion

You have successfully created and configured a new user account in **Active Directory** on **Windows Server 2022**. This setup ensures centralized management and security for user accounts within your network. Managing user accounts is an essential part of server administration, and now you have the tools to efficiently create and manage them.
