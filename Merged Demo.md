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

**Settings in active directory Domain controller ( windows Server 2019:**
------
• Rename you PC by search view your PC name 
![image](https://github.com/user-attachments/assets/9d0e298a-fd29-4e17-9f2c-880ffd4706cd)

• In windows Server 2019, setup active directory domain services.  
• In Server Manager, click Manage, select Add Roles and Features, choose Server Roles, select Active Directory Domain Services, and click Install.
![image](https://github.com/user-attachments/assets/a1f726ef-f542-43b3-a7c6-b8c4749694cb)
• Click the popped-up notification, then in Deployment Configuration, select Add a new forest,I entered farah.local as the root domain name, set a DSRM Password, click Next, and reboot your machine after completion.
• Now its showing me Farah/Administrator which means its logging as domain of Farah as the administrator. Here, the password I have been using will still work.
![image](https://github.com/user-attachments/assets/f4a4a5e1-6bed-4bb4-a5e6-e7174b7eb9bd)

**Settings in  windows 10 enterprize ( Same setting in both machines):*
------------------------
• Rename the machines, I have named one of my Machines "Sakib" and the other one "Sara".

**Set up Users,Groups and Policies in Domain Controller:**
• In Server Manager, click Tools and select Active Directory Users and Computers to manage users/groups, and Group Policy Management to configure policies.
• You can see my domain controller is meem since I named my pC name for windows server 2019 is meem
 ![image](https://github.com/user-attachments/assets/c9c3e191-5755-44f0-9c47-ab8a9dc11174)
 • Now I can see list of in Us secuirty in Users under Farah.local, Here I would like to create a new group. So right click in Farah.local Select New -> Organizational Unit and name it groups.Here, except administrator and Guest I am transfering all to the folder groups.
 ![image](https://github.com/user-attachments/assets/25c568c7-ee7f-4b0d-8320-d3736c2fbd89)
• You can edit all information from here
![image](https://github.com/user-attachments/assets/0eea9b07-7cef-47b2-b1c3-ed539228a856)
• Now lets create new users
![image](https://github.com/user-attachments/assets/426dc528-2ac5-40fb-88a6-3c53690f065f)
• In the image above, you can see my users; Tony Stark is the domain admin and a member of all groups, just like the administrator (since we copied from the administrator), while Frank Castle and Peter Parker are normal users. 
![image](https://github.com/user-attachments/assets/7b780efe-3f95-4139-be93-7320e1ce9869)
![image](https://github.com/user-attachments/assets/440ee4f5-af60-4bd4-9e9b-43d4e0941c84)
I also Created a Fake SQl Account coping from Tony Stark.(Its a bad practice)
![image](https://github.com/user-attachments/assets/49e1eae7-c336-4757-99e6-89c157cb68ee)

• Now go to files and Services, Click on shares, at the top click on Share then SMB share Quick, I named the Share me as Hackme.
•  I did this because most domain controllers have files shares, I want to open port 139 and 445 so that I have SMB enables in this domain controller, so We can scan against it. Do the same in other machines as well.
![image](https://github.com/user-attachments/assets/97dca761-46d1-49cf-a4a9-3c41f7f929dc)

**Setup the SQl Services:**
Open Cmd and run this command: 
![image](https://github.com/user-attachments/assets/bfe8c083-4bd3-4888-8b64-a0d1259712d2)
1. setspn-a HYDRA-DC/SQLService.Farah.local:60111 Farah\SQLService
2. T Farah.local -Q */*

**Set up Group Policy:** 
Lets turn off windows Defender. 
1. Search group policy and run as administrator
2. Create a GPO in the domain Farah.local and name it disable windows defender.
![image](https://github.com/user-attachments/assets/e4284ac5-fbaf-4b50-a69f-eb7b6f769f07)
3. Right Click Windows Defender -> Edit -> Computer Condiguration -> administrative templates -> windows Component -> Windows Defender Anitvirus -> Turn off windows Defender Antivirus -> enabled -> Apply
![image](https://github.com/user-attachments/assets/95edc00e-4a7d-456a-b403-2eafb09f6f9d)
![image](https://github.com/user-attachments/assets/349cf94b-022d-4762-b2cd-2d2ef1fe9de5)


**Joining our machines to the domain: ** 
-----------
1. Go to this PC and make a folder named share. Right click the folder -> Properties -> Click Sharing -> Share , Now share everything. 
2. click on the network acess -> open internet and network access -> Click change network adapter , Right click on ethnet -> Select Properties,
3.  Click Internet Protocol 4 and Put the Ip of the domain controller in Prefered DNS Server.
![image](https://github.com/user-attachments/assets/2b499f07-b636-4c1a-8c73-1041c0c6e8a9)

4. Search Domain then Click Connect -> join this device to a local active directory.
5. Here put the Domain name of the domain controller  in join a domain (for me its Farah.local) , enter username and password and there you have it
![image](https://github.com/user-attachments/assets/b8891885-08e8-47b6-81d7-a509728af4a8)

Final Result: 
1. Now You can login as admin in the user machines(windows enterprise 10), try logging in as Frank Castle and make Fcastle an admin in that machine , do the same for the 2nd machine login as Peter parker and make sure to make peter an admin there. You can also login as Farah/Administrator in both machines. 

**Checking Connected Users/devices to the active directory:**
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



