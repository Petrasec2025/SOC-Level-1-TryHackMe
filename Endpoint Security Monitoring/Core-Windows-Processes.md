# 🪟 Core Windows Processes

![Windows](https://img.shields.io/badge/Windows-Core_Processes-blue?style=for-the-badge\&logo=windows)
![SOC Analyst](https://img.shields.io/badge/SOC-Analyst-green?style=for-the-badge)
![DFIR](https://img.shields.io/badge/DFIR-Incident_Response-red?style=for-the-badge)
![Threat Hunting](https://img.shields.io/badge/Threat_Hunting-Windows-yellow?style=for-the-badge)
![TryHackMe](https://img.shields.io/badge/Lab-TryHackMe-purple?style=for-the-badge)

---

Looks like we’re going to be introduced some processes that are vital to Windows, and we can utilize them to detect and investigate our machines. It seems like a great room since a lot of users use Windows, and I believe almost all corporations use Windows too. Being exposed to the tools we have will give us a stronger foundational knowledge of Windows and as a security/SOC anaylst.

<img width="1435" height="343" alt="Screenshot 2025-09-28 at 11 02 26 AM" src="https://github.com/user-attachments/assets/f05facb9-a5c1-4e43-899a-0676a06ecb7f" />  

---

**Read more about the room:** [TryHackMe — Windows Internals (btwindowsinternals)](https://tryhackme.com/room/btwindowsinternals)

## Task 3 System

**1: What PID should System always be?**

From the reading, it said that it is always 4. Out of curiosity, I also checked my own virtual machine and the machine launched on TryHackMe. They were also 4.

**Answer:** 4

---

## Task 4 System > smss.exe

**1: What other two processes do smss.exe start in Session 1? (answer format: process1, process2)**

I checked both csrss.exe and looked for Session 1. The second csrss.exe in the screenshot had it. After that, I looked at winlogon.exe to see if it also had a Session 1, which it did. I used Process Hacker and right clicked the process I was curious about and checked the property. Once the window popped out, I clicked on the “Token” tab to find the session.

<img width="612" height="589" alt="Screenshot 2025-09-30 at 11 53 45 AM" src="https://github.com/user-attachments/assets/f6ed7848-e5a5-4e81-b462-6a234046676b" />  
<img width="605" height="596" alt="Screenshot 2025-09-30 at 11 53 56 AM" src="https://github.com/user-attachments/assets/3bbee535-2d72-4cf5-9cc5-3e51b0a7b1ef" />  

**Answer:** csrss.exe winlogon.exe

---

## Task 5 csrss.exe

**1: What was the process which had PID 384 and PID 488?**

Remember that this process self-terminates, so it will not show itself! We read that from Task 4. In the reading, we are presented with two csrss.exe programs running but their parents are non-existent. That is what gives us the hint we need to get the answer.

**Answer:** smss.exe

---

## Task 6 wininit.exe

**1: Which process might you not see running if Credential Guard is not enabled?**

This one is mentioned in the reading, prefaced with “Note.”

**Answer:** lsaiso.exe

---

## Task 7 wininit.exe > services.exe

**1: How many instances of services.exe should be running on a Windows system?**

Both the TryHackMe and my own virtual machine did have only one service running, and it had wininit.exe as the parent process.

**Answer:** 1

---

## Task 8 wininit.exe > services.exe > svchost.exe

**1: What single letter parameter should always be visible in the Command line or Binary path?**

I checked using both Process Hacker and Process Explorer. The reading showed us how to check on Process Hacker. For Process Explorer, I just right clicked one of the svchost.exe and clicked on properties. Go to the “Image” tab and you’ll be able to see the “k” in the “Command line” area.

<img width="417" height="619" alt="Screenshot 2025-09-30 at 11 54 40 AM" src="https://github.com/user-attachments/assets/bc8cd14b-a70b-43f8-b8e4-1bf7d95dbeb2" />  

**Answer:** k

---

## Task 9 lsass.exe

**1: What is the parent process for LSASS?**

I checked on TryHackMe’s VM. We can see the parent process PID, 668, in this image.

<img width="601" height="588" alt="Screenshot 2025-09-30 at 11 55 09 AM" src="https://github.com/user-attachments/assets/cc93a56b-9547-46a7-afc9-27ef1e1f7ac6" />  

**Answer:** wininit.exe

---

## Task 10 winlogon.exe

**1: What is the non-existent parent process for winlogon.exe?**

Heading back to Task 4, we read that winlogon and wininit is called on by a certain process that self terminates.

**Answer:** smss.exe

---

## Task 11 explorer.exe

**1: What is the non-existent process for explorer.exe?**

Winlogon.exe runs a process, userinit.exe. Userinit.exe then calls explorer.exe and self-terminates. This is why explorer.exe will say it has a non-existent process for the parent.

**Answer:** userinit.exe

---

## Thoughts

A pretty light room but important one. Admittedly I probably won’t remember much from this but I’m glad I got exposed to the important processes Windows has. It will give me a small idea of where to start if I was told we were compromised.

---

## ✅ Conclusion

This room highlights the **core Windows processes** that every SOC Analyst and Incident Responder should be aware of. Knowing their expected behavior and parent/child relationships helps in:

* Spotting **malware masquerading as system processes**
* Detecting **non-existent parent anomalies**
* Understanding **startup process chains** (System → smss.exe → wininit.exe → services.exe / lsass.exe / svchost.exe → explorer.exe)

Being familiar with these builds a strong foundation for Windows defense and incident investigation.

![Windows](https://img.shields.io/badge/Windows-Core_Processes-blue?style=for-the-badge\&logo=windows)
![SOC Analyst](https://img.shields.io/badge/SOC-Analyst-green?style=for-the-badge)
![DFIR](https://img.shields.io/badge/DFIR-Incident_Response-red?style=for-the-badge)
![Threat Hunting](https://img.shields.io/badge/Threat_Hunting-Windows-yellow?style=for-the-badge)
![TryHackMe](https://img.shields.io/badge/Lab-TryHackMe-purple?style=for-the-badge)

