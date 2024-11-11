# How to Install and Configure Hyper-V on Windows Server 2022

This guide walks you through the steps to **install** and **configure Hyper-V** on **Windows Server 2022**.

## Prerequisites

- A **Windows Server 2022** machine with **administrator privileges**.
- A **64-bit processor** with support for hardware-assisted virtualization (Intel VT-x or AMD-V) and **SLAT** (Second Level Address Translation).
- At least **4 GB of RAM** (8 GB or more recommended for virtualized environments).
- Ensure that the **Hyper-V** feature is supported and the hardware virtualization settings are enabled in the BIOS/UEFI.

---

## Step 1: Install Hyper-V Feature

Hyper-V is not enabled by default in Windows Server 2022, so you will need to install the feature manually.

### Using Server Manager

1. **Open Server Manager**:
   - Click the **Start** button and open **Server Manager**.

2. **Add Roles and Features**:
   - In **Server Manager**, click **Manage** in the top right corner, then select **Add Roles and Features**.

3. **Role-Based Installation**:
   - Select **Role-based or feature-based installation** and click **Next**.

4. **Select the Server**:
   - Choose the server where you want to install Hyper-V (it will likely be pre-selected). Click **Next**.

5. **Select Hyper-V Role**:
   - In the **Roles** section, check the box next to **Hyper-V**.
   - Click **Next**.

6. **Add Features**:
   - A dialog will pop up asking if you want to add the **Hyper-V management tools** (recommended). Click **Add Features**, then click **Next**.

7. **Hyper-V Installation Options**:
   - In the **Hyper-V** window, click **Next**.
   - The system will display information about the Hyper-V features, including network virtualization options and storage configurations. Click **Next**.

8. **Confirm Installation Selections**:
   - Review your selections and click **Install**. The installation process will begin.

9. **Restart the Server**:
   - After the installation is complete, you will be prompted to restart the server. Click **Close** and restart the server for changes to take effect.

---

## Step 2: Enable Hyper-V Virtualization Features in BIOS/UEFI

1. **Enter BIOS/UEFI**:
   - Reboot the server and press the appropriate key (usually **F2**, **F10**, or **Delete**) to enter the BIOS/UEFI firmware settings.

2. **Enable Virtualization**:
   - Look for an option like **Intel VT-x**, **Intel Virtualization Technology**, or **AMD-V** (depending on your processor type).
   - Enable the **Intel VT-x** (or **AMD-V**) option if it is disabled.
   - Additionally, enable **Intel VT-d** or **IOMMU** (if applicable) for better performance with Hyper-V.

3. **Save and Exit**:
   - Save the changes and exit the BIOS/UEFI settings. The system will continue to boot into Windows Server.

---

## Step 3: Verify Hyper-V Installation

To confirm that Hyper-V is properly installed:

1. **Open PowerShell**:
   - Right-click the **Start** button and select **Windows PowerShell (Admin)** to open PowerShell with administrative privileges.

2. **Check Hyper-V Status**:
   - Run the following command to check the status of Hyper-V:
     ```powershell
     Get-WindowsFeature -Name Hyper-V
     ```
   - If Hyper-V is installed successfully, you will see `Installed` next to the **Hyper-V** feature.

3. **Check Hyper-V Virtualization Support**:
   - Run the following command to ensure that your processor supports virtualization:
     ```powershell
     systeminfo
     ```
   - Look for the line that says **Hyper-V Requirements**. It should say `Yes` for the necessary features like **VM Monitor Mode Extensions**, **Virtualization Enabled in Firmware**, etc.

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

3. **Configure Virtual Switch**:
   - After creating the virtual switch, you can configure it. Select the newly created switch and choose which network adapter on the physical server it will bind to.
   - Click **OK** to apply the changes.

---

## Step 5: Create a Virtual Machine (VM)

1. **Open Hyper-V Manager**:
   - In **Hyper-V Manager**, click **New** in the right pane and select **Virtual Machine** to start the **New Virtual Machine Wizard**.

2. **VM Configuration**:
   - **Specify Name and Location**: Give your VM a name (e.g., `TestVM`) and specify a location for the VM files.
   - **Assign Memory**: Set the amount of **RAM** for the VM (e.g., 2 GB or more depending on the operating system).
   - **Configure Networking**: Select the virtual switch you created earlier.
   - **Create a Virtual Hard Disk**: Create a new virtual hard disk (VHD) with a size suitable for the VM.
   - **Install Operating System**: Choose to install the OS from an ISO file, network boot (PXE), or a physical DVD.

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

---

## Additional Notes

- **Performance Considerations**: Ensure that the host server has enough resources (CPU, RAM, storage) to run virtual machines effectively.
- **Hyper-V Integration Services**: For best performance, install **Integration Services** on the virtual machine. This includes drivers and services for improved communication between the host and VM.

---

## License

This guide is licensed under the [MIT License](LICENSE).

---

### Conclusion

You have successfully installed and configured **Hyper-V** on **Windows Server 2022**. Hyper-V allows you to run multiple virtual machines on a single physical server, offering a flexible and efficient virtualization platform for your workloads.

