# Retracted Room Walkthrough

![Room Banner](https://github.com/user-attachments/assets/e4003129-526b-46da-badf-3cb245a26aeb)

## 🏆 Badges
![Incident Response](https://img.shields.io/badge/Incident_Response-Ransomware-0078D6?style=for-the-badge&logo=shield&logoColor=white)
![Forensics](https://img.shields.io/badge/Forensics-Windows_Events-00C800?style=for-the-badge&logo=search&logoColor=white)
![Difficulty](https://img.shields.io/badge/Difficulty-Intermediate-FFA500?style=for-the-badge)
![Platform](https://img.shields.io/badge/Platform-TryHackMe-FF0000?style=for-the-badge&logo=tryhackme&logoColor=white)
![Completion](https://img.shields.io/badge/Completion-100%25-00FF00?style=for-the-badge)
![Investigation](https://img.shields.io/badge/Investigation-Case_Study-800080?style=for-the-badge)

## Scenario
Investigate the case of the missing ransomware. After learning about Wazuh previously, today's task is a bit different.

It's still part of the Endpoint Security module that we need to address. We have a ransomware case that we need to solve as cybersecurity engineers.

### A Mother's Plea
"Thanks for coming. I know you are busy with your new job, but I did not know who else to turn to."

"So I downloaded and ran an installer for an antivirus program I needed. After a while, I noticed I could no longer open any of my files. And then I saw that my wallpaper was different and contained a terrifying message telling me to pay if I wanted to get my files back. I panicked and got out of the room to call you. But when I came back, everything was back to normal."

"Except for one message telling me to check my Bitcoin wallet. But I don't even know what a Bitcoin is!"

"Can you help me check if my computer is now fine?"

## Connecting to the Machine
Start the virtual machine in split-screen view by clicking on the green "Start Machine" button on the upper right section of this task. If the VM is not visible, use the blue "Show Split View" button at the top-right of the page. Alternatively, you can connect to the VM using the credentials below via "Remote Desktop".

![RDP Credentials](https://github.com/user-attachments/assets/67164fc1-32fd-4e27-b611-1ff250c31bc0)

"Oh, the password doesn't work? Wait, I have it written somewhere. Uhmm... Try this:"

---

## TASK 2: The Message
"So, as soon as you finish logging in to the computer, you'll see a file on the desktop addressed to me."

"I have no idea why that message is there and what it means. Maybe you do?"

### Question 1: What is the full path of the text file containing the "message"?
**A:** `C:\Users\Sophie\Desktop\SOPHIE.txt`

You will find it right away when you check the details in the properties feature of Notepad.

![SOPHIE.txt Properties](https://github.com/user-attachments/assets/5c76a75d-695d-429b-b767-cb9790f201db)

### Question 2: What is the name of the process that created the text file?
**A:** `notepad.exe`

This is where it gets a little technical. You can go to Event Viewer, as we learned before, and navigate to the Application and Service Logs (since it was an app) → Microsoft → Windows → Sysmon → and finally, Operational.

![Sysmon Operational Log](https://github.com/user-attachments/assets/faae1164-3cc0-4feb-b889-bb789bea1d08)

Since we want to find the file name as well as the process that created the file, we will use the 'Process Create' task category, which is considered as Event ID 1. I'll use this for the filter to speed up the search.

![Event ID 1 Filter](https://github.com/user-attachments/assets/9f3b4205-ae32-462c-909c-63a3b3f41211)

![Process Create Events](https://github.com/user-attachments/assets/ea0356dd-2020-43c4-a39d-f61c7e94622f)

In the next step, we'll have dozens of Event ID 1 entries, but we still won't know which one to click. So, we'll need to specifically search for the file SOPHIE.txt.

![Search for SOPHIE.txt](https://github.com/user-attachments/assets/58d97974-629d-4b9d-8913-c4471789c403)

And here we go, we've found the file!

![SOPHIE.txt Creation](https://github.com/user-attachments/assets/cae1ed2f-5925-495d-b8d1-19d6ef5bfee1)

### Question 3: What is the time of execution of the process that created the text file? Timezone UTC (Format YYYY-MM-DD hh:mm:ss)
**A:** `2024-01-08 14:25:30`

We've already found it, along with the file extension.

![Creation Time](https://github.com/user-attachments/assets/6c011324-92a2-42fe-aec6-9e460880d393)

---

## TASK 3: Something Wrong
"I swear something went wrong with my computer when I ran the installer. Suddenly, my files could not be opened, and the wallpaper changed, telling me to pay."

"Wait, are you telling me that the file I downloaded is a virus? But I downloaded it from Google!"

### Question 1: What is the filename of this "installer"? (Including the file extension)
**A:** `antivirus.exe`

Let's see, maybe we can find it on the 'Google' she's been talking about. We just need to go to the 'Downloads history' section.

![Downloads History](https://github.com/user-attachments/assets/87848478-1def-462c-8254-fe1232406b20)

BINGO!! We've got it!

![antivirus.exe Download](https://github.com/user-attachments/assets/e6479fff-42d4-43aa-967d-4704d31bf0e8)

### Question 2: What is the download location of this installer?
**A:** `C:\Users\Sophie\download`

Similarly, if you want to simplify things, just 'inspect' the file using the properties feature.

![File Properties Location](https://github.com/user-attachments/assets/4243eca4-79dd-4fc3-a716-f403a1f0df5e)

### Question 3: The installer encrypts files and then adds a file extension to the end of the file name. What is this file extension?
**A:** `.dmp`

Back in the Event Viewer, we need to search for the file using the 'Find' search bar. Don't forget to clear the filter, as we won't be using it anymore.

![Clear Filter](https://github.com/user-attachments/assets/8bd5998d-99d0-4dcf-8940-2de98e156e88)

After searching for 'antivirus.exe', since the question is about file creation, we will focus on Event ID 11, which represents 'File Created'.

![File Created Events](https://github.com/user-attachments/assets/ecac794d-3a67-42f3-8b21-3c2d496c9b2a)

### Question 4: The installer reached out to an IP. What is this IP?
**A:** `10.10.8.111`

We've noticed that to find the IP address, we need to use Event ID 3, as it pertains to the network connect task category.

![Network Connect Events](https://github.com/user-attachments/assets/a170c8df-0629-41c7-b5ac-632935dfbef5)

After that, we will find the Destination IP by looking it up in the Details feature.

![Destination IP](https://github.com/user-attachments/assets/f87379ae-ba4c-400a-8f08-78a93c4fb5ba)

---

## TASK 4
"So what happened to the virus? It does seem to be gone since all my files are back."

### Question 1: The threat actor logged in via RDP right after the "installer" was downloaded. What is the source IP?
**A:** `10.11.27.46`

Still within the Event ID 3 filter (since we want to find IP addresses), we just need to search for 'RDP' to get the IP. And there we go, we've got the IP.

![RDP Source IP](https://github.com/user-attachments/assets/3d97d965-0e1a-443f-881b-22c49b10b3c9)

### Question 2: This other person downloaded a file and ran it. When was this file run? Timezone UTC (Format YYYY-MM-DD hh:mm:ss)
**A:** `2024-01-08 14:24:18`

Since we want to see when the file was run at a specific time, we need to switch back to Event ID 1 and use the decryptor.exe file that we haven't used before. Let's see if it works and is usable.

![Decryptor Execution Time](https://github.com/user-attachments/assets/3d97d965-0e1a-443f-881b-22c49b10b3c9)

And there you go, we've found the UTC time after searching for decryptor.

---

## TASK 5: Doesn't Make Sense
"So you're telling me that someone accessed my computer and changed my files but later undid the changes?"

"That doesn't make any sense. Why infect my machine and clean it afterwards?"

"Can you help me make sense of this?"

### Arrange the following events in sequential order from 1 to 7, based on the timeline in which they occurred:

1. **Sophie downloaded the malware and ran it**
2. **The malware encrypted the files on the computer and showed a ransomware note**
3. **Someone else logged into Sophie's machine via RDP and started looking around**
4. **The intruder downloaded a decryptor and decrypted all the files**
5. **A note was created on the desktop telling Sophie to check her Bitcoin**
6. **We arrive on the scene to investigate**

---

## 🎯 Final Badges
![Ransomware](https://img.shields.io/badge/Ransomware-Investigation-FF69B4?style=for-the-badge)
![Sysmon](https://img.shields.io/badge/Sysmon-Forensics-000080?style=for-the-badge)
![Room](https://img.shields.io/badge/Room-Retracted-FF4500?style=for-the-badge)
![Timeline](https://img.shields.io/badge/Timeline-Reconstruction-008080?style=for-the-badge)

## Conclusion
And there you go, the Sophie problem with her computer is resolved. The main issue lies with people who lack understanding or knowledge about cybercrime today.

This investigation demonstrated practical digital forensics skills including:
- Event log analysis using Windows Event Viewer and Sysmon
- Timeline reconstruction of security incidents
- Ransomware behavior analysis
- Network connection tracing
- File system artifact examination

The case highlights the importance of proper cybersecurity awareness and the value of systematic incident response procedures when dealing with potential malware infections.

---

**Room Link:** [https://tryhackme.com/room/retracted](https://tryhackme.com/room/retracted)




