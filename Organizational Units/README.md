# How to Create Organizational Units (OUs) on Windows Server 2022

This guide walks you through the steps to create **Organizational Units (OUs)** on **Windows Server 2022** using the **Active Directory Users and Computers (ADUC)** tool.

## Prerequisites

- A **Windows Server 2022** machine with **Active Directory Domain Services (AD DS)** installed.
- **Administrator privileges** to manage Active Directory.
- Basic understanding of **Active Directory** and **Organizational Units**.

---

## Step 1: Open Active Directory Users and Computers (ADUC)

1. **Open Server Manager**:
   - Click the **Start** button and open **Server Manager**.

2. **Launch ADUC**:
   - In **Server Manager**, click on **Tools** in the top-right corner.
   - Select **Active Directory Users and Computers** from the dropdown. This will open the **ADUC** management console.

---

## Step 2: Navigate to the Domain

1. **Expand the Domain**:
   - In the **ADUC** console, under the **Active Directory Users and Computers** section, find and expand your domain by clicking the arrow next to your domain name.
   - You should see several default containers like **Users**, **Computers**, and **Domain Controllers**.

2. **Select the Parent Container**:
   - Right-click the domain or an existing container where you want to create the new OU (for example, **Users** or directly under the domain name) and select **New** > **Organizational Unit**.

---

## Step 3: Create the Organizational Unit (OU)

1. **Define the OU Name**:
   - In the **New Object - Organizational Unit** window, type a name for the new OU (e.g., `Finance`, `HR`, `Sales`, etc.).
   - You can also set an optional **description** for the OU.

2. **Set Permissions (Optional)**:
   - Optionally, you can choose to protect the OU from accidental deletion by checking the **Protect object from accidental deletion** box.
   - Click **OK** to create the OU.

---

## Step 4: Verify the OU Creation

1. **Check the New OU**:
   - You should now see the new OU listed under your domain or the container you chose. Expand the domain or container to verify that the OU has been successfully created.

2. **View the OU Properties (Optional)**:
   - Right-click on the newly created OU and select **Properties** to modify settings, such as delegation of control or managing object security within the OU.

---

## Step 5: Move or Create Objects within the OU

1. **Move Existing Objects**:
   - To move users, computers, or groups into the new OU, right-click on an object (e.g., a user or computer) in the **Active Directory Users and Computers** console.
   - Select **Move**, choose the newly created OU, and click **OK**.

2. **Create New Objects in the OU**:
   - Right-click on the new OU and select **New** to create objects like **User**, **Group**, or **Computer** inside the OU.
   - Follow the prompts to complete the object creation.

---

## Additional Notes

- **Organizational Units (OUs)** are containers within Active Directory that help organize and manage resources in a domain. They provide a way to delegate control over specific groups of objects (users, groups, computers).
- **OU Structure**: Plan your OU structure carefully, as it helps in applying Group Policies (GPOs) and delegating administrative permissions.
- **Protection**: Use the **Protect object from accidental deletion** feature to prevent OUs from being mistakenly deleted.

---

## License

This guide is licensed under the [MIT License](LICENSE).

---

### Conclusion

You’ve successfully created an **Organizational Unit (OU)** on **Windows Server 2022**. Organizational Units help organize and manage Active Directory objects efficiently, making it easier to apply policies and delegate administrative tasks.

