# Hacking-Active-Directory

**Seting up Active Directory**
---------

 Hi, Today I am going to set my lab for active directory. Here, I have a windows server 2019 as my domain controller, and two machines windows 10 enterprise as my users. One of the machines, I have allocated to peter parker and another one to Frank castle. 
 
• Lab
1 Windows Server 2019
2 Windows 10 Enterprise (Machine 1)
3. WIndows 10 Enterprise (Machine 2) 
Requirements (minimum)
• 60 GB Disk Space
• 16 GB RAM

**Installation: **

Install machines in vmware or vitualbox. I am using the new free version of Vmware workstation pro. Below are the setting you want for your machines: 
(I suggest not keeping the floppy disk since its an extra in windows)
![image](https://github.com/user-attachments/assets/31080a4a-5aa9-4445-a509-24538497e76b)
![image](https://github.com/user-attachments/assets/8feaaab0-2423-4ce7-b25d-f28c071075cf)
![image](https://github.com/user-attachments/assets/01cdc2da-a693-457a-a310-a372512db347)

**Settings In Kali:**
-------------
1. Install Pimpmykali : https://github.com/Dewalt-arch/pimpmykali (I installed in my opt folder)

**Start setting up our active directory Domain controller ( windows Server 2019:**
------
• Rename you PC by search view your PC name 
![image](https://github.com/user-attachments/assets/9d0e298a-fd29-4e17-9f2c-880ffd4706cd)

• In windows Server 2019, setup active directory domain services. 
• In Server Manager, click Manage, select Add Roles and Features, choose Server Roles, select Active Directory Domain Services, and click Install.
![image](https://github.com/user-attachments/assets/a1f726ef-f542-43b3-a7c6-b8c4749694cb)
• Click the popped-up notification, then in Deployment Configuration, select Add a new forest,I entered farah.local as the root domain name, set a DSRM Password, click Next, and reboot your machine after completion.









**Connected Users/devices to the active directory:**
![image](https://github.com/user-attachments/assets/c99c2e39-b36a-428b-a5a4-5920a2b904e9)

**LLMNR Poisoning:** 
----------------------------------------------
![image](https://github.com/user-attachments/assets/06da6b8c-7536-4fc8-bb3e-83adb0b13f11)

Finding the Hash:
----------------------------
![image](https://github.com/user-attachments/assets/206f8562-5f5a-4589-bbc3-9f695981527b)
from:
![image](https://github.com/user-attachments/assets/48393623-fc22-42d4-83ab-d2effa75b2a6)

Cracking the hash:
------------------------------
Note: 
![image](https://github.com/user-attachments/assets/ff43987f-db9a-46ce-9166-b99b419ed069)

Cracked Password is here:
-------------------------------
![image](https://github.com/user-attachments/assets/4997b66f-d12f-4ab6-8b6a-d72034514810)
![image](https://github.com/user-attachments/assets/3e5ab67c-043d-4d9f-a56f-cb6deb318b4d)

# Mitigation Strategies for LLMNR & NBT-NS Poisoning

## Disable LLMNR and NBT-NS (Recommended)

The best defense against LLMNR and NBT-NS poisoning is to disable these protocols.

## Why Disable LLMNR and NBT-NS?

When a system attempts to resolve a hostname, it first queries **DNS**.  
- If **DNS fails** to recognize the hostname, the system falls back to **LLMNR** (Link-Local Multicast Name Resolution).  
- If **LLMNR does not respond**, the system then attempts to resolve the name using **NBT-NS** (NetBIOS Name Service).  

This fallback behavior makes LLMNR and NBT-NS vulnerable to **poisoning attacks**, where an attacker on the same network can respond with a malicious IP address, leading to credential theft or Man-in-the-Middle (MitM) attacks.

### Disable LLMNR:
1. Open the **Group Policy Editor** (`gpedit.msc`).
2. Navigate to:  Local Computer Policy > Computer Configuration > Administrative Templates > Network > DNS Client
3. Set **"Turn OFF Multicast Name Resolution"** to **Enabled**.

### Disable NBT-NS:
1. Open **Network Connections**.
2. Go to **Network Adapter Properties**.
3. Select **TCP/IPv4 Properties** > **Advanced** tab > **WINS** tab.
4. Choose **"Disable NetBIOS over TCP/IP"**.

## Alternative Mitigation Strategies

If disabling LLMNR/NBT-NS is not feasible, implement the following:

- **Enforce Network Access Control (NAC)** to restrict unauthorized devices.
- **Require Strong Passwords:**
- Use passwords **longer than 14 characters**.
- Avoid common words to prevent easy hash cracking.

By implementing these mitigations, you can significantly reduce the risk of LLMNR/NBT-NS poisoning attacks.

**Relay Attacks:**
---------------------------
1. Check if the network is allowing to share.
2. Set ip of peter in target.txt ![image](https://github.com/user-attachments/assets/d7f2b8f1-7df7-414c-855d-4f1f0c92688f)

3. Turn off SMB and HTTP
![image](https://github.com/user-attachments/assets/1a3ba50d-4a8f-4b93-85a9-3b155f7c6b25)

4.![image](https://github.com/user-attachments/assets/231402a1-c536-4984-8f95-2a8fa64d8a0e)


![image](https://github.com/user-attachments/assets/147f752a-bdbb-43c5-bd18-e0b4db414014)









