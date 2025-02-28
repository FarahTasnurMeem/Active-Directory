# LLMNR Poisoning

**LLMNR (Link-Local Multicast Name Resolution)** poisoning is a common attack method where an attacker on the same network can poison the LLMNR cache, leading to credential theft or Man-in-the-Middle (MitM) attacks. This technique exploits the **LLMNR** protocol, which is used by Windows to resolve hostnames in the absence of DNS servers.

In this section, I will walk you through the steps of performing an **LLMNR poisoning attack** and show how an attacker can capture and crack password hashes, enabling them to access sensitive information. I will also explain the best mitigation strategies to secure your network against such attacks.

---

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
