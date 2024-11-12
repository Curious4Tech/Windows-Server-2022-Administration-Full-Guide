# How to Install and Configure Hyper-V on Windows Server 2022

This guide walks you through the steps to **install** and **configure Hyper-V** on **Windows Server 2022**.

## Prerequisites

- A **Windows Server 2022** machine with **administrator privileges**.
- A **64-bit processor** with support for hardware-assisted virtualization (Intel VT-x or AMD-V) and **SLAT** (Second Level Address Translation).
- At least **4 GB of RAM** (8 GB or more recommended for virtualized environments).
- Ensure that the **Hyper-V** feature is supported and the hardware virtualization settings are enabled in the BIOS/UEFI.

---

## Step 1: Verify Host System Compatibility with Nested Virtualization (Required if using Hyper-V or other virtualization software)

   - Nested virtualization requires a compatible processor (Intel processors with VT-x and AMD processors with AMD-V).
   - This guide assumes your host machine is running Windows Server 2016 or later, or Windows 10 or later, with Hyper-V enabled.
     
### Shut Down the VM

   - Go to **Hyper-V Manager** on your host machine.
   - Locate the **Windows Server 2022 VM** where you want to enable nested virtualization.
   - Right-click on the VM and select **Shut down** or **Turn off**.

### Enable Nested Virtualization on the VM

  - With the **VM turned off**, open PowerShell on the host system and run the following command:
```bash
Set-VMProcessor -VMName "YourVMName" -ExposeVirtualizationExtensions $true

```
Replace **`YourVMName`** with the name of your Windows Server 2022 virtual machine.


