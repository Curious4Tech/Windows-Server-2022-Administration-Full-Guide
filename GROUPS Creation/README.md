# How to Create Groups on Windows Server 2022

This guide will walk you through the steps to **create groups** on **Windows Server 2022**. Groups are essential for organizing users and applying permissions to them efficiently.

## Prerequisites

- A **Windows Server 2022** machine with **administrator privileges**.
- Basic knowledge of **Active Directory** and **User Management**.

---

## Step 1: Open Active Directory Users and Computers

To create groups, you’ll need to access the **Active Directory Users and Computers** (ADUC) console.

1. **Open Server Manager**:
   - Click the **Start** button and open **Server Manager**.

2. **Access Active Directory Users and Computers**:
   - In **Server Manager**, click **Tools** in the top-right corner.
   - From the dropdown, select **Active Directory Users and Computers**.

---

## Step 2: Create a New Group

Once you're inside the **Active Directory Users and Computers** console, follow these steps to create a new group.

1. **Navigate to the Organizational Unit (OU)**:
   - In the **Active Directory Users and Computers** console, find the **Organizational Unit (OU)** where you want to create the group.
   - Right-click the OU, and choose **New** > **Group**.

2. **Enter Group Information**:
   - In the **New Object - Group** window:
     - **Group name**: Enter the name of the group (e.g., `HR_Department`).
     - **Group name (pre-Windows 2000)**: This will be automatically filled in, but you can modify it if necessary.
     - **Group scope**:
       - **Domain local**: Used for groups that are specific to a domain.
       - **Global**: Used for groups that can be assigned permissions within the domain.
       - **Universal**: Used for groups that can be assigned permissions in multiple domains.
     - **Group type**: Choose **Security** for groups used to assign permissions.
   
   - Click **OK** to create the group.

---

## Step 3: Add Members to the Group

After creating a group, you need to add members (users) to it.

1. **Select the Group**:
   - In the **Active Directory Users and Computers** console, navigate to the group you just created.

2. **Open the Group Properties**:
   - Right-click the group and select **Properties**.

3. **Add Members**:
   - In the **Group Properties** window, go to the **Members** tab.
   - Click **Add** to search for users or other groups to add to this group.
   - Enter the names of users or groups you want to add and click **OK**.

4. **Save Changes**:
   - After adding the members, click **Apply** and then **OK**.

---

## Step 4: Verify the Group

Once the group is created and members have been added, it’s important to verify that the group is functioning as expected.

1. **Verify the Group in Active Directory**:
   - In **Active Directory Users and Computers**, select the group and check the **Members** tab to ensure all members have been successfully added.

2. **Check Group Permissions**:
   - If you are using this group to manage permissions (e.g., for file shares or applications), verify that the group has the correct permissions assigned in the relevant locations (e.g., shared folders or applications).

---

## Additional Notes

- **Group Scope**:
   - **Domain Local** groups are used for assigning permissions within a single domain.
   - **Global** groups are typically used for user accounts within the same domain, but they can also be assigned permissions in other domains.
   - **Universal** groups can be used across multiple domains and are often employed in larger, multi-domain environments.
  
- **Group Types**:
   - **Security Groups**: Used to assign permissions and control access to resources.
   - **Distribution Groups**: Used for email distribution lists but do not grant security permissions.

---

## License

This guide is licensed under the [MIT License](LICENSE).

---

### Conclusion

You’ve successfully created a group on **Windows Server 2022**, added members to the group, and verified the setup. This process is essential for organizing users in your Active Directory environment and managing permissions effectively.

