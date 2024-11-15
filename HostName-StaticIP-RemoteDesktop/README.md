# How to Rename, Set a Static IP, and Enable Remote Desktop on Windows Server 2022

This guide walks you through the steps to **rename** your server, **set a static IP address**, and **enable Remote Desktop** on **Windows Server 2022**.

## Prerequisites

- A **Windows Server 2022** machine with **administrator privileges**.
- Basic knowledge of **Networking** and **Remote Desktop** features.

---

## Step 1: Rename the Server

Renaming the server involves changing the computer’s name, which will help with network management and identification.

1. **Open Server Manager**:
   - Click the **Start** button and open **Server Manager**.

2. **Access System Properties**:
   - In **Server Manager**, click on **Local Server** in the left-hand pane.
   - Under the **Properties** section, find **Computer Name** and click on the **hyperlinked** text (which will show the current server name).
  
     ![image](https://github.com/user-attachments/assets/d8cf2623-c4da-4a65-bdbd-b4ef0916f5ec)


3. **Rename the Server**:
   - The **System Properties** window will open. Click **Change**.
   - In the **Computer Name/Domain Changes** dialog, type the new name for your server in the **Computer name** field.
   - Click **OK** to apply the changes.

   ![image](https://github.com/user-attachments/assets/1bff5cf7-5186-434e-9fc1-623b7da6972e)


4. **Restart the Server**:
   - A prompt will appear asking you to restart the server for the changes to take effect. Click **OK** and restart the server.

  ![image](https://github.com/user-attachments/assets/17ba63cf-cfe2-4f0d-93fa-c67362bce818)

---

## Step 2: Set a Static IP Address

Assigning a static IP ensures that the server always uses the same IP address, which is important for network reliability.

1. **Open Network Connections**:
   - Right-click on the **Network Icon** in the taskbar (bottom-right corner).
   - Select **Open Network & Internet Settings**.

![image](https://github.com/user-attachments/assets/122f1f38-1a54-4406-a07a-dddea97d29d1)

   - In the window that opens, click **Change adapter options**.

     ![image](https://github.com/user-attachments/assets/8a2fd518-85be-4a23-8f1e-112e05f7c042)


1. **Configure the Network Adapter**:
   - Right-click on the network adapter you are using (e.g., **Ethernet**) and select **Properties**.

![image](https://github.com/user-attachments/assets/e16d7959-579d-4c2e-8fea-e842cc8c64e7)


   - In the **Ethernet Properties** window, select **Internet Protocol Version 4 (TCP/IPv4)** and click **Properties**.

1. **Assign a Static IP**:
   - In the **Internet Protocol Version 4 (TCP/IPv4) Properties** window, select **Use the following IP address**.
   - Enter the **Static IP Address**, **Subnet Mask**, and **Default Gateway** (if applicable for your network):
     - **IP Address**: Example: `192.168.1.100` (Change this based on your network range).
     - **Subnet Mask**: Typically `255.255.255.0`.
     - **Default Gateway**: The IP address of your router (e.g., `192.168.1.1`).
   - Under **Use the following DNS server addresses**, enter the DNS server addresses (e.g., for your local DNS `127.0.0.1` or a public DNS like Google's  `8.8.8.8`).
   - Click **OK** to save the settings.
  
![image](https://github.com/user-attachments/assets/0559696e-2df7-432a-9a0b-579d43bdddf9)


---

## Step 3: Enable Remote Desktop

Remote Desktop allows you to access your server remotely, which is crucial for server management.

1. **Open Server Manager**:
   - Click the **Start** button and open **Server Manager**.

2. **Navigate to Local Server**:
   - In **Server Manager**, click on **Local Server** in the left-hand pane.

3. **Enable Remote Desktop**:
   - Under **Properties**, locate the **Remote Desktop** section. Click on the **Disabled** link (this will open the **System Properties** window).

     
   ![image](https://github.com/user-attachments/assets/b6994e79-4f89-4208-bc03-f694d04e5c15)


   - In the **System Properties** window, select the **Remote** tab.
   - Under **Remote Desktop**, choose **Allow remote connections to this computer**.
   - Optionally, if you are in a domain environment, select **Allow connections only from computers running Remote Desktop with Network Level Authentication** for added security.
   - Click **Apply**, then **OK**.


     ![image](https://github.com/user-attachments/assets/22b5aca7-61fb-45c2-a557-19153542098d)


4. **Verify Firewall Settings**:
   - Ensure that the **Windows Defender Firewall** allows Remote Desktop connections. In most cases, this is enabled by default when you enable Remote Desktop.
   - You can verify this by going to **Control Panel > System and Security > Windows Defender Firewall > Allow an app or feature through Windows Defender Firewall** and ensuring that **Remote Desktop** is checked.

---

## Step 4: Test the Configuration

After completing the steps above, you can test that everything is working correctly.

![image](https://github.com/user-attachments/assets/044090d2-b4a6-4738-b0cb-d4838553fde9)


1. **Test the Static IP**:
   - Open **Command Prompt** and type the following command to ensure the static IP is set correctly:
     ```bash
     ipconfig
     ```
   - Verify that the IP address listed is the one you assigned earlier.
  
     ![image](https://github.com/user-attachments/assets/aff842e0-66c4-4917-bbbd-fd74f465bf19)


2. **Test Remote Desktop**:
   - From another computer, open the **Remote Desktop Connection** application.
   - Enter the **IP Address** of your Windows Server 2022 machine (e.g., `192.168.1.100`) and click **Connect**.
   - Enter the **administrator credentials** to log in remotely.

---

## Additional Notes

- **Static IP**: Ensure the static IP you assigned does not conflict with other devices on your network. You may want to configure it outside of the DHCP range to avoid IP conflicts.
- **Remote Desktop**: If you're connecting from a different network, you may need to configure port forwarding (TCP port 3389) on your router/firewall.

---

### Conclusion

You’ve successfully renamed your server, set a static IP address, and enabled Remote Desktop on **Windows Server 2022**. This setup allows for more stable network management and convenient remote access for administrative tasks.
