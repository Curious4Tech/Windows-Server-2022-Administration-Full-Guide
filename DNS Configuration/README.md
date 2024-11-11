# How to Set Up a DNS Server on Windows Server 2022

This guide will help you install and configure a **DNS Server** on **Windows Server 2022**.

## Prerequisites

- A **Windows Server 2022** machine with **administrator privileges**.
- A static IP address for your server (recommended for DNS servers).
- A basic understanding of DNS concepts.

---

## Step 1: Install the DNS Server Role

1. Open **Server Manager** on your Windows Server 2022.
2. In the **Server Manager** window, click on **Manage** and select **Add Roles and Features**.
3. In the **Add Roles and Features Wizard**, click **Next** until you reach the **Select Server Roles** page.
4. On the **Select Server Roles** page, check the box for **DNS Server**.
5. Click **Next** and proceed through the wizard until you reach the **Confirm Installation Selections** page.
6. Click **Install** to begin the installation process.
7. Once the installation is complete, click **Close**.
If already installed while installing **AD DS**, skip the **Step 1**.
---

## Step 2: Open DNS Manager

1. In **Server Manager**, click on **Tools** in the top right corner.

![image](https://github.com/user-attachments/assets/b413ee16-84db-4d0b-95e4-d2a81082b396)

3. Select **DNS** from the drop-down list to open the **DNS Manager**.

---

## Step 3: Configure the DNS Server

### 3.1: Set Up Forward Lookup Zones

A **forward lookup zone** allows the DNS server to resolve domain names to IP addresses.

1. In **DNS Manager**, right-click on **Forward Lookup Zones** and select **New Zone**.
2. In the **New Zone Wizard**, click **Next**.
3. Select the **Primary zone** option and click **Next**.
4. On the next page, select the **This server only** option and click **Next**.
5. Enter the **Zone Name** (e.g., `example.com`), and click **Next**.
6. Choose the **Do not allow dynamic updates** option (or select **Allow both non-secure and secure dynamic updates** if you want to enable dynamic updates), then click **Next**.
7. Click **Finish** to complete the zone creation.

### 3.2: Add DNS Records

Now that the zone is created, you can add DNS records to map domain names to IP addresses.

1. In **DNS Manager**, right-click on the zone you just created and select **New Host (A or AAAA)**.
2. In the **New Host** window, enter the **Name** (e.g., `www` for `www.example.com`) and the corresponding **IP Address** (e.g., `192.168.1.100`).
3. Click **Add Host** to create the DNS record.

Repeat this process to add more records for other hostnames or services.

---

## Step 4: Configure Reverse Lookup Zones (Optional)

A **reverse lookup zone** allows the DNS server to resolve IP addresses to domain names.

1. In **DNS Manager**, right-click on **Reverse Lookup Zones** and select **New Zone**.
2. Follow the same steps as for forward lookup zones, but this time specify the **IP network** for which you want to create a reverse lookup zone (e.g., `192.168.1.x`).
3. Complete the wizard by clicking **Next** and **Finish**.

---

## Step 5: Test the DNS Server

### 5.1: Use nslookup to Test Forward Lookup

1. Open **Command Prompt** on any client machine in your network.
2. Type the following command:
   ```
   nslookup www.example.com
   ```
3. You should receive the corresponding IP address that you set in the DNS record.

### 5.2: Test Reverse Lookup

1. In **Command Prompt**, type the following command (replace `192.168.1.100` with an IP in your reverse zone):
   ```
   nslookup 192.168.1.100
   ```
2. You should receive the associated domain name for that IP address (e.g., `www.example.com`).

---

## Step 6: Set the DNS Server on Client Machines

1. Open **Network and Sharing Center** on the client machine.
2. Click **Change adapter settings**.
3. Right-click the network connection, and select **Properties**.
4. Select **Internet Protocol Version 4 (TCP/IPv4)** and click **Properties**.
5. Set the **Preferred DNS Server** to the IP address of your Windows Server 2022 DNS server.
6. Click **OK** to apply the settings.

---

## Additional Notes

- Ensure your firewall allows traffic on **UDP/53** (DNS).
- For DNS to function correctly in a larger network, you may need to configure secondary DNS servers or forwarders for external resolution.

---

## License

This guide is licensed under the [MIT License](LICENSE).

---

### Conclusion

You’ve now set up a DNS server on Windows Server 2022. This configuration will allow devices in your network to resolve domain names and IP addresses efficiently.
