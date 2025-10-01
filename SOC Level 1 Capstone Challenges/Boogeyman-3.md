<img width="1437" height="273" alt="Screenshot 2025-10-01 at 4 46 58 PM" src="https://github.com/user-attachments/assets/2badc36a-5d50-49a0-8ead-8f1b3109aee4" />
Introduction:
Have you feared the return of the Boogeyman?

If not, you’ve stumbled on the right blog! Welcome to my weekly walkthrough. This is a comprehensive walkthrough of the Boogeyman 3 challenge from TryHackMe, the third in a series of capstone challenges for their SOC Level 1 learning path. This challenge is a digital forensics and incident response (DFIR) engagement for the final showdown with a fictional threat actor called the Boogeyman.

If you want to catch up on how we got here, check out my walkthroughs of Boogeyman 1 & Boogeyman 2 first.

TryHackMe — Boogeyman 1 Challenge Walkthrough
Email, Endpoint, & Network Forensic Investigation using Thunderbird, LNKParse3, PowerShell Logs, JQ, & Wireshark
stumblesec.medium.com

TryHackMe — Boogeyman 2 Challenge Walkthrough
Email & Endpoint Forensic Investigation using olevba, strings, & Volatility 3
stumblesec.medium.com

To unmask the Boogeyman this time, we’re all about hunting through logs within Kibana, part of the Elastic Stack, to figure out how the latest attack unfolded against an organization compromised by this persistent, shadowy threat actor. Doesn’t sound so scary, right?

Now let’s grab our flashlights and shine a light on the Boogeyman’s latest tactics, techniques, and procedures. I don’t want to ruin any of the surprises, so this walkthrough is spoiler-free, but please use it as a reference and enjoy! Thanks for reading along!

Challenge Link: https://tryhackme.com/r/room/boogeyman3

Challenge Scenario:
Due to the previous attacks of Boogeyman, Quick Logistics LLC hired a managed security service provider to handle its Security Operations Center. Little did they know, the Boogeyman was still lurking and waiting for the right moment to return.

In this room, you will be tasked to analyse the new tactics, techniques, and procedures (TTPs) of the threat group named Boogeyman.

Without tripping any security defences of Quick Logistics LLC, the Boogeyman was able to compromise one of the employees and stayed in the dark, waiting for the right moment to continue the attack. Using this initial email access, the threat actors attempted to expand the impact by targeting the CEO, Evan Hutchinson.

Question 1: What is the PID of the process that executed the initial stage 1 payload?
First things first. After starting the lab environment, enter the Elastic web console and navigate to the Analytics > Discover module. This dashboard is where we’ll be exploring the logs within the winlogbeat index.
<img width="682" height="487" alt="Screenshot 2025-10-01 at 4 48 31 PM" src="https://github.com/user-attachments/assets/7a3f44e0-8fc0-4fd2-96a4-3e13923acbf9" />
Once we get into our dashboard, we’ll have to adjust the time filters to view the logged events during the time of the incident. Fortunately, the security team reported to us that “the incident occurred between August 29 and August 30, 2023” so we can narrow the scope by modifying the dates in the time selection field.
<img width="676" height="388" alt="Screenshot 2025-10-01 at 4 49 58 PM" src="https://github.com/user-attachments/assets/af4933eb-f9db-4c96-8021-b493b15f6a8a" />
We’ll filter the first date/time, selecting Absolute and setting the start date to August 29th, 2023, at 0:00 and the end date of August 30th, 2023, at 23:30. This selection gives us all the logs ingested during the incident.
<img width="674" height="208" alt="Screenshot 2025-10-01 at 4 50 04 PM" src="https://github.com/user-attachments/assets/4f9b4984-9a39-4541-a39a-465080a87084" />
Now that we have the time period set, where do we start? Well, remember from the scenario that the initial access method was a spear phishing email that had an attachment executed by the CEO, Evan Hutchinson. The security team discovered that the attachment was an ISO file containing a “PDF” file — ProjectFinancialSummary_Q3.pdf.

We saw from the triage that Windows Explorer displayed this is an HTML application (HTA), not a PDF. So, we’re potentially looking for malicious Mshta code execution activity. But let’s start broadly and simply search for the file name by entering it into the search bar at the top of the window.

This will produce 4 events for us to review. Let’s start with the first event with the oldest time stamp. As we suspected, we see our parent file spawning mshta.exe to handle the file along with the corresponding ProcessId that we’ll need to answer Question 1.