![image](https://github.com/user-attachments/assets/eed5d74b-1343-46a8-b7b0-90a039bb6de2)


### Configure MAC Address Spoofing

MAC address spoofing is required to allow network communication when nested virtualization is enabled. Run the following PowerShell command on the host machine:

```bash
Set-VMNetworkAdapter -VMName "YourVMName" -MacAddressSpoofing On

```
Replace **`YourVMName`** with the name of your Windows Server 2022 virtual machine.


![image](https://github.com/user-attachments/assets/b63e4a65-d91f-4527-9810-5f6b859cc711)

 - Go back to **Hyper-V Manager** and **start** the **Windows Server 2022 VM** where nested virtualization is now enabled.
 
 ---
 
### Step 2 : Install Hyper-V Feature

Hyper-V is not enabled by default in Windows Server 2022, so you will need to install the feature manually.

### Using Server Manager

1. **Open Server Manager**:
   - Click the **Start** button and open **Server Manager**.

2. **Add Roles and Features**:
   - In **Server Manager**, click **Manage** in the top right corner, then select **Add Roles and Features**.


![image](https://github.com/user-attachments/assets/4770d659-3a78-4ac3-93dc-18a6203deb8a)


3. **Role-Based Installation**:
   - Select **Role-based or feature-based installation** and click **Next**.

4. **Select the Server**:
   - Choose the server where you want to install Hyper-V (it will likely be pre-selected). Click **Next**.

5. **Select Hyper-V Role**:
   - In the **Roles** section, check the box next to **Hyper-V**.
   

   ![image](https://github.com/user-attachments/assets/ae53a08c-747a-4de8-865b-cd89b651fc49)


6. **Add Features**:
   - A dialog will pop up asking if you want to add the **Hyper-V management tools** (recommended). Click **Add Features**, then click **Next**.


![image](https://github.com/user-attachments/assets/82615c3f-dc8d-4659-bd8d-a40721773c24)


7. **Hyper-V Installation Options**:
   - In the **Hyper-V** window, click **Next**.
   - The system will display information about the Hyper-V features.
   - Configure network virtualization options **(Virtual Switch)** and then click **Next**.

![image](https://github.com/user-attachments/assets/c3d59e91-bf17-45a4-a402-d78dbd79f6a6)

   -  Configure the **Migration** option and then click **Next**.


![image](https://github.com/user-attachments/assets/621f692e-5130-499f-b452-4e275e06124f)

   -  Set up storage configurations. 


![image](https://github.com/user-attachments/assets/87af21bd-62b7-4807-a09b-883d87282d80)


8. **Confirm Installation Selections**:
   - Review your selections and click **Install**. The installation process will begin.

![image](https://github.com/user-attachments/assets/7829ae8e-3336-4f86-b1a8-9bcf86c1ac7b)

9. **Restart the Server**:
   - After the installation is complete, you will be prompted to restart the server. Click **Close** and restart the server for changes to take effect.

---

## Step 4: Verify Hyper-V Installation

To confirm that **Hyper-V** is properly installed:

1. **Open PowerShell**:
   - Right-click the **Start** button and select **Windows PowerShell (Admin)** to open PowerShell with administrative privileges.

2. **Check Hyper-V Status**:
   - Run the following command to check the status of Hyper-V:
     ```powershell
     Get-WindowsFeature -Name Hyper-V
     ```
   - If Hyper-V is installed successfully, you will see **`Installed`** next to the **Hyper-V** feature.


![image](https://github.com/user-attachments/assets/ac6ff145-4dfa-43af-ace5-444558d3b41c)


3. **Check Hyper-V Virtualization Support**:
   - Run the following command to ensure that your processor supports virtualization:
     ```powershell
     systeminfo
     ```
   - Look for the line that says **Hyper-V Requirements**. It should say **`Yes`** for the necessary features like **VM Monitor Mode Extensions**, **Virtualization Enabled in Firmware**, etc.


![image](https://github.com/user-attachments/assets/431dfb4c-d734-4e11-96dd-5f9c94a57cc9)

---

## Step 4: Create and Configure Virtual Switch

To create a **Virtual Switch** in Hyper-V, follow these steps:

1. **Open Hyper-V Manager**:
   - Open the **Start** menu, search for **Hyper-V Manager**, and click to open it.

2. **Create Virtual Switch**:
   - In **Hyper-V Manager**, in the right-hand pane, click **Virtual Switch Manager**.
   - In the **Virtual Switch Manager**, select **New virtual network switch** on the left side.
   - Choose the type of virtual switch you want to create:
     - **External**: Allows VMs to access external networks (recommended for most use cases).
     - **Internal**: Allows VMs to communicate with each other and the host.
     - **Private**: Allows VMs to communicate only with each other.
   - Click **Create Virtual Switch** after selecting the type.


![image](https://github.com/user-attachments/assets/22413e4f-f1fe-433b-a20e-439baf7c7e45)


3. **Configure Virtual Switch**:
   - Give a name to the virtual switch (e.g, `First switch`). Select the newly created switch and choose which network adapter on the physical server it will bind to.
   - Click **Apply** to apply the changes and then click on **OK** to finish the setup.


![image](https://github.com/user-attachments/assets/ffd5db56-84cf-466c-8211-a0f3887820b0)

---

## Step 5: Create a Virtual Machine (VM)

1. **Open Hyper-V Manager**:
   - In **Hyper-V Manager**, click **New** in the right pane and select **Virtual Machine** to start the **New Virtual Machine Wizard**.

2. **VM Configuration**:
   - **Specify Name and Location**: Give your VM a name (e.g., `TestVM`) and specify a location for the VM files.


![image](https://github.com/user-attachments/assets/a36a78ff-848c-4095-a9e3-0f26f61652c3)


   - **Assign Memory**: Set the amount of **RAM** for the VM (e.g., 2 GB or more depending on the operating system).


![image](https://github.com/user-attachments/assets/39d4541c-8eaf-44f6-8cef-a1bae6aabc52)


   - **Configure Networking**: Select the virtual switch you created earlier.


![image](https://github.com/user-attachments/assets/9749a42a-bedb-420e-8b1c-73a3c2ca8a33)


   - **Create a Virtual Hard Disk**: Create a new virtual hard disk (VHD) with a size suitable for the VM.


![image](https://github.com/user-attachments/assets/6f2f2f5f-fe19-40d8-9c4d-9ab8ad03218d)


   - **Install Operating System**: Choose to install the OS from an ISO file, network boot (PXE), or a physical DVD.


![image](https://github.com/user-attachments/assets/c10d439a-f959-4a0d-b964-6cd3dafc7afd)


3. **Finish the VM Setup**:
   - Review your settings and click **Finish** to create the VM.

---

## Step 6: Start and Connect to the Virtual Machine

1. **Start the Virtual Machine**:
   - In **Hyper-V Manager**, select your newly created VM and click **Start** to power it on.

2. **Connect to the VM**:
   - Right-click the VM and select **Connect**. This will open the VM in a separate window where you can interact with it just like a physical computer.

3. **Install the Operating System**:
   - Follow the installation prompts to install the desired operating system on the virtual machine.


![image](https://github.com/user-attachments/assets/b323fd2b-f6be-4deb-8e72-2c8997a6a0ad)

---

## Additional Notes

- **Performance Considerations**: Ensure that the host server has enough resources (CPU, RAM, storage) to run virtual machines effectively.
- **Hyper-V Integration Services**: For best performance, install **Integration Services** on the virtual machine. This includes drivers and services for improved communication between the host and VM.

---
### Conclusion

You have successfully installed and configured **Hyper-V** on **Windows Server 2022**. Hyper-V allows you to run multiple virtual machines on a single physical server, offering a flexible and efficient virtualization platform for your workloads.

