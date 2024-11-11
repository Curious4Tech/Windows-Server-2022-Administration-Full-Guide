# How to Install and Set Up IIS on Windows Server 2022

This guide walks you through the steps to **install** and **set up** **IIS (Internet Information Services)** on **Windows Server 2022**.

## Prerequisites

- A **Windows Server 2022** machine with **administrator privileges**.
- A basic understanding of **web servers** and **IIS**.

---

## Step 1: Install IIS (Internet Information Services)

1. **Open Server Manager**:
   - Click the **Start** button and open **Server Manager**.

2. **Add Roles and Features**:
   - In **Server Manager**, click **Manage** in the top-right corner and then select **Add Roles and Features**.

3. **Start the Wizard**:
   - The **Add Roles and Features Wizard** will open. Click **Next** to proceed.

4. **Select Installation Type**:
   - In the **Installation Type** section, select **Role-based or feature-based installation** and click **Next**.

5. **Select the Destination Server**:
   - Choose the server on which you want to install IIS (the local server is selected by default). Click **Next**.

6. **Select Server Roles**:
   - In the **Select server roles** section, check **Web Server (IIS)**.
   - A prompt will appear to install additional features required for IIS. Click **Add Features**.
   - Click **Next**.


![image](https://github.com/user-attachments/assets/51d91980-e049-4259-a167-b932454bddb8)


7. **Select Features**:
   - In the **Select features** section, you can add additional features, but the default selection for **Web Server (IIS)** is sufficient for most use cases. Click **Next**.

8. **Select Role Services**:
   - In the **Select role services** section, you can choose specific IIS services you want to install. The default options are generally sufficient. For a basic IIS installation, leave the default selections and click **Next**.

9. **Confirm Installation**:
   - Review your selections and click **Install** to start the installation process.
   - The installation may take a few minutes to complete.

![image](https://github.com/user-attachments/assets/3f528e2b-1e53-4dab-85ba-298d4d69f094)

10. **Complete the Installation**:
    - Once the installation is complete, click **Close**.

![image](https://github.com/user-attachments/assets/7c58d78d-efb8-4ba9-8190-e8f1377c6a63)

---

## Step 2: Verify IIS Installation

1. **Open IIS Manager**:
   - To confirm IIS was installed successfully, click the **Start** button and search for **IIS Manager**.
   - Open the **Internet Information Services (IIS) Manager** application.

![image](https://github.com/user-attachments/assets/61ce1a2a-3711-4c07-a486-0a46318a590d)


2. **Verify IIS Server is Running**:
   - In **IIS Manager**, under **Connections**, you should see your server name listed. This confirms that IIS is installed and running.


![image](https://github.com/user-attachments/assets/7f382dff-abad-425b-8b24-084bfa5623b3)

3. **Test IIS**:
   - Open a web browser and type `http://localhost` in the address bar. You should see the **IIS Welcome Page**, which confirms that the web server is up and running.


![image](https://github.com/user-attachments/assets/6e8a1f2b-ec19-4708-a694-f83d4501e491)

---

## Step 3: Configure IIS (Optional)

If you want to set up a basic website, you can do so by following these steps:

1. **Create a New Website**:
   - In **IIS Manager**, right-click **Sites** in the left-hand pane and select **Add Website**.

2. **Configure Website Settings**:
   - **Site Name**: Enter a name for your site (e.g., `MyWebsite`).
   - **Physical Path**: Select the folder that contains your website's files (e.g., `C:\inetpub\wwwroot\MyWebsite`).
   - **Binding**: Choose the IP address and port for your site (default is `http://*:80` for HTTP traffic).

3. **Set Permissions**:
   - Ensure that the correct permissions are set for the website folder to allow the web server to access the files.

4. **Start the Website**:
   - Click **OK** to create the site. The site will now appear under **Sites** in **IIS Manager**. Right-click on it and select **Start** to launch the website.


![image](https://github.com/user-attachments/assets/dac5d2c8-0ece-474a-a144-ebd020e8dbaf)

5. **Test Your Website**:
   - Open a web browser and enter your domain name in the address bar (e.g., `wwww.contonso.com`). You should see the website you configured.

![image](https://github.com/user-attachments/assets/cb872041-b440-4491-b55b-4f18248514ba)

---

## Step 4: Configure Firewall (Optional)

If you need to allow access to your IIS server from other computers, ensure that the **Windows Firewall** allows HTTP and HTTPS traffic.

1. **Open Windows Defender Firewall**:
   - Go to **Control Panel** > **System and Security** > **Windows Defender Firewall**.

2. **Allow an App or Feature**:
   - On the left-hand side, click **Allow an app or feature through Windows Defender Firewall**.

3. **Enable Web Traffic**:
   - Scroll down and ensure that **World Wide Web Services (HTTP)** and **World Wide Web Services (HTTPS)** are allowed through both private and public networks.
   - Click **OK** to save the changes.

---

## Step 5: Monitor IIS (Optional)

You can use **IIS Manager** to monitor the status of your server and websites:

1. **Check Site Health**:
   - In **IIS Manager**, you can see the status of all your sites under **Sites**. Ensure that the **Status** is set to **Started**.

2. **Check Logs**:
   - IIS keeps logs of all requests made to your server. To check these logs, navigate to the **Logging** section under the site’s settings in **IIS Manager**.
   - You can view, filter, and analyze the logs to troubleshoot or monitor activity.

---

## Additional Notes

- **IIS Features**: IIS comes with many additional features that can be enabled based on your needs, including SSL encryption, authentication, URL rewriting, and more.
- **Permissions**: Be sure to set proper permissions for files and directories to ensure your websites are secure.
- **Website Content**: Ensure that the website content is properly configured, and test the website regularly to ensure uptime and accessibility.

---

### Conclusion

You have successfully installed and configured **IIS** on **Windows Server 2022**. You can now host websites, manage web applications, and ensure secure, reliable service for users accessing your server via the web.

