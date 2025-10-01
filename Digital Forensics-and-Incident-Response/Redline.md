<img width="1427" height="274" alt="Screenshot 2025-10-01 at 7 06 12 PM" src="https://github.com/user-attachments/assets/fe193ad2-1c7f-4abf-8d38-f9c140cebb59" />
Learn how to use Redline to perform memory analysis and to scan for IOCs on an endpoint.

I really suck at memory analysis, so this is going to be a toughie

Task 1 Introduction
Question 1:

Who created Redline?

HOW: Answer is in the above text. Linking the page for future reference.

https://fireeye.market/apps/211364

Answer: fireeye

Task 2 Data Collection
Question 1:

What data collection method takes the least amount of time?

Answer: Standard Collector

Question 2:
You are reading a research paper on a new strain of ransomware. You want to run the data collection on your computer based on the patterns provided, such as domains, hashes, IP addresses, filenames, etc. What method would you choose to run a granular data collection against the known indicators?

Answer: IOC Search Collector

Question 3:

What script would you run to initiate the data collection process? Please include the file extension.

Answer: RunRedlineAudit.bat

Question 4:

If you want to collect the data on Disks and Volumes, under which option can you find it?

Answer: disk enumeration

Question 5:

What cache does Windows use to maintain a preference for recently executed code?

HINT: Check the Redline User Guide

Answer: prefetch

Task 3 The Redline Interface
Question 1:

Where in the Redline UI can you view information about the Logged in User?

Answer: System Information

Task 4 Standard Collector Analysis
Question 1:

Provide the Operating System detected for the workstation.

HINT: Check System Information

HOW: My machine crashed, so I lost the image I had made. I found the lab one in C:\Users\Administrator\Documents\Analysis\Sessions\AnalysisSession1. When I opened that I went to System Information, and scrolled down.

Press enter or click to view image in full size
<img width="681" height="557" alt="Screenshot 2025-10-01 at 7 08 08 PM" src="https://github.com/user-attachments/assets/c5c6f760-ea30-4496-af31-b1fb1a74ebd6" />
Answer: Windows Server 2019 Standard 17763

Question 2:

Provide the BIOS Version for the workstation.

HINT: Check System Information. If the answer doesn’t match, are you using the imported analysis?

HOW: I had to make a new analysis, so I did other questions using the session already in the image to answer the other questions while I waited.

Answer: AMAZON — 1

Question 3:

What is the suspicious scheduled task that got created on the victim’s computer?

HOW: Went to tasks, and the suspicious one really stands out.
<img width="682" height="551" alt="Screenshot 2025-10-01 at 7 08 19 PM" src="https://github.com/user-attachments/assets/9c2c3965-2697-449e-858f-4556de6df626" />
Answer: MSOfficeUpdateFa.ke

Question 4:

Find the message that the intruder left for you in the task.

HINT: Check the “Comment” section for the scheduled task

HOW: It’s in the comment section of the above screenshot

Answer: THM-p3R5IStENCe-m3Chani$m

Question 5:

There is a new System Event ID created by an intruder with the source name “THM-Redline-User” and the Type “ERROR”. Find the Event ID #.

HOW: Go to events, search for “THM-Redline-User” and you will find it easily:
<img width="682" height="552" alt="Screenshot 2025-10-01 at 7 08 27 PM" src="https://github.com/user-attachments/assets/941c2f30-321e-4346-9669-5dddcb2bb323" />
Answer: 546

Question 6:

Provide the message for the Event ID.

HOW: Click on the even you found in the last question and you will get an expanded view of the message.

Answer: Someone cracked my password. Now I need to rename my puppy-++-

Question 7:

It looks like the intruder downloaded a file containing the flag for Question 8. Provide the full URL of the website.

HOW: I went to the download history, and one of the files is called flag.txt

Press enter or click to view image in full size
<img width="692" height="273" alt="Screenshot 2025-10-01 at 7 08 35 PM" src="https://github.com/user-attachments/assets/57004166-d57e-4eb8-b3a5-c03e125ab5e4" />
Answer: https://wormhole.app/download-stream/gI9vQtChjyYAmZ8Ody0AuA