Press enter or click to view image in full size
<img width="1070" height="704" alt="Screenshot 2025-10-01 at 4 50 15 PM" src="https://github.com/user-attachments/assets/681e489a-6005-45ce-bdd5-81290cd4f2ea" />
Before we submit our answer, note the hostname, host IP address, and username of the CEO’s compromised workstation. This will help us stay organized as we follow the attack.

WKSTN-0051 / 10.10.155.159 / evan.hutchinson
<img width="684" height="97" alt="Screenshot 2025-10-01 at 4 50 26 PM" src="https://github.com/user-attachments/assets/2629408c-866c-41d2-8251-aebf6897b03c" />
Question 2: The stage 1 payload attempted to implant a file to another location. What is the full command-line value of this execution?
Now, let’s focus on the next event in the list. We see evidence of xcopy activity which can be used to move files around the system.
<img width="681" height="227" alt="Screenshot 2025-10-01 at 4 50 33 PM" src="https://github.com/user-attachments/assets/76c13ed7-66fd-4a4e-95b0-59c103f44b19" />
Since we’re interested in the full command to understand what file was copied and to which destination, let’s make some adjustments to our dashboard and toggle some columns within our table instead of expanding the event. This will allow us to see the full process.command_line field easily and have a cleaner view moving forward.

To do this, search the Available fields column on the left-hand side and press the + button to add the process.command_line field as a column.
<img width="675" height="244" alt="Screenshot 2025-10-01 at 4 50 44 PM" src="https://github.com/user-attachments/assets/11a890ca-b19f-45fc-845d-d9de38e00132" />
You’ll notice in the screenshots below that I also added the process.parent.executable and host.hostname fields as columns too, making it far easier to see the sequence of events at a glance.
<img width="1070" height="320" alt="Screenshot 2025-10-01 at 4 50 51 PM" src="https://github.com/user-attachments/assets/4f35758d-d1f2-44c2-b297-1d1991aca76d" />
Now, revisiting the second event with this view, we’ll see the full command-line value for the xcopy activity, revealing that the attacker moved a file from the ISO to a temporary directory on WKSTN-0051.
<img width="690" height="101" alt="Screenshot 2025-10-01 at 4 50 56 PM" src="https://github.com/user-attachments/assets/f7502ca0-8e65-43e9-ab6a-0dfbf78084a5" />
Question 3: The implanted file was eventually used and executed by the stage 1 payload. What is the full command-line value of this execution?
Continuing through the timeline, let’s look at the third event. Analyzing the command line, we see rundll32 executed to register a DLL within the ISO.
<img width="1070" height="420" alt="Screenshot 2025-10-01 at 4 51 41 PM" src="https://github.com/user-attachments/assets/817a8307-df9e-478e-81f4-f9d1b05801dd" />
Question 4: The stage 1 payload established a persistence mechanism. What is the name of the scheduled task created by the malicious script?
Next, examine the last of the four events. By focusing on the process.command_line column, we can see that PowerShell is used to create a new Scheduled Task for persistence. This task executes rundll32 to register the file transferred to WKSTN-0051 via xcopy from Question 2.

Examining the Register-ScheduledTask parameter, we’ll find the name of the task in the command:
<img width="1114" height="441" alt="Screenshot 2025-10-01 at 4 51 50 PM" src="https://github.com/user-attachments/assets/e4b5b3c0-bd17-4022-9c35-8ff228f650f9" />
Question 5: The execution of the implanted file inside the machine has initiated a potential C2 connection. What is the IP and port used by this connection? (format: IP:port)
Since we’re out of events to analyze in the current search, we need to pivot and expand our scope. Since we know from the last question that the attacker is leveraging PowerShell, let’s try narrowing our search for that. Fortunately for us, Quick Logistics LLC, had deployed Sysmon on the CEO’s workstation which gives us an advantage.

Searching for PowerShell.exe and querying Sysmon Event ID 3 for “the network connection event logs TCP/UDP connections on the machine” might help find some clues leading us to uncover the command and control (C2) connection.

