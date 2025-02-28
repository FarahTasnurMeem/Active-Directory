# Hacking Active Directory

## Setting up Active Directory
---

Hello! Today, I am setting up a lab for Active Directory. I have a **Windows Server 2019** acting as my domain controller and two **Windows 10 Enterprise** machines as user machines. One machine is assigned to **Peter Parker**, and the other to **Frank Castle**.

### Lab Setup:
1. **Windows Server 2019** (Domain Controller)
2. **Windows 10 Enterprise** (Machine 1)
3. **Windows 10 Enterprise** (Machine 2)

### Minimum Requirements:
- **60 GB Disk Space**
- **16 GB RAM**

## Installation
---

Install the machines using **VMware** or **VirtualBox**. I am using the free version of **VMware Workstation Pro**. Below are the recommended settings for the virtual machines:  
(*Note: It's suggested to disable the floppy disk since it's unnecessary for Windows.*)

![VM Settings 1](https://github.com/user-attachments/assets/31080a4a-5aa9-4445-a509-24538497e76b)  
![VM Settings 2](https://github.com/user-attachments/assets/8feaaab0-2423-4ce7-b25d-f28c071075cf)  
![VM Settings 3](https://github.com/user-attachments/assets/01cdc2da-a693-457a-a310-a372512db347)

## Settings in Kali
---

1. Install **Pimpmykali**:  
   [https://github.com/Dewalt-arch/pimpmykali](https://github.com/Dewalt-arch/pimpmykali)  
   (*I installed it in my `/opt` folder.*)

## Active Directory Domain Controller Setup (Windows Server 2019)
---

### Renaming the PC:
- To rename the PC, search and view your PC name in the system settings:  
   ![PC Rename](https://github.com/user-attachments/assets/9d0e298a-fd29-4e17-9f2c-880ffd4706cd)

### Installing Active Directory Domain Services:
1. In **Server Manager**, click **Manage**, select **Add Roles and Features**, choose **Server Roles**, select **Active Directory Domain Services**, and click **Install**.

   ![AD DS Installation](https://github.com/user-attachments/assets/a1f726ef-f542-43b3-a7c6-b8c4749694cb)

2. After installation, click the popped-up notification. In the **Deployment Configuration**, select **Add a new forest**, enter **farah.local** as the root domain name, set a **DSRM Password**, click **Next**, and reboot your machine after completion.

   Once rebooted, it should show **Farah/Administrator**, indicating that you are logged in as the **Farah** domain's administrator. The password you set will work here.

   ![Domain Login](https://github.com/user-attachments/assets/f4a4a5e1-6bed-4bb4-a5e6-e7174b7eb9bd)

## Settings in Windows 10 Enterprise (Same settings for both machines)
---

1. Rename the machines. I've named one **"Sakib"** and the other **"Sara"**.

