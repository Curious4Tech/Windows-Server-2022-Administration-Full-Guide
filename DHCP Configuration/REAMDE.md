# DHCP Server Setup on Windows Server 2022

This guide provides step-by-step instructions for setting up a DHCP (Dynamic Host Configuration Protocol) server on **Windows Server 2022**, including optional steps for IP exclusions (or IP reservation).

## Prerequisites

- A running instance of **Windows Server 2022**.
- Administrator access to the server.

---

## Step 1: Install the DHCP Server Role

1. Open **Server Manager**.
2. Click **Manage** > **Add Roles and Features**.
3. In the **Add Roles and Features Wizard**, click **Next** until you reach the **Select Server Roles** page.
4. Check **DHCP Server** and click **Next**.

   
![image](https://github.com/user-attachments/assets/d99afbba-1a30-4d1a-ac1e-384bee0b5541)

5. Proceed through the wizard, confirming selections by clicking on **Add features**, and click **Install**.
6. Once installation is complete, click **Close**.


![image](https://github.com/user-attachments/assets/59629917-73f7-4c9e-a125-d0a4f1eadceb)

---

## Step 2: Configure the DHCP Server

1. In **Server Manager**, click the **Notifications** flag at the top, then select **Complete DHCP configuration**.


![image](https://github.com/user-attachments/assets/2cc8f3db-20ce-48a6-b912-e175544936a0)

2. In the **DHCP Post-Install Configuration Wizard**, select **Commit** to authorize the DHCP server.


![image](https://github.com/user-attachments/assets/da1d126a-e1aa-4980-bd22-b3e2d9c80510)

3. Click **Close** to finish the configuration.

---

## Step 3: Open DHCP Management Console

1. In **Server Manager**, go to **Tools** and select **DHCP**.


![image](https://github.com/user-attachments/assets/9386a92e-2e82-41bc-95c0-15a38c2a8757)

2. Expand your server’s name and locate **IPv4** under the server node.

---

## Step 4: Create a New DHCP Scope

1. Right-click **IPv4** and select **New Scope**.


![image](https://github.com/user-attachments/assets/005c15f4-724c-4c04-91a5-4a34e2588469)

2. In the **New Scope Wizard**, enter a **Name** and **Description** for the scope, then click **Next**.
3. Specify the **IP Address Range** (e.g., Start IP: `192.168.1.100` to End IP: `192.168.1.200`). And specify the **Subnet mask**.
4. Click **Next**.


![image](https://github.com/user-attachments/assets/a9fd7134-3027-4d5f-aa55-72bfcda465af)


---

### Optional: Set IP Exclusions (IP Reservation)

- On the **Add Exclusions and Delay** page, you can specify IP addresses to **exclude** from the DHCP range.
- Enter the **Start** and **End IP** addresses for the range you want to exclude, then click **Add**.
- Click **Next**.


![image](https://github.com/user-attachments/assets/4cb439cd-b936-453d-86bd-a3a64e309d1f)


## Step 5: Set Lease Duration

1. Choose the **Lease Duration** (the default is 8 days).
2. Click **Next**.


![image](https://github.com/user-attachments/assets/edc887bc-8fc5-4ba8-ba2b-0f82b7731de7)

---

## Step 6: Configure DHCP Options

1. Choose **Yes, I want to configure these options now** and click **Next**.
2. Enter the **Default Gateway** (e.g., `192.168.1.1`) and click **Add**, then click **Next**.


![image](https://github.com/user-attachments/assets/dd4f859d-79b3-4bcb-8045-028547c1fb34)

3. Enter the **Domain Name** and **DNS Servers**. The DNS server should be the IP address of your DNS server (e.g., `192.168.1.2`). Click **Next**.

![image](https://github.com/user-attachments/assets/a8e4cea2-c021-4659-9a10-3f2927560447)

4. If you use WINS, configure the **WINS Servers**; otherwise, click **Next**.

---

## Step 7: Activate the Scope

1. Select **Yes, I want to activate this scope now**.
2. Click **Next**, then **Finish**.

Your new scope is active now.

![image](https://github.com/user-attachments/assets/fc2e4c53-45de-49ca-ba31-f3bcc7eb0cd6)

---

## (Optional) Step 8: Configure IP Reservations

1. In the **DHCP Console**, expand your scope and select **Reservations**.
2. Right-click **Reservations** and select **New Reservation**.
3. Enter a **Reservation Name**, the **IP Address** you want to reserve, the **MAC Address** of the device, and an optional **Description**.
4. Click **Add** to complete the reservation.


![image](https://github.com/user-attachments/assets/77c9f8f1-1012-4918-8a6d-3e56e194a12e)

---

## Step 9: Verify DHCP Functionality

1. Use a client device on the network to verify it receives an IP address within the scope.
2. On the client device, run the **`ipconfig /all`** command and ensure it receives the DHCP-assigned IP.

---

## Additional Notes

- The DHCP server should now be set up and operational, with IP exclusions or reservations as needed.
- Ensure that your network devices are configured to use DHCP for automatic IP assignment.

---
🎉 Congratulations! 🎉

You've successfully set up a DHCP Server on Windows Server 2022! This is a huge step toward mastering network management and automation. By completing this setup, you’ve learned how to efficiently manage IP addressing, which is critical in any networked environment.
