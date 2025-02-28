## Setting up Active Directory
---

In this file, I will guide you through the process of setting up an **Active Directory** environment using **Windows Server 2019** as the domain controller and **Windows 10 Enterprise** as the client machines. This lab setup will serve as the foundation for a series of penetration testing exercises, where you'll learn to exploit vulnerabilities and secure Active Directory networks.

The primary goal of this setup is to create a controlled environment where various attacks on Active Directory can be tested. By following this guide, you’ll gain hands-on experience, deepen your understanding of how Active Directory functions, learn how to secure it, and explore how attackers may exploit its vulnerabilities.

---

## Lab Environment:

- **Domain Controller**: Windows Server 2019 (Active Directory Domain Controller)
- **Client Machines**: Windows 10 Enterprise (Two machines for user setup)

The following sections will walk you through the detailed steps to install and configure your Active Directory lab, set up the domain controller, create users, and configure domain policies.

---

## Prerequisites:

- Virtualization software (VMware or VirtualBox)
- Basic understanding of **Active Directory** and **networking**
- Administrative access to configure **Windows Server 2019** and **Windows 10** machines

---

Hello! Today, I am setting up a lab for Active Directory with the following setup:
- A **Windows Server 2019** acting as the domain controller.
- Two **Windows 10 Enterprise** machines acting as user machines. One machine is assigned to **Peter Parker**, and the other to **Frank Castle**.

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

2. **Setup Active Directory Domain Services**:  
   - In **Server Manager**, click **Manage**, select **Add Roles and Features**, choose **Server Roles**, and select **Active Directory Domain Services**. Click **Install**.

   ![AD DS Installation](https://github.com/user-attachments/assets/a1f726ef-f542-43b3-a7c6-b8c4749694cb)

3. **Domain Setup**:  
   - Click the popped-up notification, then in **Deployment Configuration**, select **Add a new forest**, enter `farah.local` as the root domain name, set a **DSRM Password**, click **Next**, and reboot your machine after completion.

   - After reboot, it will show **Farah/Administrator**, indicating you're logged in as the **Farah** domain administrator. The password used for this login will still work.

   ![Domain Login](https://github.com/user-attachments/assets/f4a4a5e1-6bed-4bb4-a5e6-e7174b7eb9bd)

## Settings in Windows 10 Enterprise (Same settings in both machines)
------------------------
- Rename the machines. I have named one **"Sakib"** and the other **"Sara"**.

## Set up Users, Groups, and Policies in Domain Controller
------
1. In **Server Manager**, click **Tools** and select **Active Directory Users and Computers** to manage users/groups and **Group Policy Management** to configure policies.

2. You can see my domain controller is named **Meem** (as I named my PC for Windows Server 2019).

   ![Domain Controller Meem](https://github.com/user-attachments/assets/c9c3e191-5755-44f0-9c47-ab8a9dc11174)

3. I created a new **Organizational Unit (OU)** called **Groups** under **Farah.local**. Here, except for **Administrator** and **Guest**, I transferred all users to this folder.

   ![Organizational Unit](https://github.com/user-attachments/assets/25c568c7-ee7f-4b0d-8320-d3736c2fbd89)

4. You can edit all user information from here:

   ![User Info](https://github.com/user-attachments/assets/0eea9b07-7cef-47b2-b1c3-ed539228a856)

5. To create new users, follow the steps shown below:

   ![Creating New User](https://github.com/user-attachments/assets/426dc528-2ac5-40fb-88a6-3c53690f065f)

6. In the image above, you can see my users; **Tony Stark** is the domain admin and a member of all groups (since we copied from the administrator), while **Frank Castle** and **Peter Parker** are normal users.

   ![Users Overview](https://github.com/user-attachments/assets/7b780efe-3f95-4139-be93-7320e1ce9869)  
   ![User Details](https://github.com/user-attachments/assets/440ee4f5-af60-4bd4-9e9b-43d4e0941c84)

7. I also created a fake SQL account by copying from **Tony Stark** (although this is a bad practice).

   ![SQL Account](https://github.com/user-attachments/assets/49e1eae7-c336-4757-99e6-89c157cb68ee)

### Share Files and Services
------
1. Go to **Files and Services**, click on **Shares**, and at the top, click **Share** then **SMB Share Quick**. I named the Share **Hackme**.

2. I enabled **SMB** by opening ports **139** and **445** on the domain controller. This way, we can scan it later. Perform the same configuration on the other machines as well.

   ![SMB Share](https://github.com/user-attachments/assets/97dca761-46d1-49cf-a4a9-3c41f7f929dc)

## Setup the SQL Services
------
1. Open **Cmd** and run the following command:

   ![SQL Command](https://github.com/user-attachments/assets/bfe8c083-4bd3-4888-8b64-a0d1259712d2)

   ```bash
   setspn -a HYDRA-DC/SQLService.Farah.local:60111 Farah\SQLService


## Set up Group Policy
------
To disable **Windows Defender** via Group Policy:

1. Search **Group Policy** and run it as Administrator.
2. Create a new **GPO** in the **Farah.local** domain and name it **Disable Windows Defender**.

![GPO Creation](https://github.com/user-attachments/assets/e4284ac5-fbaf-4b50-a69f-eb7b6f769f07)

3. Right-click **Windows Defender**, go to **Edit**, and navigate to:  
**Computer Configuration → Administrative Templates → Windows Components → Windows Defender Antivirus → Turn off Windows Defender Antivirus** → Set to **Enabled** → **Apply**.

![Windows Defender Settings](https://github.com/user-attachments/assets/95edc00e-4a7d-456a-b403-2eafb09f6f9d)  
![Policy Applied](https://github.com/user-attachments/assets/349cf94b-022d-4762-b2cd-2d2ef1fe9de5)

## Joining Machines to the Domain
------
1. On the Windows 10 machine, create a folder named **Share**. Right-click on the folder → **Properties** → **Sharing** → **Share**, and share everything.
2. Go to **Network Access** → **Open Internet and Network Access** → **Change Network Adapter** → Right-click **Ethernet** → **Properties** → Set the **Preferred DNS Server** to the domain controller's IP.

![Network Settings](https://github.com/user-attachments/assets/2b499f07-b636-4c1a-8c73-1041c0c6e8a9)

3. Search for **Domain**, then click **Connect** and join the device to the local active directory. Enter the domain name (e.g., **Farah.local**) and credentials, then finish the process.

![Join Domain](https://github.com/user-attachments/assets/b8891885-08e8-47b6-81d7-a509728af4a8)

### Final Result:
------
Now, you can log in as **Administrator** on the user machines (Windows 10 Enterprise). Try logging in as **Frank Castle** and promote him to **Admin** on that machine. Do the same for the second machine by logging in as **Peter Parker** and making him an admin there. You can also log in as **Farah/Administrator** on both machines.

## Checking Connected Users/Devices to the Active Directory
------
You can view the connected users and devices to the active directory using the **Active Directory Users and Computers** tool.

![Connected Devices](https://github.com/user-attachments/assets/c99c2e39-b36a-428b-a5a4-5920a2b904e9)
