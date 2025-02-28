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


## Mitigation Strategies:

To protect against SMB relay attacks, implement the following mitigations:
- **Use SMB signing**: Enforce the use of SMB signing to verify that SMB packets come from a trusted source.
- **Disable SMBv1**: SMBv1 is an outdated protocol that is vulnerable to various attacks, including relay attacks. Ensure it is disabled in your environment.
- **Use strong authentication mechanisms**: Implement multi-factor authentication (MFA) and secure SMB configurations to prevent unauthorized access.

By following these steps, you'll be able to execute the SMB relay attack and also understand the risks involved in such attacks.
