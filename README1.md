# Hydra SSH Brute Force Attack Lab

## Overview

This project demonstrates how to use **Hydra**, a widely used password-cracking tool in penetration testing, to brute-force SSH credentials and gain access to an insecure Ubuntu virtual machine.

The lab simulates a common attack scenario where an attacker attempts to gain unauthorized access to a system using a password wordlist. The exercise highlights how weak passwords and lack of brute-force protections can lead to system compromise.

---

## Tools Used

- **Hydra** – brute-force password cracking tool
- **SSH** – remote login protocol
- **Nano** – text editor used for post-exploitation verification
- **rockyou.txt** – common password wordlist

---

## Lab Environment

| Machine | Role |
|------|------|
| Kali Linux VM | Attacker |
| Ubuntu VM | Target (intentionally insecure) |

---

# Walkthrough

## 1. Identifying the Target Machine

The IP address of the vulnerable Ubuntu VM is identified so the attacker machine can target it.

<p align="center">
<img src="screenshots/image1.pngimage 1.png" width="80%">
</p>

---

## 2. Attempting Initial SSH Access

An SSH login attempt is made using known credentials. This fails because the correct password is unknown.




<p align="center">
<img src="screenshots/image 3.png" width="80%">
</p>

---

## 3. Login Failure

The system rejects the login attempt due to an incorrect password.

<p align="center">
<img src="screenshots/image4.png" width="80%">
</p>

---

## 4. Launching a Hydra Brute-Force Attack

Hydra is used to attempt many passwords automatically using a wordlist.

Example command:



### Hydra Flags Explained

| Flag | Purpose |
|-----|------|
| `-l` | Specifies the username |
| `-P` | Specifies the password wordlist |
| `-V` | Enables verbose output |
| `-I` | Starts from the beginning of the wordlist |
| `-F` | Stops once a valid password is found |

<p align="center">
<img src="screenshots/image5.png" width="80%">
</p>

---

## 5. Hydra Brute-Force Process

Hydra begins systematically testing passwords from the wordlist.

<p align="center">
<img src="screenshots/image6.png" width="80%">
</p>

<p align="center">
<img src="screenshots/image7.png" width="80%">
</p>

<p align="center">
<img src="screenshots/image8.png" width="80%">
</p>

---

## 6. Password Successfully Discovered

Hydra eventually finds the correct password:



<p align="center">
<img src="screenshots/image9.png" width="80%">
</p>

---

## 7. Gaining SSH Access

Using the discovered credentials, the attacker successfully logs into the target machine via SSH.




<p align="center">
<img src="screenshots/image11.png" width="80%">
</p>

---

## 8. Post-Exploitation: Accessing the System

After gaining access, the attacker can interact with the filesystem.

Example:



<p align="center">
<img src="screenshots/image12.png" width="80%">
</p>

<p align="center">
<img src="screenshots/image13.png" width="80%">
</p>

<p align="center">
<img src="screenshots/image14.png" width="80%">
</p>

---

## 9. Editing Files with Nano

The attacker edits the newly created file using Nano.



<p align="center">
<img src="screenshots/image16.png" width="80%">
</p>

<p align="center">
<img src="screenshots/image17.png" width="80%">
</p>

<p align="center">
<img src="screenshots/image18.png" width="80%">
</p>

---

# Security Takeaways

This exercise demonstrates how easily systems can be compromised when weak passwords are used.

Important defenses against brute-force attacks include:

- Using **strong, unique passwords**
- Implementing **account lockout policies**
- Enabling **rate limiting**
- Deploying **multi-factor authentication (MFA)**
- Monitoring for suspicious login activity

---

# Educational Purpose

This project was conducted in a **controlled lab environment for educational purposes only**. The techniques demonstrated are intended to help understand vulnerabilities and improve defensive security practices.



