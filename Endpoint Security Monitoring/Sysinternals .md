# Sysinternals Room Walkthrough

![Room Banner](https://github.com/user-attachments/assets/0cfa584e-7247-4e18-8558-a5c4d651d8f1)

## 🏆 Badges
![Windows](https://img.shields.io/badge/Windows-Sysinternals-0078D6?style=for-the-badge&logo=windows&logoColor=white)
![Tools](https://img.shields.io/badge/Tools-Administration-00C800?style=for-the-badge&logo=tools&logoColor=white)
![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-FFFF00?style=for-the-badge)
![Platform](https://img.shields.io/badge/Platform-TryHackMe-FF0000?style=for-the-badge&logo=tryhackme&logoColor=white)
![Completion](https://img.shields.io/badge/Completion-100%25-00FF00?style=for-the-badge)
![Skills](https://img.shields.io/badge/Skills-Windows_Forensics-800080?style=for-the-badge)

## Overview
Last time, we learned a few common core processes that Windows run. We were taught some common irregularities that might cause us needing to investigate further. This time, we will be exposed a tool called Sysinternals, which is a compilation of tools used by IT administrators, especially in a Windows setting. I'm pretty excited for this lab as the further I delve into the SOC Level 1 Module, the more comfortable I feel troubleshooting Windows. Let's get started! I'll be documenting my thought process as to how I get the answer, if it's right or wrong.

---

## Task 2 Install the Sysinternals Suite

### Question 1: What is the last tool listed within the Sysinternals Suite?
This will require us to look at the link given to us in the task. [Click here for the link](https://docs.microsoft.com/en-us/sysinternals/). Scroll down once you are at the site.

**Answer:** `Zoomit`

---

## Task 3 Using Sysinternals Live

### Question 1: What service needs to be enabled on the local host to interact with live.sysinternals.com?
In the reading, the service mentioned that is needed is called Webclient. In Windows 10, it is disabled by default so we will need to turn it on if we want to use Sysinternals without downloading the tools.

We're going to be turning on Webclient and installing WebDAV Redirector to the machine in the lab. I decided to RDP into the Windows machine using my own Kali VM. Below is the command I typed into my Kali VM. `/u:` is for username, `/p:` is for password, `/v:` is for the IP address of the machine we are going to RDP into, and `/dynamic-resolution` is so we can change the resolution once we RDP into the machine.

![RDP Command](https://github.com/user-attachments/assets/27853572-525d-4320-9c73-60e1c7ba929d)

It will ask you if you want to trust the certificate. Press "Y."

![Certificate Trust](https://github.com/user-attachments/assets/8b3da99e-e5b4-47e0-83a3-369ebda107c3)

And you can see I successfully RDP's into the Windows machine!

![RDP Success](https://github.com/user-attachments/assets/72de4642-ee26-462f-8b3b-8c4ea9136f03)

Next, we're going to start Powershell. Click on the blue icon on the bottom of your Windows machine screen.

![PowerShell](https://github.com/user-attachments/assets/51985e2b-fd59-43e0-98e2-0107532ab7f5)

After that, I ran `get-service webclient` to see if my service is running. It is not, so I typed `start-service webclient` to start it, and then confirming it is running now.

![WebClient Service](https://github.com/user-attachments/assets/6f346378-f928-410e-97fc-a883365da7f7)

Next, we are going to make sure our network discovery is turned on. I typed in `control.exe /name Microsoft.NetworkAndSharingCenter` into PowerShell as per the reading. You should have a window that appears, just like the one shown below. Click on "Change advanced sharing settings" on the left.

![Network Sharing Center](https://github.com/user-attachments/assets/fb75c9be-b079-435d-9390-ec68cd8e58e8)

Then turn network discovery on.

![Network Discovery](https://github.com/user-attachments/assets/553e11b8-5d13-46bc-8e08-2f26704a5f1a)

Finally, we are going to install a feature called "WebDAV Redirector" onto our Windows machine. I typed in `Install-WindowsFeature WebDAV-Redirector -Restart`, and apparently we are suppose to have our machine restart as per the reading. Mine said it didn't need, so I'm not sure if everyone else will be the same.

![WebDAV Install](https://github.com/user-attachments/assets/adf47500-c5c8-49b7-8299-d09f470bad0b)

I typed `Get-WindowsFeature WebDAV-Redirector | Format-Table -Autosize` after to make sure my output is the same as the reading, and it was.

![WebDAV Verification](https://github.com/user-attachments/assets/fc6978e9-3169-468d-b179-0cd00a548f71)

And after all that, seems like it didn't work haha. After spending 30 minutes of troubleshooting, I found out that the machine does not have access to the internet. We will have to use sysinternals differently. We are mainly going to use it through the command line but we do not have to map it or anything.

![No Internet](https://github.com/user-attachments/assets/6b429835-9765-4671-9ff3-fedc1fb67820)

![Ping Test](https://github.com/user-attachments/assets/a895b5c8-380f-4e51-bd3c-6b1c8288b1f8)

We still have this compressed file so I think we can still continue this room, even if we cannot access the files online.

![Compressed File](https://github.com/user-attachments/assets/05eb2b52-723d-466c-86ff-4b60236f7ad0)

**Answer:** `Webclient`

---

## Task 4 File and Disk Utilities

### Question 1: There is a txt file on the desktop named file.txt. Using one of the three discussed tools in this task, what is the text within the ADS?
We will extract the file to Desktop. Right click The SysinternalSuite.zip, right click it, and extract all. The default location should be extract to Desktop. After that is done, go to your terminal and type `cd Desktop` to make sure our current directory is in Desktop. After that, run `streams file.txt`. Take note of a new text file that pop up! I used the hint for the final step. Run `notepad file.txt:ads.txt` to view that hidden text file in our notepad.

![Streams Output](https://github.com/user-attachments/assets/ee29f2de-72f4-4906-b2ab-ea047c58a52e)

**Answer:** `I am hiding in the stream.`

---

## Task 5 Networking Utilities

### Question 1: Using WHOIS tools, what is the ISP/Organization for the remote address in the screenshots above?
Admittedly, I used the WHOIS tool on the machine even though it does not have internet. What you really have to do is go to https://www.whois.com/ and type in the IP address there. Look for "Organization" tag and type in the answer!

**Answer:** `Microsoft Corporation`

---

## Task 6 Process Utilities

### Question 1: What entry was updated?
Launch autoruns with `autoruns` in the terminal and then head over to the "Image Hijacks" tab. Give it around a minute or so to load. You should see a new entry loaded in. If you don't see it loaded.

**Answer:** `taskmgr.exe`

### Question 2: What is the updated value?
Look at the image path.

![Autoruns Output](https://github.com/user-attachments/assets/957693c7-8bd1-496e-9900-58f12625c9ac)

**Answer:** `C:\TOOLS\SYSINT\PROCEXP.EXE`

---

## Task 9 Miscellaneous

### Question 1: Run the Strings tool on ZoomIt.exe. What is the full path to the .pdb file?
I ran the following command into the terminal. First I went to the SysinternalSuite directory with `cd SysinternalSuites`. After that, I typed `strings Zoomit.exe | findstr /i .pdb` as we are looking for a .pdb string. Two results come up! Unfortunately, the room isn't updated with the answer. It uses the old answer, which I found out on THM's official Discord page. I had to look for an older write-up to get the answer.

![Strings Output](https://github.com/user-attachments/assets/044e1645-5675-49ae-8ff9-ea5257ef62dd)

**Answer:** `C:\agent\_work\112\s\Win32\Release\ZoomIt.pdb`

In the future, the answer could be one of the above if the room gets updated.

---

## 🎯 Final Badges
![Tools Used](https://img.shields.io/badge/Tools_Used-Streams|Autoruns|Strings-FFA500?style=for-the-badge)
![Forensics](https://img.shields.io/badge/Forensics-ADS_Detection-000080?style=for-the-badge)
![Room](https://img.shields.io/badge/Room-Sysinternals-FF69B4?style=for-the-badge)

## Thoughts & Conclusion

I admit I was pretty frustrated troubleshooting issues for task 3. I didn't fully detail what I did during the troubleshooting but it sure did take about 30 minutes, along with watching videos and reading documentations. I guess that helps my troubleshooting skills!

Also pretty excited for the Sysmon room. I was exposed to it during Splunk practice, so I think it's a good way to see how it integrates into SIEMs.

I do wish the room is updated to have the output we have in task 9 as the correct answer. I guess the nature of updating rooms and fixing bugs in hundreds of machines can be a daunting task for THM. At least for now, I did my best to document the correct answer as of July 15, 2023.

---

**Room Link:** [https://tryhackme.com/room/btsysinternalssg](https://tryhackme.com/room/btsysinternalssg)