First, we’ll input the search.
<img width="666" height="68" alt="Screenshot 2025-10-01 at 4 52 32 PM" src="https://github.com/user-attachments/assets/b922ff3e-01a9-40c7-b135-8f4c8908f6d2" />
<img width="1063" height="459" alt="Screenshot 2025-10-01 at 4 52 40 PM" src="https://github.com/user-attachments/assets/e95fcc2d-857f-46e0-8c56-b13e3d6155b9" />
Then, enter destination.ip into the search field names box and click the field name. This will show us the top 5 values across the logs. Notice that there are three IP addresses: One is the CEO’s workstation, another is the IPv6 local loopback, and the top result is an external IP. The external IP is present in the overwhelming majority of the searched PowerShell logs. It’s suspicious that a compromised workstation would connect to an external IP address over PowerShell.

For the second half of the question, we can check the destination.port field to find the port number. Since there is only one entry, we don’t need to look any further. Now we have both the IP Address and Port of the C2 connection.
<img width="713" height="612" alt="Screenshot 2025-10-01 at 4 52 50 PM" src="https://github.com/user-attachments/assets/d648a4f6-3e34-4d0d-acaf-7abcf9588be3" />
<img width="673" height="73" alt="Screenshot 2025-10-01 at 4 52 56 PM" src="https://github.com/user-attachments/assets/a28541f5-e43e-4465-b1b0-04d624f44196" />
Question 6: The attacker has discovered that the current access is a local administrator. What is the name of the process used by the attacker to execute a UAC bypass?
Now that we’ve identified the C2 server, we need to understand how the attacker escalated privileges and bypassed user account control (UAC). Recall from Question 2 that the stage 1 payload leveraged xcopy to implant a file onto the CEO’s workstation?

Let’s search for the implanted file, review.dat, to understand what other actions were performed. Right away we’ll see some discovery activity including whoami and net.exe commands used to enumerate local group membership and the associated permissions. But that’s not what we’re interested in. Notice another odd executable in the list for the Windows Features on Demand Helper. This seems out of place, doesn’t it?

<img width="1067" height="464" alt="Screenshot 2025-10-01 at 4 53 04 PM" src="https://github.com/user-attachments/assets/caebb580-98f8-415f-a6d6-aafa6928d77c" />

Let’s research on MITRE ATT&CK to understand if this executable can be abused to bypass UAC. With a quick search, we’ll land on the page for the technique Abuse Elevation Control Mechanism: Bypass User Account Control (T1548.002) where we find the note below with a reference link:

<img width="679" height="114" alt="Screenshot 2025-10-01 at 4 53 11 PM" src="https://github.com/user-attachments/assets/3398cc1a-bb20-4c01-9c1c-042d2f3ec89e" />
For additional intelligence, let’s explore the reference link from Red Canary where we’ll learn that the executable can be abused to achieve a UAC bypass:

Processes launched by [REDACTED].exe run with elevated administrative privileges without requiring a User Account Control prompt.

This means the attacker abused the legitimate binary to execute processes as an administrator without the user account control dialogue to interfere.

Since we have discovered a known method of abusing the Features on Demand Helper binary to bypass UAC combined with the evidence that this technique was used on compromised device, we’ve found the answer to Question 6.
<img width="659" height="67" alt="Screenshot 2025-10-01 at 4 53 17 PM" src="https://github.com/user-attachments/assets/7b08a774-56d9-4dd6-b658-c8921d392706" />
Question 7: Having a high privilege machine access, the attacker attempted to dump the credentials inside the machine. What is the GitHub link used by the attacker to download a tool for credential dumping?
Now, we’ll need to discover what tool the attacker downloaded onto the victim’s device from GitHub. Jumping back to the search bar, let’s search for something broad like github.com, then refine our scope, filtering the host.ip field for the CEO’s workstation (10.10.155.159 / WKSTN-0051).
<img width="1077" height="470" alt="Screenshot 2025-10-01 at 4 53 28 PM" src="https://github.com/user-attachments/assets/92792a29-6176-4a40-9630-c6f544ad027c" />
The search reveals that the attacker downloaded the very famous credential dumping tool, Mimikatz — not good! Let’s press forward to determine what the attacker was able to access.
<img width="671" height="91" alt="Screenshot 2025-10-01 at 4 53 35 PM" src="https://github.com/user-attachments/assets/5c2dbf14-7fb3-4d0f-9919-109c3204b1bd" />
Question 8: After successfully dumping the credentials inside the machine, the attacker used the credentials to gain access to another machine. What is the username and hash of the new credential pair? (format: username:hash)
Now that we’ve discovered the attacker downloaded Mimikatz, let’s continue analyzing the logs from the CEO’s workstation focusing on the executable name of the tool inside the mimi.zip archive — mimikatz.exe.

