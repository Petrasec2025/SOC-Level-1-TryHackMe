# Sysmon Room Walkthrough

![Room Banner](https://github.com/user-attachments/assets/4476890f-91e5-4b4b-92ff-d6c6822f3b61)

## 🏆 Badges
![Windows](https://img.shields.io/badge/Windows-Sysmon-0078D6?style=for-the-badge&logo=windows&logoColor=white)
![Forensics](https://img.shields.io/badge/Forensics-Log_Analysis-00C800?style=for-the-badge&logo=search&logoColor=white)
![Difficulty](https://img.shields.io/badge/Difficulty-Intermediate-FFA500?style=for-the-badge)
![Platform](https://img.shields.io/badge/Platform-TryHackMe-FF0000?style=for-the-badge&logo=tryhackme&logoColor=white)
![Completion](https://img.shields.io/badge/Completion-100%25-00FF00?style=for-the-badge)
![Tools](https://img.shields.io/badge/Tools-EventViewer|PowerShell-800080?style=for-the-badge)

## Overview
We will be doing the Sysmon room this time. I don't know about Sysmon too much except that it's usually running in the background and helps logs events for us, similar to Windows Event Manager. I believe it is a bit more comprehensive in its logging which is why it's useful to check these logs when using our SIEMs. Let's get started! As always, I'll document if I used external sources when doing these labs.

---

## Task 3 Installing and Preparing Sysmon

I will be RDPing into the machine instead of downloading the files on my host machine. I created a RDP guide recently since we RDP a lot. I thought it'll be nice to keep the RDP steps in one post instead of always writing it. It's located here. Please check it out!

---

## Task 4 Cutting out the Noise

### Question 1: How many event ID 3 events are in C:\Users\THM-Analyst\Desktop\Scenarios\Practice\Filtering.evtx?
I used the following command `C:\Users\THM-Analyst\Desktop\Scenarios\Practice> Get-WinEvent -Path C:\Users\THM-Analyst\Desktop\Scenarios\Practice\Filtering.evtx -FilterXPath '*/System/EventID=3'| Measure-Object -Line`. I defined the path using the -Path parameter and telling which file we are going to examine. Using our XPath knowledge, I created a filter to only look for EventIDs that had a value of 3. I used Measure-Object -Line to count the results for me. If you didn't use it (like I did originally), you would be flooded with the sheer amount of logs, and I don't even think it'll tell you how many logs were there at the end.

![Event ID 3 Count](https://github.com/user-attachments/assets/a8e9f83f-640f-4efe-b485-ebe830951af3)

![Event Count Result](https://github.com/user-attachments/assets/44dbd9b4-3e32-4e7c-9eab-8023d26a1062)

**Answer:** `73,591` (The comma is necessary!)

### Question 2: What is the UTC time created of the first network event in C:\Users\THM-Analyst\Desktop\Scenarios\Practice\Filtering.evtx?
I decided to use Windows Event Viewer again since I'm really not good with XPath queries. I opened the file by going to the Scenario folder, then opening Practice, and finally double clicking on "Filtering."

![Opening Filtering File](https://github.com/user-attachments/assets/4e20df73-462d-4a12-a5a8-c30a88447c41)

This should open Event Viewer. From there, I looked for the oldest event that looked network-related.

![Oldest Network Event](https://github.com/user-attachments/assets/72712b4d-df7a-4545-9b19-e46dbd4ef3dc)

Once I believed I found my log, I went to the details tab, clicked on XML view and looked for "UTC Time."

![UTC Time](https://github.com/user-attachments/assets/0aa83972-6680-48fa-a724-5123c20f938c)

**Answer:** `2021-01-06 01:35:50.464`

---

## Task 10 Practical Investigations

### Question 1: What is the full registry key of the USB device calling svchost.exe in Investigation 1?
I looked at the earliest logs and worked my way to the latest. What I focused on was to see if anything references svchost.exe.

![USB Registry Key](https://github.com/user-attachments/assets/3e671cfd-6df1-485a-b409-91361143f85c)

**Answer:** `HKLM\System\CurrentControlSet\Enum\WpdBusEnumRoot\UMB\2&37c186b&0&STORAGE#VOLUME#_??_USBSTOR#DISK&VEN_SANDISK&PROD_U3_CRUZER_MICRO&REV_8.01#4054910EF19005B3&0#\FriendlyName`

### Question 2: What is the device name when being called by RawAccessRead in Investigation 1?
I looked at the earliest instance of "RawAccessRead" under Task Category. After that, I looked for anything that would give a name. Instead I found a "Device" tag instead.

![RawAccessRead Device](https://github.com/user-attachments/assets/bccd2092-624b-4b5e-8d5b-ae06aad21e8c)

**Answer:** `\Device\HarddiskVolume3`

### Question 3: What is the first exe the process executes in Investigation 1?
I worked down starting with the earliest after the first RawAccessRead event. WUDFHost.exe was not the right answer. After a few tries, I saw the latest entry is rundll32.exe being terminated. I decided to enter that as the answer because I thought maybe the malicious file wanted to terminate the process it started to make it harder for anyone to notice something is in the network.

**Answer:** `rundll32.exe`

### Question 4: What is the full path of the payload in Investigation 2?
Loading investigation 2, I saw there was only 3 events. I scanned through all 3 of them until I found this interesting bit.

![Payload Path](https://github.com/user-attachments/assets/fa2bbb7a-3f5a-4455-879c-30cf44acf73e)

**Answer:** `C:\Users\IEUser\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\S97WTYG7\update.hta`

### Question 5: What is the full path of the file the payload masked itself as in Investigation 2?
I tried a couple of other answers that looked interesting but unfortunately, they were not correct. In the end, I found the answer.

![Masked File Path](https://github.com/user-attachments/assets/38eaa436-b214-4b9b-a0ac-583db0d6e244)

**Answer:** `C:\Users\IEUser\Downloads\update.html`

### Question 6: What signed binary executed the payload in Investigation 2?
I decided to go with this one first because this was on the same line as the payload. It was correct!

![Signed Binary](https://github.com/user-attachments/assets/d78ce815-6887-417a-a055-673d24a68b13)

**Answer:** `C:\Windows\System32\mshta.exe`

### Question 7: What is the IP of the adversary in Investigation 2?
I looked at the event logs and looked for anything that dealt with networks. It looks like one of them had "Network connections detected" which felt like might give me the answer.

![Network Connection](https://github.com/user-attachments/assets/b5fb09a4-398d-4b47-aa78-536439540b20)

Initially I entered 10.0.2.13 but it was wrong. Looks like it was the destination IP instead. I'm not sure why. Perhaps this was a backdoor and we are trying to connect a C2 server.

![Destination IP](https://github.com/user-attachments/assets/4a7a141b-298a-4598-ae04-b0861326689c)

**Answer:** `10.0.2.18`

### Question 8: What back connect port is used in Investigation 2?
From the above image, we just have to find the destination port too.

**Answer:** `4443`

### Question 9: What is the IP of the suspected adversary in Investigation 3.1?
I decided to check the earliest connection event first. From there, I looked at destination IP because the scenario is that there is persistence in our network. I believe that means that our computer is trying to connect to a C2 server, so we would be the source and C2 server would be the destination.

![Adversary IP](https://github.com/user-attachments/assets/d0a134cd-011b-48ed-a41f-cea0ee3036f6)

**Answer:** `172.30.1.253`

### Question 10: What is the hostname of the affected endpoint in Investigation 3.1?
Now that we know we are the host, we have to find the host name. The above image shows what we need.

**Answer:** `DESKTOP-O153T4R`

### Question 11: What is the hostname of the C2 server connecting to the endpoint in Investigation 3.1?
We know the destination IP, now we need to look for the host name, which is displayed from the screenshot two questions ago.

**Answer:** `empirec2`

### Question 12: Where in the registry was the payload stored in Investigation 3.1?
I was looking through the logs and saw something interesting. I'm not confident enough to say it's a base64 but the target object seems to be called again in a different event in a powershell script, so it looked like this could be where the payload is stored.

![Registry Payload](https://github.com/user-attachments/assets/2d6a8270-4790-4d62-8138-be1936c64754)

**Answer:** `HKLM\SOFTWARE\Microsoft\Network\debug`

### Question 13: What PowerShell launch code was used to launch the payload in Investigation 3.1?
**Answer:** `"C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe" -c "$x=$((gp HKLM:Software\Microsoft\Network debug).debug);start -Win Hidden -A \"-enc $x\" powershell";exit;`

### Question 14: What is the IP of the adversary in Investigation 3.2?
What I did here is starting from the earliest log. I saw there was a network connection detected and sourcehostname is us. I tried the destination IP as the answer and it was correct.

![Adversary IP 3.2](https://github.com/user-attachments/assets/de5d46d1-3edc-48e6-b5fa-b69d6294eb01)

**Answer:** `172.168.103.188`

### Question 15: What is the full path of the payload location in Investigation 3.2?
Again, working my way from the earliest to latest, I came across an event that had this in the command line. It seems to be in Base64 and its calling for something called blah.txt.

![Payload Location](https://github.com/user-attachments/assets/4a94660e-6339-4bf4-b7ce-29261e36afca)

**Answer:** `c:\users\q\AppData:blah.txt`

### Question 16: What was the full command used to create the scheduled task in Investigation 3.2?
Continuing on with the event logs digging, I saw this one has schtasks.exe, which helps create, delete, and query scheduled tasks, along with other options. This has to be it.

![Scheduled Task Command](https://github.com/user-attachments/assets/c3d64fd8-df09-4109-9063-b19b79c8d253)

**Answer:** `"C:\WINDOWS\system32\schtasks.exe" /Create /F /SC DAILY /ST 09:00 /TN Updater /TR "C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe -NonI -W hidden -c \"IEX ([Text.Encoding]::UNICODE.GetString([Convert]::FromBase64String($(cmd /c ''more < c:\users\q\AppData:blah.txt'''))))\""`

### Question 17: What process was accessed by schtasks.exe that would be considered suspicious behavior in Investigation 3.2?
I saw lsass.exe and schtasks.exe on a few logs,and thought it may be weird. I had t check online was lsass.exe was again as I forgot. It is a windows process that verifies your username and password. Deleting this process would log you out of Windows, which is probably weird that there is a scheduled task on it.

![Suspicious Process](https://github.com/user-attachments/assets/27a338be-e046-4c70-9c4f-8dac66863db2)

**Answer:** `lsass.exe`

### Question 18: What is the IP of the adversary in Investigation 4?
I started from the earliest event again. I found this IP and the hostname was an adversary from previous scenarios, so I thought this had to be it.

![Adversary IP 4](https://github.com/user-attachments/assets/eaec42de-0fcc-46f1-b0e4-ee63f039e3a9)

**Answer:** `172.30.1.253`

### Question 19: What port is the adversary operating on in Investigation 4?
The port is also given in the same log entry!

**Answer:** `80`

### Question 20: What C2 is the adversary utilizing in Investigation 4?
I searched online what empirec2 is. Apparently it's Empire C2. Looks like that was the answer.

**Answer:** `Empire`

---

## 🎯 Final Badges
![Analysis](https://img.shields.io/badge/Analysis-Event_Investigation-FF69B4?style=for-the-badge)
![Security](https://img.shields.io/badge/Security-Incident_Response-000080?style=for-the-badge)
![Room](https://img.shields.io/badge/Room-Sysmon-FF4500?style=for-the-badge)
![C2](https://img.shields.io/badge/C2-Empire_Detection-008080?style=for-the-badge)

## Thoughts & Conclusion

This wasn't too hard. It was another good run utilizing Windows Event Viewer and how you can get a couple of questions answered in your identification phase of incident response. I don't know if it's just me, but it did not prepare me how to use XPath queries to answer these questions. Just when I started getting an understanding of it, I had to rely on the GUI of Windows Event Viewer. Slow but steady!

The room provided excellent practical experience with Sysmon event analysis and investigation techniques. The hands-on scenarios helped reinforce the importance of detailed logging in detecting malicious activities, from USB device analysis to C2 communication detection and persistence mechanism identification.

---

**Room Link:** [https://tryhackme.com/room/sysmon](https://tryhackme.com/room/sysmon)
