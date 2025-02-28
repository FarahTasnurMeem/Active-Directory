# Hacking-Active-Directory

# Active Directory Security Testing Lab

This project focuses on setting up an **Active Directory** environment and performing various penetration testing techniques to explore vulnerabilities within the system. The main goal is to develop a deep understanding of the security flaws within **Active Directory** through practical hands-on attacks, including **LMNR** and **SMB Replay** attacks, as well as future exploration of **IPv6** vulnerabilities.

---

## Project Objectives:
- Set up a functional **Active Directory** environment with a **Windows Server 2019** domain controller and **Windows 10 Enterprise** user machines.
- Perform the **LMNR (Link-Local Multicast Name Resolution)** attack to intercept network communication and gain unauthorized access.
- Execute the **SMB Replay Attack** to exploit SMB vulnerabilities and understand its impact on the Active Directory network.
- Explore and document other attacks such as **IPv6** and additional common penetration techniques.

---

## Prerequisites:
- Basic understanding of Active Directory and networking concepts.
- A system capable of running virtual machines for lab setup (VMware/VirtualBox).
- Administrative access to configure and manipulate **Active Directory** and perform security testing.

---

## Project Files:

### 1. **SetupActiveDirectory.md**:
This file contains detailed instructions on setting up your own **Active Directory** environment. It includes step-by-step guidance for creating the domain controller, configuring user machines, and connecting them to the domain. Follow this to replicate a similar lab setup.

### 2. **LMNRAttack.md**:
Here, you will find the steps and techniques for conducting the **LMNR (Link-Local Multicast Name Resolution)** attack. This file walks you through how LMNR can be exploited in an Active Directory network to intercept and manipulate communications.

### 3. **SMBReplayAttack.md**:
This file provides a detailed guide on performing the **SMB Replay Attack**. It explains how to exploit weaknesses in SMB authentication to gain unauthorized access and execute attacks on the Active Directory network.

### 4. **FutureExplorations.md** (Coming Soon):
This file will be updated with further experiments and attacks you can try in your Active Directory lab, including **IPv6** attack strategies, **Pass-the-Hash**, **Kerberos Ticket Attacks**, and more.

---

## Future Additions:
- Testing additional attacks like **Pass-the-Hash**, **Kerberos Ticket Attacks**, and more.
- Detailed step-by-step guides and scripts for replicating the attacks in a controlled environment.
  
---