<img width="1073" height="521" alt="Screenshot 2025-10-01 at 4 53 45 PM" src="https://github.com/user-attachments/assets/4be266fb-9a17-419b-a351-dd96e03f84d0" />
Here we’ll observe that Mimikatz dumps the credentials for users recently logged-on to the workstation (sekurlsa::logonpasswords) exposing their password hashes. Next, the attacker performs a Pass the Hash (sekurlsa::pth ) using the NTLM hash of one of the exposed administrative users — itadmin .

<img width="682" height="90" alt="Screenshot 2025-10-01 at 4 53 52 PM" src="https://github.com/user-attachments/assets/d5911920-5389-416c-9107-a70dc8f18eba" />
Question 9: Using the new credentials, the attacker attempted to enumerate accessible file shares. What is the name of the file accessed by the attacker from a remote share?
So, let’s do a quick recap. We know that the attacker compromised Evan, the CEO’s, workstation with a spear-phishing attachment. Then, the stage 1 payload performed a variety of activities to establish a foothold including using PowerShell to create persistence mechanisms, abusing living off the land binaries to elevate privileges, and dumping privileged OS credentials after downloading Mimikatz from GitHub. Now we’ll need to find what file shares the attacker found and accessed.

Based on what we know about the attacker’s tactics, techniques, and procedures (TTPs) it’s likely that they would need to download additional tools to perform file sharing enumeration in the environment.

Let’s test this theory by first filtering all events from the CEO, Evan’s, device — WKSTN-0051.quicklogistics.org. Then, we’ll narrow the search further starting with the attacker’s known technique of using PowerShell to download tools from GitHub. For this, we’ll format a query that specifies the CEO’s workstation in the host.name field and matches all fields for the term PowerShell and a wildcard search for GitHub.

<img width="650" height="59" alt="Screenshot 2025-10-01 at 4 53 57 PM" src="https://github.com/user-attachments/assets/2d4d8fd7-8eaf-4df5-abb3-acd7fef2ebc2" />

Right away, there’s something interesting. We’ll see that PowerShell downloaded PowerView.ps1 , a network reconnaissance tool, then runs the Invoke-ShareFinder cmdlet to discover accessible file shares within the domain.
<img width="1073" height="480" alt="Screenshot 2025-10-01 at 4 54 05 PM" src="https://github.com/user-attachments/assets/ecdce099-b035-443c-9e7c-d1dd0c1b6bc8" />
This discovery brings us one step closer by answering the how, but we still need to determine what was accessed. Let’s modify the original query, removing the GitHub wildcard, and zoom-out to all PowerShell activities from this workstation.
<img width="644" height="60" alt="Screenshot 2025-10-01 at 4 54 12 PM" src="https://github.com/user-attachments/assets/1fd4f3c9-82ff-4090-8965-373fc3179b65" />
<img width="1067" height="460" alt="Screenshot 2025-10-01 at 4 54 22 PM" src="https://github.com/user-attachments/assets/773a0503-41d9-40b4-966f-409021379b13" />
Bingo! We see that the attacker discovered a file share on WKSTN-1327 hosting an automation script where credentials are potentially stored to enable automation. Then, using the cat command, the attacker prints the output of this script to the console giving them access to the password within.
<img width="668" height="79" alt="Screenshot 2025-10-01 at 4 54 28 PM" src="https://github.com/user-attachments/assets/38c1dce8-48be-4bea-9fb7-7b5526578f96" />
Question 10: After getting the contents of the remote file, the attacker used the new credentials to move laterally. What is the new set of credentials discovered by the attacker? (format: username:password)
Sticking with our current search parameters, scroll up through the newer events in the timeline. Shortly, we’ll stumble upon the series of events below showing that the attacker remotely used the newly discovered credentials for allan.smith to move laterally, executing code on a second workstation.
<img width="1123" height="548" alt="Screenshot 2025-10-01 at 4 54 36 PM" src="https://github.com/user-attachments/assets/721cab17-0b02-4719-9cfc-6ab029b9ff35" />
Question 11: What is the hostname of the attacker’s target machine for its lateral movement attempt?
From the previous two steps in the analysis, we’ve already determined the hostname and user account targeted for lateral movement. Let’s check our work and move forward with the investigation.
<img width="681" height="96" alt="Screenshot 2025-10-01 at 4 54 45 PM" src="https://github.com/user-attachments/assets/0ee52ed7-ab34-48a3-b4b9-4dc7bf4205c2" />
Question 12: Using the malicious command executed by the attacker from the first machine to move laterally, what is the parent process name of the malicious command executed on the second compromised machine?
Now we’ll switch our scope to the workstation targeted for lateral movement from the last question. To do this, we’ll zoom out focusing on the Microsoft-Windows-Sysmon events again and searching Sysmon Event ID 1 or process creation events. Since we are looking for a parent/child process used for lateral movement, let’s start here and see what we find.
<img width="668" height="67" alt="Screenshot 2025-10-01 at 4 54 51 PM" src="https://github.com/user-attachments/assets/b233a8bc-d33f-4045-9062-d58339067aad" />
<img width="1061" height="416" alt="Screenshot 2025-10-01 at 4 54 58 PM" src="https://github.com/user-attachments/assets/0d60fd77-0cf9-4482-9672-b8aea5f1c45c" />
Excellent! Notice the encoded PowerShell command and that the timestamp follows directly after the use of the credentials from WKSTN-0051 ? The process.parent.executable of the PowerShell process is what we’ll need to answer Question 12.
<img width="705" height="111" alt="Screenshot 2025-10-01 at 4 55 08 PM" src="https://github.com/user-attachments/assets/2e94659e-64c8-498f-b430-53129ee15753" />
Question 13: The attacker then dumped the hashes in this second machine. What is the username and hash of the newly dumped credentials? (format: username:hash)
Staying within our current filters, we’ll see that once the attacker is connected, they perform the same patterns of system discovery as on the first workstation, including downloading Mimikatz to dump credentials on the second compromised workstation
<img width="692" height="32" alt="Screenshot 2025-10-01 at 4 55 15 PM" src="https://github.com/user-attachments/assets/fc1ab4a6-1e80-41cd-9182-5d5d34f1faeb" />
In addition to exposing the previous credentials we found back in Question 8 again, the attacker also discovers another set of administrative credentials, which may include Domain Admin privileges.
<img width="1089" height="611" alt="Screenshot 2025-10-01 at 4 55 22 PM" src="https://github.com/user-attachments/assets/8a1ffaa0-9899-410c-a895-4a4bdcb14492" />

