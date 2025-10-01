# Linux Forensics

![Room Banner](https://github.com/user-attachments/assets/3729a007-4203-447a-9a2b-0c6ec3baae46)

## 📋 Overview

We just finished Windows Forensics part 1 and 2, now we are moving on to Linux. Unlike Windows, I have no experience in finding artifacts in Linux, so I may struggle here. That being said, I also had no experience using some tools in the entire training module and I seem to be doing well. Let's hope this one won't give me too hard of a time.

## 👥 Task 3: OS and account information

### **Q1: Which two users are the members of the group audio?**

I modified the example code given in the reading to help format it nicely for us. `cat /etc/group | column -t -s :`

![Group Members](https://github.com/user-attachments/assets/893388ac-c458-4204-b824-da3e213daf11)

**Answer: `ubuntu, pulse`**

### **Q2: In the attached VM, there is a user account named tryhackme. What is the uid of this account?**

I used the following command that was found in the reading, `cat /etc/passwd | column -t -s :`. This help gave me a list of users on the machine. Now we just need to look for the account and the corresponding UID.

![User UID](https://github.com/user-attachments/assets/374c89a3-12c9-47b9-822d-38cd0bc7323f)

**Answer: `1001`**

### **Q3: A session was started on this machine on Sat Apr 16 20:10. How long did this session last?**

For this one, I used the last command to help display login information. `last -f /var/log/wtmp`

![Session Duration](https://github.com/user-attachments/assets/1301e47b-a713-4ef0-a688-547a6d3d4659)

**Answer: `01:32`**

## ⚙️ Task 4: System Configuration

### **Q1: What is the hostname of the attached VM?**

I typed `cat /etc/hostname` as per the reading and the terminal will output the hostname.

![Hostname](https://github.com/user-attachments/assets/795cbb63-34b1-450f-83b6-83972386e36b)

**Answer: `Linux4n6`**

### **Q2: What is the timezone of the attached VM?**

The readings will provide the command.

![Timezone](https://github.com/user-attachments/assets/2c1b0bbc-afdc-43bc-8ae0-21ef426b5d14)

**Answer: `Asia/Karachi`**

### **Q3: What program is listening on the address 127.0.0.1:5901?**

I followed the example given in the reading. Look at the IP address, port, state, and Program name.

![Listening Programs](https://github.com/user-attachments/assets/0f6ae7df-7e3e-4d6f-8979-ba53c828ed01)

**Answer: `Xtigervnc`**

### **Q4: What is the full path of this program?**

I used the hint for this. I combined ps to list the processes and grep to display results that has Xtigervnc so the output would not be too big.

![Program Path](https://github.com/user-attachments/assets/3b3465f6-1ef2-4a50-848d-8ac85454e27d)

**Answer: `/usr/bin/Xtigervnc`**

## 🔄 Task 5: Persistence mechanisms

### **Q1: In the bashrc file, the size of the history file is defined. What is the size of the history file that is set for the user Ubuntu in the attached machine?**

Typing `cat ~/.bashrc` that was given from the reading, we can see the file size allocated to us in this machine.

![Bashrc History Size](https://github.com/user-attachments/assets/fa001c1c-3b81-459f-bc02-99598dc1b24c)

**Answer: `2000`**

## ⚡ Task 6: Evidence of Execution

### **Q1: The user tryhackme used apt-get to install a package. What was the command that was issued?**

I used the example command given in the reading. I didn't use -i option since it just ignores cases. I didn't think the cases were important here. Look for the correct user!

![Apt-get Command](https://github.com/user-attachments/assets/d4435ccf-e715-43b5-8b1f-a117a4323611)

**Answer: `sudo apt-get install apache2`**

### **Q2: What was the current working directory when the command to install net-tools was issued?**

Not particularly sure what happened but I started getting error messages when typing `cat /var/log/auth.log* |grep net-tools`. I decided to sudo it and it fixed. I searched for net-tools to reduce the results. Look for PWD for present working directory.

![Working Directory](https://github.com/user-attachments/assets/f5d85dbb-b8ba-4624-bcd1-4ff26d62baea)

**Answer: `/home/ubuntu`**

## 📝 Task 7: Log files

### **Q1: Though the machine's current hostname is the one we identified in Task 4. The machine earlier had a different hostname. What was the previous hostname of the machine?**

I decided to check the syslogs first. Using grep, I searched for logs that had mentions hostname. Seems like we found it!

![Previous Hostname](https://github.com/user-attachments/assets/864dd715-20f3-4177-8f91-88684003cd76)

**Answer: `tryhackme`**

## 💭 Thoughts

Definitely on the lighter side than the Windows one. Admittedly, I didn't feel as invested as Windows one. I'm not entirely sure why. That being said, I'm still going to download that cheat sheet because I'll never know if I need to investigate artifacts in a Linux machine.

---

## 🔐 Cybersecurity Badges

<div align="center">
  
![Linux Forensics](https://img.shields.io/badge/Linux-Forensics-blue)
![System Analysis](https://img.shields.io/badge/System-Analysis-green)
![Log Analysis](https://img.shields.io/badge/Log-Analysis-red)
![User Account Forensics](https://img.shields.io/badge/User_Account-Forensics-orange)
![Process Analysis](https://img.shields.io/badge/Process-Analysis-purple)
![Bash History](https://img.shields.io/badge/Bash-History-yellow)
![Configuration Forensics](https://img.shields.io/badge/Configuration-Forensics-lightgrey)
![Linux Artifacts](https://img.shields.io/badge/Linux-Artifacts-9cf)

</div>

---

## 🛡️ Skills Demonstrated

- **Linux User Account Analysis**
- **System Configuration Investigation**
- **Process and Service Analysis**
- **Bash History Examination**
- **Log File Forensics**
- **Persistence Mechanism Detection**
- **Command Execution Tracking**
- **Hostname and Timezone Analysis**
- **Network Service Investigation**
- **Linux Forensic Artifact Collection**

---

<div align="center">

**🔍 Linux Forensics Investigation Completed** | **✅ System Artifacts Analyzed** | **🛡️ Log Analysis Techniques Applied**

*This investigation provided essential insights into Linux forensic artifacts, system configuration analysis, and log file examination for incident response.*

</div>