Question 8:

Provide the full path to where the file was downloaded to including the filename.

HOW: All details are in the previously found file.

Answer: C:\Program Files (x86)\Windows Mail\SomeMailFolder\flag.txt

Question 9:

Provide the message the intruder left for you in the file.

HOW: Copy and paste the above path into file explorer and read the .txt file

Answer: THM{600D-C@7cH-My-FR1EnD}

Task 5 IOC Search Collector
Handy Link for the future: https://www.fireeye.com/content/dam/fireeye-www/services/freeware/ug-ioc-editor.pdf.

NOTE: I’m getting really annoyed with this one. My VM crashed again, and then I couldn’t open the IOC, so I had to run it again. It’s been over an hour of just trying to get ready to answer these questions.

I gave up and googled it. It turns out that this room is just broken, and it’s known to not work. I guess they haven’t updated it.

There is discussion for a solution (on reddit i think). Basically you need to create an IoC report from the existing scan on the machine ( C:\Users\Administrator\Documents\Analysis\Sessions\AnalysisSession1), creating a new IoC search collector doesn't work.
So for tasks 5 and 6 I recommend following this writeup, and reading how they got their answers since this is essentially crap.

Writeup: Redline - AtomicMaya/knowledge-base GitHub Wiki
For this box I used the browser based remote. Link: Redline on TryHackMe Who created Redline? Answer: FireEye What data…
github-wiki-see.page

Task 7 Endpoint Investigation
Question 1:

Can you identify the product name of the machine?

HOW:
<img width="680" height="513" alt="Screenshot 2025-10-01 at 7 08 52 PM" src="https://github.com/user-attachments/assets/f8f3825b-44ef-4814-9199-be9788f7c96b" />
Answer: \_R_E_A_D___T_H_I_S___AJYG1O_.txt

Question 3:

Find the Windows Defender service; what is the name of its service DLL?

HOW:
<img width="685" height="353" alt="Screenshot 2025-10-01 at 7 09 09 PM" src="https://github.com/user-attachments/assets/40eaae1f-63d6-4be0-bbcf-4ea1c6057093" />

<img width="513" height="223" alt="Screenshot 2025-10-01 at 7 09 15 PM" src="https://github.com/user-attachments/assets/cfea2157-ed3e-4233-9ef3-d89f8bc18a06" />

Answer: MpSvc.dll

Question 3:

The user manually downloaded a zip file from the web. Can you find the filename?

HOW:

<img width="683" height="322" alt="Screenshot 2025-10-01 at 7 09 22 PM" src="https://github.com/user-attachments/assets/2d512bcb-fe9b-4b5e-a6e9-299612570933" />

Answer: eb5489216d4361f9e3650e6a6332f7ee21b0bc9f3f3a4018c69733949be1d481.zip

Question 4:

Provide the filename of the malicious executable that got dropped on the user’s Desktop.

HOW:
<img width="712" height="200" alt="Screenshot 2025-10-01 at 7 09 30 PM" src="https://github.com/user-attachments/assets/9eedc1ee-d7bc-4e45-a9aa-c77ddb7c7d90" />
Answer: Endermanch@Cerber5.exe

Question 5:

Provide the MD5 hash for the dropped malicious executable.

HOW:
<img width="614" height="230" alt="Screenshot 2025-10-01 at 7 09 36 PM" src="https://github.com/user-attachments/assets/1355b752-aab6-49a6-b48b-78ba1547c4e5" />
Answer: fe1bc60a95b2c2d77cd5d232296a7fa4

Question 6:

What is the name of the ransomware?

HOW: Looked at the hash on virustotal.com

Answer: Cerber

CONCLUSION:
This is obviously a useful tool, but my word was this ever a pointless endeavour in this room. THM really needs to improve the stability of the VMs as there is no good reason for this to have taken me so long. For hours now I’ve just been fighting with this virtual machine.

Even including the analysis files in the image would make this so much easier. That way when your VM inevitably crashes you can just open the image and you don’t have to fuck around for 30 minutes recapturing everything, and then fighting with it further.