Question 14: After gaining access to the domain controller, the attacker attempted to dump the hashes via a DCSync attack. Aside from the administrator account, what account did the attacker dump?
Keep scrolling to the newer events following the administrator account credential dump, we see the attacker performed a Pass the Hash again using the new domain admin NTLM hash to access environment’s domain controller, following-up with a DCSync attack.

Press enter or click to view image in full size
<img width="1062" height="463" alt="Screenshot 2025-10-01 at 4 55 30 PM" src="https://github.com/user-attachments/assets/3c41e6c6-6216-44e2-9b82-fe9bd9bce010" />

This gives us a good idea of where to look next. To confirm, let’s adjust our query again focusing on events from DC01 to see the full story.
<img width="661" height="62" alt="Screenshot 2025-10-01 at 4 55 38 PM" src="https://github.com/user-attachments/assets/aa795f88-ed37-4bd0-834e-4a524865601d" />

<img width="1074" height="484" alt="Screenshot 2025-10-01 at 4 55 46 PM" src="https://github.com/user-attachments/assets/3736853e-9f95-4105-bc6b-f6c7d6c585e8" />

Once again, we’ll see familiar TTPs including system/user discovery and downloading Mimikatz. By performing a DCSync attack the attacker accesses the account credentials from the previous question and another new set of credentials.

Press enter or click to view image in full size
<img width="670" height="84" alt="Screenshot 2025-10-01 at 4 55 56 PM" src="https://github.com/user-attachments/assets/3d8aa0c1-5430-4cc4-9e05-977d408a8bd5" />
Question 15: After dumping the hashes, the attacker attempted to download another remote file to execute ransomware. What is the link used by the attacker to download the ransomware binary?
Now that the attacker has achieved domain dominance, we can see that a few minutes later, the attacker downloads a ransomware binary from a remote server. This is the URL needed to answer Question 15.

<img width="1071" height="437" alt="Screenshot 2025-10-01 at 5 11 20 PM" src="https://github.com/user-attachments/assets/e0d3fd9c-647d-43bc-bdc9-f5f45473886a" />
To be thorough and fully scope the impact of the incident, let’s make a quick adjustment to our filters to understand if the ransomware binary was also executed after download.

