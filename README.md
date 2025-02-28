
## Active Directory Security Testing Lab

This project is focused on setting up an **Active Directory** environment and performing various penetration testing techniques to explore and exploit vulnerabilities within the system. The main goal is to develop a deeper understanding of **Active Directory**'s security flaws by applying practical hands-on attacks. So far, **LMNR (Link-Local Multicast Name Resolution)** and **SMB Replay** attacks have been explored, and additional attacks will be added as the project progresses.

---

## Project Objectives:
- Set up a fully functional **Active Directory** environment using a **Windows Server 2019** domain controller and **Windows 10 Enterprise** user machines.
- Perform the **LMNR (Link-Local Multicast Name Resolution)** attack to intercept network communications and gain unauthorized access to sensitive information.
- Execute the **SMB Replay Attack** to exploit SMB vulnerabilities, understanding its potential impact on the Active Directory network.
- Explore and document additional attacks, including **IPv6** and other common penetration techniques, as I move forward in the project.

---

## Prerequisites:
- Basic understanding of **Active Directory** and **networking concepts**.
- A system capable of running virtual machines to set up the lab (VMware/VirtualBox).
- Administrative access to configure **Active Directory** and perform security testing.

---

## Project Files:

### 1. **SetupActiveDirectory.md**:
This comprehensive file walks you through the process of setting up your own **Active Directory** environment. It includes step-by-step instructions for creating the domain controller, configuring user machines, and connecting them to the domain. Follow this guide to replicate the lab setup in your environment.

### 2. **LMNRAttack.md**:
This file contains detailed instructions on how to perform the **LMNR (Link-Local Multicast Name Resolution)** attack. It explains how attackers can exploit LMNR in an Active Directory network to intercept and manipulate communications, allowing unauthorized access to sensitive data.

### 3. **SMBReplayAttack.md**:
In this file, you will find an in-depth guide on performing the **SMB Replay Attack**. It covers how SMB authentication weaknesses can be exploited, helping you understand the impact on the Active Directory network and how attackers can gain unauthorized access.

---

## Future Additions:
- Testing additional attacks such as **Pass-the-Hash**, **Kerberos Ticket Attacks**, and more.
- Providing detailed, step-by-step guides and scripts for replicating attacks in a controlled, virtualized environment.

---

**Note:** This repository serves as an ongoing lab to explore and document attacks on **Active Directory**. As I move forward, new attacks will be added, and existing techniques will be further explored and improved.

