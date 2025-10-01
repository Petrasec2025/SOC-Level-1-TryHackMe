# Windows Forensics 2

![Room Banner](https://github.com/user-attachments/assets/f632650f-ae4e-477d-a7a6-5b1bf913cd8d)

## 📋 Overview

This is the second part of Windows Forensics. The write-up I did for the first part can be found here. I enjoyed the difficulty last time and I hope this time will be the same. Looks like we're not going to be focused on the registry but also on the file system this time. Let's get started!

## 💾 Task 2: The FAT file systems

### **Q1: How many addressable bits are there in the FAT32 file system?**
This can be found in the reading.

**Answer: `28 bits`**

### **Q2: What is the maximum file size supported by the FAT32 file system?**
This can be found in the reading. Just note that while FAT32 can hold up to 2TB, a single file can only be a maximum of 4GB.

**Answer: `4GB`**

### **Q3: Which file system is used by digital cameras and SD cards?**
This can be found in the reading.

**Answer: `exFAT`**

## 🔍 Task 3: The NTFS File System

I will be RDPing into the machine. I wrote a guide here. Please check it out!

### **Q1: Parse the $MFT file placed in C:\users\THM-4n6\Desktop\triage\C\ and analyze it. What is the Size of the file located at .\Windows\Security\logs\SceSetupLog.etl**

First, we will open the command prompt and run it as an administrator. Go to the search bar next to the start menu and type in cmd. Right click command prompt and run it as administrator. If you did it correctly, it should show C:\WINDOWS\system32 like below.

![Admin Command Prompt](https://github.com/user-attachments/assets/d615cc08-6815-484e-81bd-15ac38bbb4ea)

![Admin Confirmation](https://github.com/user-attachments/assets/eb90ba03-981f-4238-ac48-8c802ebc9e47)

Let's navigate to where EZtools is at with `cd C:\Users\THM-4n6\Desktop\EZtools`

![Navigate to EZTools](https://github.com/user-attachments/assets/ee3004d3-8295-43ca-88d4-c7233d36d65b)

Now we will run the following command to parse the $MFT file and save it to a new location with `MFTECmd.exe -f C:\Users\THM-4n6\Desktop\triage\C\$MFT -csv C:\Users\THM-4n6\Desktop`. I got the command from the reading.

![MFT Parse Command](https://github.com/user-attachments/assets/e0f2c261-956b-4a5c-8d6a-8e417dc27185)

It may take a while to process. The new file will appear in the desktop.

![MFT Output File](https://github.com/user-attachments/assets/95bb3acb-c0df-4a4f-b07b-c4892e6d8a2e)

Now lets open EZViewer. It can be found in your Desktop folder -> EZtools -> EZViewer.
Once EZViewer loads, I dragged our output file into EZViewer.

![EZViewer Load](https://github.com/user-attachments/assets/5200c1b0-1423-481c-ad50-c262111d27fd)

If done correctly, it should load the file and it'll look like an excel spreadsheet.

![MFT Data Loaded](https://github.com/user-attachments/assets/898a7e5f-dd95-4f2d-983c-ea37b00385d8)

The next step took me about 10 minutes. I did CTRL+F to help find my results and pasted `.\Windows\Security\logs\SceSetupLog.etl` but I kept getting no results. I ended up trying out `.\Windows\Se` to see if this works. I ended up finding what I need!

![File Search Results](https://github.com/user-attachments/assets/c05b52ad-012b-49da-86a7-64d626834b23)

I extended a few column headers to see what the columns were displaying.

**Answer: `49152`**

### **Q2: What is the size of the cluster for the volume from which this triage was taken?**

I had to look at the hint for this. Looks like we need to parse the $BOOT file this time. The command I used is `MFTECmd.exe -f C:\Users\THM-4n6\Desktop\triage\C\$BOOT`. Remember that your command prompt has to be in administrator mode, and it has to be in the EZTool folder.

The output should be like this.

![Boot File Output](https://github.com/user-attachments/assets/476afb94-4836-4c08-bd77-93e0e1d6f2f1)

**Answer: `4096`**

## 🔄 Task 4: Recovering deleted files

### **Q1: There is another xlsx file that was deleted. What is the full name of that file?**

I followed the instructions per the reading to set up Autopsy. There are a few deleted files I can see. Deleted files has an X mark on their icon. The first one, "New Microsoft Excel Worksheet.xlsx" was part of the Autopsy set up demonstration. The second one is the answer.

![Deleted Files](https://github.com/user-attachments/assets/e8dccf38-77aa-4f81-87b0-cf7e296f628d)

**Answer: `TryHackme.xlsx`**

### **Q2: What is the name of the TXT file that was deleted from the disk?**

From the above screenshot, we can see another deleted file, this time a .txt. This is what we need.

**Answer: `TryHackMe2.txt`**

### **Q3: Recover the TXT file from Question #2. What was written in this txt file?**

Right click the file and then select Extra File(s). Remember where you saved it!

![File Extraction](https://github.com/user-attachments/assets/ed7b908a-9e94-4f31-bb05-61daf70d01c0)

After that, it's a matter of opening that file to view contents.

![File Contents](https://github.com/user-attachments/assets/ac3849ce-5b86-4840-8d35-5d1d3080f107)

Alternatively, you can view text file directly from Autopsy by selecting the Text tab at the bottom.

![Text View](https://github.com/user-attachments/assets/3788e43a-3882-4e76-bbaa-e5a64df1084f)

**Answer: `THM-4n6-2-4`**

## ⚡ Task 5: Evidence of Execution

### **Q1: How many times was gkape.exe executed?**

Looks like we will be parsing files quite a bit in this section. Since we are checking how many times a certain file was executed, we will be using Prefetch Parser. The command is that I used is `PECmd.exe -d C:\Users\THM-4n6\Desktop\triage\C\Windows\prefetch -csv C:\Users\THM-4n6\Desktop`. I modified the example command given from the reading. The location of the prefetch directory we need to parse is at `C:\Users\THM-4n6\Desktop\triage\C\Windows\prefetch`.

![Prefetch Parse Command](https://github.com/user-attachments/assets/12be4723-597b-4964-8501-a4a1a193f262)

Two output files should appear. I opened the PECmd_Output.csv file (not timeline) with EZViewer. To search for the file, I did CTRL+F and typed in gkape.exe. There may be two results. The first result didn't really give me the path that I needed. The second one sent me to the path I need. I then scrolled up to look at the column headers and saw it was ran twice.

![Execution Count](https://github.com/user-attachments/assets/4b2390ca-d744-44d3-9848-b14c06cc6dfa)

**Answer: `2`**

### **Q2: What is the last execution time of gkape.exe**

The above screenshot also shows the last time it was executed. Also note that THM wants the answer in a MM/DD/YYYY HH:MM format. I was wondering why 12/1/2012 13:04 didn't work for a bit.

**Answer: `12/01/2021 13:04`**

### **Q3: When Notepad.exe was opened on 11/30/2021 at 10:56, how long did it remain in focus?**

Since we are going to see how long a certain application has been in focus, we will need to parse using Windows 10 Timeline. I used the following command on the command line. `WxTCmd.exe -f C:\Users\THM-4n6\Desktop\triage\C\Users\THM-4n6\AppData\Local\ConnectedDevicesPlatform\L.THM-4n6\ActivitiesCache.db --csv C:\Users\THM-4n6\Desktop`.

![Timeline Parse Command](https://github.com/user-attachments/assets/d2a266a8-a326-4644-ba5d-295767546d6b)

Two files should be outputted. I opened Activity.csv (not Activity Package ID) with EZViewer. I used CTRL+F again and looked for notepad.exe. There are 4 results. Make sure you check the correct notepad.exe! I definitely didn't make that mistake and entered 0:00:56 twice! Then look at the duration.

![Notepad Focus Duration](https://github.com/user-attachments/assets/ef9a8fc5-9b1a-4eec-86f9-9c6a6cd0c4ed)

**Answer: `00:00:41`**

### **Q4: What program was used to open C:\Users\THM-4n6\Desktop\KAPE\KAPE\ChangeLog.txt?**

Back to the terminal again! This time we will be parsing the Jump Lists. I typed in `JLECmd.exe -d C:\Users\THM-4n6\Desktop\triage\C\Users\THM-4n6\AppData\Roaming\Microsoft\Windows\Recent\AutomaticDestinations --csv C:\Users\THM-4n6\Desktop` in the terminal. Again, I modified the example command that was given in the reading.

![Jump Lists Parse Command](https://github.com/user-attachments/assets/56c28116-2ad0-4c7d-a500-3cbd86e639d6)

I opened the output file, AutomaticDestinations.csv, with EZViewer. I used CTRL+F to find KAPE\KAPE and found few results. I'm not entirely sure but I looked at AppIdDescription and saw notepad, so my guess was the user used notepad.

![Jump Lists Results](https://github.com/user-attachments/assets/f4cb2e14-3355-4612-9377-3ba548c25482)

**Answer: `Notepad.exe`**

## 📁 Task 6: File/folder knowledge

### **Q1: When was the folder C:\Users\THM-4n6\Desktop\regripper last opened?**

I used the following command `LECmd.exe -d C:\Users\THM-4n6\Desktop\triage\C\Users\THM-4n6\AppData\Roaming\Microsoft\Windows\Recent\ --csv C:\Users\THM-4n6\Desktop`. I modified the example given in the reading.

![LECmd Command](https://github.com/user-attachments/assets/75a030c8-7a4e-4e60-986b-a83147fe4cec)

I opened the output, LECmd_Output.csv, with EZViewer. I used CTRL+F and searched for regripper. I inputted quite a few dates before finding out that LastModified had the right answer.

![Folder Access Time](https://github.com/user-attachments/assets/8c3212f6-c84b-482b-a1f5-d6d062b927bf)

**Answer: `12/1/2021 13:01`**

### **Q2: When was the above-mentioned folder first opened?**

From the above screenshot, this time we enter the date found in CreationTime.

**Answer: `12/1/2021 12:31`**

## 🔌 Task 7: External Devices/USB device forensics

### **Q1: Which artifact will tell us the first and last connection times of a removable drive?**
The answer can be found in the reading.

**Answer: `setupapi.dev.log`**

## 💭 Thoughts

I still enjoyed it as much as the first room. Definitely had a bit of setting up to do. I wished Autopsy was used more but I know there is a dedicated Autopsy room a bit later in this Digital Forensics room. I'm really enjoying, and seeing, the benefits of Eric Zimmerman's tools. It would be cool if there was a cheat sheet here too as there was just too much information to absorb. Can't wait for the Linux room!

---

## 🔐 Cybersecurity Badges

<div align="center">
  
![Windows Forensics 2](https://img.shields.io/badge/Windows-Forensics_2-blue)
![File System Analysis](https://img.shields.io/badge/File_System-Analysis-green)
![NTFS Forensics](https://img.shields.io/badge/NTFS-Forensics-red)
![Data Recovery](https://img.shields.io/badge/Data-Recovery-orange)
![Execution Analysis](https://img.shields.io/badge/Execution-Analysis-purple)
![EZ Tools](https://img.shields.io/badge/EZ_Tools-Parsing-yellow)
![Autopsy](https://img.shields.io/badge/Autopsy-Investigation-lightgrey)
![Digital Forensics](https://img.shields.io/badge/Digital-Forensics-9cf)

</div>

---

## 🛡️ Skills Demonstrated

- **NTFS File System Analysis**
- **MFT and Boot File Parsing**
- **Deleted File Recovery**
- **Prefetch Analysis**
- **Execution Timeline Reconstruction**
- **Jump Lists Analysis**
- **File Access Tracking**
- **EZ Tools Command Line Usage**
- **Autopsy File Recovery**
- **Forensic Data Processing**

---

<div align="center">

**🔍 Advanced Windows Forensics Completed** | **✅ File System Analysis Mastered** | **🛡️ Comprehensive Evidence Collection Applied**

*This investigation provided deep insights into Windows file system forensics, data recovery techniques, and execution artifact analysis using specialized forensic tools.*

</div>

