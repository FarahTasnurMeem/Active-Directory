# SMB Relay Attack

### Relay Attacks:
This section outlines the steps for performing an **SMB Relay Attack** to exploit vulnerabilities in the SMB protocol. The goal is to relay authentication requests to gain unauthorized access to network resources.

---

### 1. Check if the network allows sharing:
Before proceeding, ensure that the network is configured to allow file sharing via SMB. This step is crucial for the attack to work, as SMB sharing must be enabled for the attack to succeed.

---

### 2. Set the IP of the target (Peter's machine):
Next, set the IP address of the target machine (Peter's machine) in the `target.txt` file. This file will store the target information used for the SMB relay attack.

Example of setting the target IP:

--------------

![Image](https://github.com/user-attachments/assets/d7f2b8f1-7df7-414c-855d-4f1f0c92688f)

---

### 3. Turn off SMB and HTTP on the target machine:
To ensure that the relay attack proceeds correctly, disable SMB and HTTP services on the target machine temporarily. This action ensures that the SMB requests will be relayed to the attacker, allowing the attack to exploit the authentication process.

You can disable SMB and HTTP by using the following steps:
- **SMB**: Disable via `services.msc` or through command-line management tools.
- **HTTP**: Disable IIS or Apache services (if applicable).

![Image](https://github.com/user-attachments/assets/1a3ba50d-4a8f-4b93-85a9-3b155f7c6b25)

---
### 4. Perform the relay attack:
After configuring the target and disabling the necessary services, proceed with initiating the SMB relay attack. This step intercepts the SMB authentication request and relays it to the attacker machine, allowing unauthorized access.

Once the attack is successful, you will capture the hash from the intercepted SMB authentication request. This hash can then be used for further exploitation, such as cracking the password or performing pass-the-hash attacks.

![Image](https://github.com/user-attachments/assets/7387ea27-9de6-436a-85ad-affcc7100a5a)
*Here, the screenshot shows that the hash has been successfully captured from the SMB relay attack.*

---

### Next Steps:
Once the hash is captured, you can use tools like **John the Ripper** or **Hashcat** to crack the password associated with the hash, gaining unauthorized access to the system.

---

## Mitigation Strategies:
To defend against SMB relay attacks, consider implementing the following strategies:

1. **Disable SMBv1**: SMBv1 is vulnerable to relay attacks. Ensure that SMBv2 or SMBv3 is enabled and SMBv1 is disabled across all systems.
   - To disable SMBv1, use the following command:
     ```bash
     sc config lanmanworkstation depend= bowser/mrxsmb20/nsi
     sc config mrxsmb10 start= disabled
     ```
   
2. **Use SMB Signing**: Enable SMB signing to help prevent attackers from tampering with SMB communication. This can be configured via group policy settings.
   
3. **Implement Network Segmentation**: Separate critical systems and resources from general network access. This limits the exposure of sensitive systems to potential attacks.
   
4. **Enable Windows Defender Firewall**: Configure firewall rules to restrict SMB traffic to only trusted machines, reducing the risk of attack from external systems.
   
5. **Require Mutual Authentication**: Enforce mutual authentication to ensure that both the client and server authenticate each other before the session begins.
   
6. **Patch Vulnerabilities Regularly**: Regularly update and patch systems to address known vulnerabilities that could be exploited for relay attacks.
   
7. **Use VPNs for Remote Access**: Require the use of Virtual Private Networks (VPNs) for secure remote access, ensuring encrypted communications that cannot be easily intercepted or relayed.


By following these steps, you'll be able to execute the SMB relay attack and also understand the risks involved in such attacks.
