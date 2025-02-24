# Hacking-Active-Directory

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










