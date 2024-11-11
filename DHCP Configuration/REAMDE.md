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
5. Proceed through the wizard, confirming selections, and click **Install**.
6. Once installation is complete, click **Close**.

---

## Step 2: Configure the DHCP Server

1. In **Server Manager**, click the **Notifications** flag at the top, then select **Complete DHCP configuration**.
2. In the **DHCP Post-Install Configuration Wizard**, select **Commit** to authorize the DHCP server.
3. Click **Close** to finish the configuration.

---

## Step 3: Open DHCP Management Console

1. In **Server Manager**, go to **Tools** and select **DHCP**.
2. Expand your server’s name and locate **IPv4** under the server node.

---

## Step 4: Create a New DHCP Scope

1. Right-click **IPv4** and select **New Scope**.
2. In the **New Scope Wizard**, enter a **Name** and **Description** for the scope, then click **Next**.
3. Specify the **IP Address Range** (e.g., Start IP: `192.168.1.100` to End IP: `192.168.1.200`).
4. Click **Next**.

---

### Optional: Set IP Exclusions (IP Reservation)

- On the **Add Exclusions and Delay** page, you can specify IP addresses to **exclude** from the DHCP range.
- Enter the **Start** and **End IP** addresses for the range you want to exclude, then click **Add**.
- Click **Next**.

---

## Step 5: Set Lease Duration

1. Choose the **Lease Duration** (the default is 8 days).
2. Click **Next**.

---

## Step 6: Configure DHCP Options

1. Choose **Yes, I want to configure these options now** and click **Next**.
2. Enter the **Default Gateway** (e.g., `192.168.1.1`) and click **Add**, then click **Next**.
3. Enter the **Domain Name** and **DNS Servers**. The DNS server should be the IP address of your DNS server (e.g., `192.168.1.2`). Click **Next**.
4. If you use WINS, configure the **WINS Servers**; otherwise, click **Next**.

---

## Step 7: Activate the Scope

1. Select **Yes, I want to activate this scope now**.
2. Click **Next**, then **Finish**.

---

## (Optional) Step 8: Configure IP Reservations

1. In the **DHCP Console**, expand your scope and select **Reservations**.
2. Right-click **Reservations** and select **New Reservation**.
3. Enter a **Reservation Name**, the **IP Address** you want to reserve, the **MAC Address** of the device, and an optional **Description**.
4. Click **Add** to complete the reservation.

---

## Step 9: Verify DHCP Functionality

1. Use a client device on the network to verify it receives an IP address within the scope.
2. On the client device, run the **`ipconfig /all`** command and ensure it receives the DHCP-assigned IP.

---

## Additional Notes

- The DHCP server should now be set up and operational, with IP exclusions or reservations as needed.
- Ensure that your network devices are configured to use DHCP for automatic IP assignment.

---

## License

This guide is licensed under the [MIT License](LICENSE).

