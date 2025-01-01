# Hydra-Project
<h1>Using Hydra to Hack into an Insecure VM</h1>

<h2>Description</h2>
This project demonstrates how to utilize Hydra, a popular penetration testing tool, to brute-force SSH credentials and gain access to an insecure Ubuntu virtual machine (VM) from an attacker VM. The walkthrough highlights the use of wordlists, specific Hydra flags, and basic post-exploitation steps to interact with the compromised VM.

<h2>Languages and Utilities Used</h2>

- Hydra
- SSH
- Nano

<h2>Environments Used</h2>

- Insecure Ubuntu VM (target)
- Kali Linux (attacker VM)

<h2>Lab Walk-through:</h2>

<p align="center">
1. Identifying the target VM: The IP address of the insecure Ubuntu machine (right) is noted. <br/>
<img src="https://i.ibb.co/kKKLzd2/image-1.png" height="80%" width="80%" alt="Target VM IP Address"/>
<br />
<br />
2. Attempting to gain SSH access: <br/>
<img src="https://i.ibb.co/brfGCGs/image-3.png" height="80%" width="80%" alt="SSH Attempt"/>
<br />
<br />
3. Login failed due to incorrect password: <br/>
<img src="https://i.ibb.co/qxmhSd3/image-4.png" height="80%" width="80%" alt="SSH Login Failure"/>
<br />
<br />
4. Using Hydra to brute-force the password: Hydra can brute-force SSH passwords using wordlists. A wordlist is a file containing a list of possible passwords, and Kali Linux conveniently comes with pre-installed wordlists like `rockyou.txt`. <br/>
<img src="https://i.ibb.co/m4GBKHv/image-5.png" height="80%" width="80%" alt="Hydra Setup"/>
<br />
<br />
5. Configuring Hydra parameters:  
   - `-l` specifies the login name (`vboxuser`).  
   - `-P` points to the wordlist (`rockyou.txt`).  
   - `-V` enables verbose mode to show details of each attempt.  
   - `-I` ensures Hydra starts from the beginning of the wordlist.  
   - `-F` stops Hydra after finding the correct password.  
<br/>
<img src="https://i.ibb.co/T22M3bt/image-6.png" height="80%" width="80%" alt="Hydra Command"/>
<img src="https://i.ibb.co/n3dTrhz/image-7.png" height="80%" width="80%" alt="Hydra Process"/>
<img src="https://i.ibb.co/zHsX8Nc/image-8.png" height="80%" width="80%" alt="Hydra Progress"/>
<br />
<br />
6. Successful password discovery: Hydra finds the correct password, which is `password`. <br/>
<img src="https://i.ibb.co/FVmmJGY/image-9butbetter.png" height="80%" width="80%" alt="Password Found"/>
<br />
<br />
7. Gaining SSH access to the Ubuntu machine: Using the discovered password, SSH access is established. <br/>
<img src="https://i.ibb.co/9g32kts/image-11.png" height="80%" width="80%" alt="SSH Access"/>
<br />
<br />
8. Exploring the compromised VM: Navigating the filesystem and creating a file (`hello.txt`). <br/>
<img src="https://i.ibb.co/4s5XWD2/image-12.png" height="80%" width="80%" alt="Logged In"/>
<img src="https://i.ibb.co/pjqqSQN/image-13.png" height="80%" width="80%" alt="File Creation"/>
<img src="https://i.ibb.co/KWFJ11C/image-14.png" height="80%" width="80%" alt="File Created"/>
<br />
<br />
9. Editing the created file using Nano: Verifying changes are reflected on the target VM. <br/>
<img src="https://i.ibb.co/ydNzZG7/image-16.png" height="80%" width="80%" alt="File Editing"/>
<img src="https://i.ibb.co/C55MHgP/image-17.png" height="80%" width="80%" alt="Nano Usage"/>
<img src="https://i.ibb.co/r7HcgJ7/image-18.png" height="80%" width="80%" alt="File Modified"/>
<br />
<br />
</p>
<h2>Conclusion</h2>
This demonstration showcases the effectiveness of Hydra as a penetration testing tool for brute-forcing SSH credentials. By leveraging wordlists such as `rockyou.txt`, we successfully gained unauthorized access to the insecure Ubuntu VM. This emphasizes the importance of using strong, unique passwords and implementing security measures like rate-limiting and multi-factor authentication to mitigate brute-force attacks. The steps post-compromise also highlight how attackers can manipulate files once access is obtained, further underscoring the need for robust system security practices.