In the search bar, we’ll enter the name of the executable, ransomboogey.exe. But we also want to understand what user accounts were used for execution and the winlog.event_id to understand if the file was executed. For this just select the user.name and winlog.event_id fields to add them to our dashboard.

First, we’ll see that the binary is executed (Sysmon Event ID 1) on DCO1 by Administrator.

Press enter or click to view image in full size
<img width="1070" height="366" alt="Screenshot 2025-10-01 at 5 11 28 PM" src="https://github.com/user-attachments/assets/32d2dca1-7966-4937-b3aa-73b602454005" />
Shortly after, we see that the ransomware is created (Sysmon Event ID 11), but not executed on the CEO's workstation, WKSTN-0051.
<img width="687" height="18" alt="Screenshot 2025-10-01 at 5 11 38 PM" src="https://github.com/user-attachments/assets/33a52d81-4ee3-4100-adc8-16df13e1c1a0" />
Finally, we’ll determine that the ransomware binary was executed on WKSTN-1327 by itadmin.
<img width="686" height="32" alt="Screenshot 2025-10-01 at 5 11 42 PM" src="https://github.com/user-attachments/assets/ec0599f9-4e97-4d22-b4f3-d82dec05bdd2" />
Whew! Now that we have fully answered all the questions and have built a solid understanding of how the latest Boogeyman attack unfolded, let’s wrap up this investigation!
<img width="700" height="86" alt="Screenshot 2025-10-01 at 5 11 47 PM" src="https://github.com/user-attachments/assets/57212db2-b946-4c6a-b759-a65dc9d56abf" />

Conclusion:
The third time’s the charm! We’ve come to the end of our frighteningly fun investigation of Boogeyman 3, facing the Boogeyman for the final time. Using our forensic skills in ELK, we learned that the Boogeyman infected CEO’s device through a spear phishing email with a malicious attachment. Then, they performed a variety of activities to establish a foothold including leveraging PowerShell to create persistence and command and control, abusing living off the land binaries to elevate privileges, dumping privileged credentials with Mimikatz, performing discovery in the environment, moving laterally, and achieving domain dominance before finally deploying ransomware. While it was a scary incident, we successfully traced the Boogeyman’s activities and now, let’s wrap this investigation — Quick Logistics LLC’s nightmare is over!

A huge thank you to TryHackMe for the excellent part III of the Boogeyman series. This challenge was the perfect way to end the year and the awesome SOC Level 1 learning path! As usual for this series, I was truly impressed with the details and narrative of this room. This one felt closer to a real-world simulation exercise than others I have completed and it really pushed me to level-up my skills in Elastic. It was really engaging to see how the Boogeyman changed tactics, techniques, and procedures between the three rooms and the stakes felt real for the fictional organization! Let’s hope we never have to deal with Boogeyman again.

Thanks for the support and going through this investigation with me. Remember, if you found this walkthrough helpful don’t forget to give it a clap! Your feedback really is invaluable and helps fuel my commitment to support your journey in the security community. Cybersecurity is a team sport and we’re in this together!

Until next week’s challenge — stay curious and be safe out there!

Tools & References:
MITRE ATT&CK: System Binary Proxy Execution: Mshta (T1218.005): https://attack.mitre.org/techniques/T1218/005/

Microsoft Learn — xcopy: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/xcopy

Microsoft Learn — rundll32: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/rundll32

MITRE ATT&CK: Scheduled Task/Job: Scheduled Task (T1053.005): https://attack.mitre.org/techniques/T1053/005/

Microsoft Learn — Sysmon: https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon

MITRE ATT&CK: https://attack.mitre.org/

MITRE ATT&CK: Abuse Elevation Control Mechanism: Bypass User Account Control (T1548.002): https://attack.mitre.org/techniques/T1548/002/

MITRE ATT&CK: OS Credential Dumping (T1003): https://attack.mitre.org/techniques/T1003/

MITRE ATT&CK: Mimikatz (S0002): https://attack.mitre.org/software/S0002/

MITRE ATT&CK: Remote System Discovery (T1018): https://attack.mitre.org/techniques/T1018/

MITRE ATT&CK: Use Alternate Authentication Material: Pass the Hash ( T1550): https://attack.mitre.org/techniques/T1550/002/

MITRE ATT&CK: OS Credential Dumping: DCSync (T1003.006): https://attack.mitre.org/techniques/T1003/006/



