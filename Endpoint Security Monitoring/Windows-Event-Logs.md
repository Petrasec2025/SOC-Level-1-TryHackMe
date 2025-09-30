<img width="1438" height="313" alt="Screenshot 2025-09-30 at 12 39 58 PM" src="https://github.com/user-attachments/assets/2ce0f03b-b2f5-4328-9cd8-1d09c2f0c82f" />
After learning about the tool suite, Sysinternals, we are now going to be learning about logs, specifically Windows Event Logs. I’m familiar with it but I haven’t really delved too far in into it. It’s good they mentioned how it can be useful with SIEMs as a few of the Splunk labs in TryHackMe had me looking into logs. I think this is just a good module overall to understand a bit more about what the logs mean and how to extract relevant information from it.

I’ll be RDPing into the machine with my Kali VM, but you can use whatever you want. To RDP into the machine with Kali, I used xfreerdp /u:administrator /p:blueT3aming! /v:10.10.121.132 /dynamic-resolution where /u is the username, /p is the password /v is the IP address we are trying to connect to and /dynamic-resolution to adjust the resolution as needed. The IP address may be different for you. Once you enter that command, it will ask you if you trust the certificate. Press “Y” and then press enter and you should connect properly.
<img width="704" height="178" alt="Screenshot 2025-09-30 at 12 44 30 PM" src="https://github.com/user-attachments/assets/ad5a0e7c-b12c-486d-a3f0-316232bcb5d5" />
<img width="679" height="526" alt="Screenshot 2025-09-30 at 12 44 41 PM" src="https://github.com/user-attachments/assets/28fb3920-4e5a-4504-a4fe-1045af6ec0ef" />
Task 2 Event Viewer

1: What is the Event ID for the first recorded event?

We will be heading over to a specific log for this and the next few questions. Open event viewer in the machine by right clicking the start menu (Windows icon) at the bottom left and click event viewer. There are multiple ways to do this but I did it this way.
<img width="333" height="676" alt="Screenshot 2025-09-30 at 12 44 59 PM" src="https://github.com/user-attachments/assets/b6212ae1-0ea9-493c-9270-d3849b552005" />
Event viewer should open up. On the left side, we will navigate to our folder that we need. Expand “Applications and Services Logs” then “Microsoft” then “Windows” then “Powershell” and finally click on “Operational.” This is where we will be working in.
<img width="334" height="692" alt="Screenshot 2025-09-30 at 12 45 15 PM" src="https://github.com/user-attachments/assets/d8a0411a-f910-43c9-8b96-4171652badad" />
<img width="438" height="178" alt="Screenshot 2025-09-30 at 12 46 49 PM" src="https://github.com/user-attachments/assets/d75dce2d-582f-413e-963f-2c1b83e6317a" />
Once you are here, click on “Date and Time” to rearrange it and scroll either to the bottom or top to look for the earliest date. This specific entry’s Event ID will be the answer.
<img width="685" height="111" alt="Screenshot 2025-09-30 at 12 45 26 PM" src="https://github.com/user-attachments/assets/d11b8552-76ad-4ea1-a954-4dbbbb52c840" />
Answer: 40961

2: Filter on Event ID 4104. What was the 2nd command executed in the PowerShell session?

I did this by filtering the current log. It is located on the right side of event viewer. Click on “Filter Current Log” and a new window should pop up.
<img width="347" height="419" alt="Screenshot 2025-09-30 at 12 45 36 PM" src="https://github.com/user-attachments/assets/11302948-7eb1-4aa1-99ac-4e76869774a7" />
Enter “4104” where <All Event IDs> is at. In the picture below, you will see where I entered “4104.”
<img width="540" height="553" alt="Screenshot 2025-09-30 at 12 48 07 PM" src="https://github.com/user-attachments/assets/421b0d17-5b1c-4b2d-aae0-d1b6042b69f0" />
Click ok and the PowerShell’s Operational log will only display entries with 4104 for the Event ID. Look for the second earliest entry and look at the General tab to see what the entry says. In this case, logged what command was used.
<img width="681" height="333" alt="Screenshot 2025-09-30 at 12 48 15 PM" src="https://github.com/user-attachments/assets/bf9f16e1-63df-4187-a05e-f6ae1bf3b9e2" />
Answer: whoami

3: What is the Task Category for Event ID 4104?

Read the “Task Category” column to find the answer.
<img width="683" height="122" alt="Screenshot 2025-09-30 at 12 48 25 PM" src="https://github.com/user-attachments/assets/415128c8-63f1-4399-bf98-a62f6e3c9bd7" />
Answer: Execute a Remote Command

4: Analyze the Windows PowerShell log. What is the Task Category for Event ID 800?

Looks like we are going to be changing locations for this question. Head all the way to the bottom to find “Windows PowerShell.” If you don’t see it, the path should be Event Viewer (Local) > Applications and Services Logs > Microsoft > Windows PowerShell
<img width="348" height="698" alt="Screenshot 2025-09-30 at 12 48 36 PM" src="https://github.com/user-attachments/assets/99aede90-c240-4459-aee8-b55238a465dc" />

Now we look for an entry with 800 for their event ID and then look at the task category.
<img width="679" height="112" alt="Screenshot 2025-09-30 at 12 48 44 PM" src="https://github.com/user-attachments/assets/fecec983-4a1e-4b3d-ae4f-3fcde75440e1" />
Answer: Pipeline Execution Details

Task 3 wevtutil.exe

1: How many log names are in the machine?

We are using PowerShell now. Open PowerShell by clicking on the blue icon on the bottom left.
<img width="194" height="44" alt="Screenshot 2025-09-30 at 12 48 51 PM" src="https://github.com/user-attachments/assets/46c51ff2-b41a-418c-a9e2-fdcf48a49c8e" />
I had to use the hint for this one as I didn’t know PowerShell’s equivalent to Linux’s “Count” command. I typed in wevtutil /? first to know what options I have and to know what command I need to use. After skimming the guide, I typed in wevtutil el |Measure-Object which will display the number of logs.
<img width="381" height="126" alt="Screenshot 2025-09-30 at 12 49 08 PM" src="https://github.com/user-attachments/assets/65c26f4f-2f6b-42e1-b11a-529ab7860b74" />
Answer: 1071

2: What event files would be read when using the query-events command?

Typing in wevtutil eq /? and reading the output helped me find this answer.
<img width="464" height="40" alt="Screenshot 2025-09-30 at 12 49 19 PM" src="https://github.com/user-attachments/assets/b06478b3-1b96-4acd-886d-faef7ef39ba9" />
Answer: Event log, log file, structured query

3: What option would you use to provide a path to a log file?

Typing in wevtutil eq /? and reading the output helped me find this answer.
<img width="339" height="38" alt="Screenshot 2025-09-30 at 12 49 28 PM" src="https://github.com/user-attachments/assets/cb279286-ba63-4f70-92b7-19086292fad5" />
Answer: /lf:true

4: What is the VALUE for /q?

Typing in wevtutil eq /? and reading the output helped me find this answer
<img width="580" height="49" alt="Screenshot 2025-09-30 at 12 49 39 PM" src="https://github.com/user-attachments/assets/13c297c6-9f11-4a00-b55a-4acd22e154cc" />

Answer: XPath query

5: What is the log name?

I copy and pasted the command that was given to us from the reading into PowerShell. The code is wevtutil qe Application /c:3 /rd:true /f:text . Reading the output, we can see the log name.
<img width="220" height="26" alt="Screenshot 2025-09-30 at 12 50 00 PM" src="https://github.com/user-attachments/assets/d3f607a1-51bc-4691-bbf7-0a63448acdc0" />
Answer: Application

6: What is the /rd option for?

Typing in wevtutil eq /? and reading the output helped me find this answer.
<img width="515" height="32" alt="Screenshot 2025-09-30 at 12 50 10 PM" src="https://github.com/user-attachments/assets/648bf7d4-fb76-4f35-a4b9-3d657afb30c7" />

Answer: Event read direction

7: What is the /c option for?

Typing in wevtutil eq /? and reading the output helped me find this answer.
<img width="233" height="35" alt="Screenshot 2025-09-30 at 12 50 20 PM" src="https://github.com/user-attachments/assets/6a865d5f-a309-40f6-802f-6b9dfd7ea095" />
Answer: Maximum number of events to read

Task 4 Get-WinEvent

We will be using the online guide by Microsoft here to answer the following questions.

1: Execute the command from Example 1 (as is). What are the names of the logs related to OpenSSH?

This command is actually located in the reading. Type in Get-WinEvent -ListLog * in PowerShell and hit enter. The answer is conveniently located near the bottom for us, so no need to scroll a lot!
<img width="433" height="28" alt="Screenshot 2025-09-30 at 12 50 29 PM" src="https://github.com/user-attachments/assets/331923d5-f67f-45e3-b192-64e93453c5f8" />
Answer: OpenSSH/Admin, OpenSSH/Operational

2: Execute the command from Example 8. Instead of the string *Policy* search for *PowerShell*. What is the name of the 3rd log provider?

Grabbing the command from Example 8 in the online guide, we get Get-WinEvent -ListProvider *Policy* . We do have to change it a little bit to fit our question so our final command is Get-WinEvent -ListProvider *PowerShell* . Enter this and then press enter. We will be provided with 3 log providers. The third one is the answer.
<img width="682" height="332" alt="Screenshot 2025-09-30 at 12 50 39 PM" src="https://github.com/user-attachments/assets/3ced692b-33a4-4f42-acbb-42d863520a23" />
Answer: Microsoft-Windows-PowerShell-DesiredStateConfiguration-FileDownloadManager

3: Execute the command from Example 9. Use Microsoft-Windows-PowerShell as the log provider. How many event ids are displayed for this event provider?

Similar to the previous question, we will grab example 9’s command and modify it to fit our needs. The command is (Get-WinEvent -ListProvider Microsoft-Windows-PowerShell).Events | Format-Table Id, Description | Measure-Object where we changed the log provider to “Microsoft-Windows-PowerShell” and we added “Measure-Object” to count the number of entries for us.
<img width="683" height="116" alt="Screenshot 2025-09-30 at 12 50 52 PM" src="https://github.com/user-attachments/assets/37fa02bd-9f28-49c4-b45f-3aadeba73b81" />
Answer: 192

4: How do you specify the number of events to display?

Reading the online guide, I saw that Example 13 had an interesting parameter. It had -MaxEvents . I read a bit more and it helps display a maximum number of events.

Answer: -MaxEvents

5: When using the FilterHashtable parameter and filtering by level, what is the value for Informational?

After spending some time digging around through the online documentation, I found this page. It provided detailed explanation on how to use FilterHashtable. I also found the values and what they meant.
<img width="609" height="314" alt="Screenshot 2025-09-30 at 12 51 07 PM" src="https://github.com/user-attachments/assets/0db47532-4293-4898-ad7e-e4cbee196128" />
Answer: 4

Task 5 XPath Queries

1: Using the knowledge gained on Get-WinEvent and XPath, what is the query to find WLMS events with a System Time of 2020–12–15T01:09:08.940277500Z?

I had to dig around the documentation a lot, but the hardest part was understanding what to put in after “TimeCreated.” I was able to find a helpful article here. It’s more about scripting but it allowed me to see that I needed to add @SystemTime

Answer: Get-WinEvent -LogName Application -FilterXPath ‘*/System/Provider[@Name=”WLMS”] and */System/TimeCreated[@SystemTime=”2020–12–15T01:09:08.940277500Z”]’

2: Using Get-WinEvent and XPath, what is the query to find a user named Sam with an Logon Event ID of 4720?

I copied and edited the codes that were in the reading and came up with
Get-WinEvent -LogName Security -FilterXPath ‘*/EventData/Data[@Name=”TargetUserName”]=”Sam” and */System/EventID=4720’ .

Answer: Get-WinEvent -LogName Security -FilterXPath ‘*/EventData/Data[@Name=”TargetUserName”]=”Sam” and */System/EventID=4720’

3: Based on the previous query, how many results are returned?

Press enter when you enter the command if you did not yet. There will be two results.
<img width="672" height="89" alt="Screenshot 2025-09-30 at 12 51 20 PM" src="https://github.com/user-attachments/assets/f1d58aae-7550-4cd3-9230-c732a141f3fb" />
Answer: 2

4: Based on the output from the question #2, what is Message?

All we have to do is read the message. They are both the same!

Answer: A user account was created

5: Still working with Sam as the user, what time was Event ID 4724 recorded? (MM/DD/YYYY H:MM:SS [AM/PM])

Using the previous code as our reference, we just have to change Event ID from “4720” to “4724.” The result should be Get-WinEvent -LogName Security -FilterXPath ‘*/EventData/Data[@Name=”TargetUserName”]=”Sam” and */System/EventID=4724’ . There should only be one entry.

Answer: 12/17/2020 1:57:14 PM

6: What is the Provider Name?

The provider name will be right above the the first entry that we obtained from the previous question.
<img width="681" height="69" alt="Screenshot 2025-09-30 at 12 51 30 PM" src="https://github.com/user-attachments/assets/0f2748c3-51f2-4566-acb6-bd04fc2261a2" />
Answer: Microsoft-Windows-Security-Auditing

Task 7 Putting theory into practice

1: What event ID is to detect a PowerShell downgrade attack?

For this one, I used Google and searched it up.

Answer: 400

2: What is the Date and Time this attack took place? (MM/DD/YYYY H:MM:SS [AM/PM])

It’s not the most efficient way, but I found the answer through scrolling through the logs. I found all but one log had a host version of 5.1.

<img width="466" height="260" alt="Screenshot 2025-09-30 at 12 51 48 PM" src="https://github.com/user-attachments/assets/35e668db-247c-454a-9a36-b70ad198216b" />
The attack downgraded the version to 2.0.
<img width="420" height="267" alt="Screenshot 2025-09-30 at 12 51 57 PM" src="https://github.com/user-attachments/assets/9aad1fc3-5d17-41ff-83d5-9fa706848626" />

I started from the earliest date and then scrolled up. I just held the up arrow key as the information never changed spots, which was extremely helpful for me. Once you find this entry, look at the time stamp!

Answer: 12/18/2020 7:50:33 AM

3: A Log clear event was recorded. What is the ‘Event Record ID’?

This took me a long amount of time. I initially searched for Log Clear Event ID, which returned 1104. When I entered it in the filter, it did not produce any result. I had to keep refining my search and I had to check further down the search results where I found out that there is another event ID, 104. I found my answer here under “Event Log Manipulation.” Seems like a useful site to also keep around as a quick cheat sheet for event IDs. I entered 104 the filter and I got one result!
<img width="685" height="441" alt="Screenshot 2025-09-30 at 12 52 07 PM" src="https://github.com/user-attachments/assets/e8679343-a244-4bfd-a99b-1522149290d0" />

Answer: 27736

4: What is the name of the computer?

The screenshot above also shows the answer, just slightly below EventRecordID.

Answer: PC01.example.corp

5: What is the name of the first variable within the PowerShell command?

Probably not the “right” way to do it but I checked the hint and saw -Oldest . My assumption is that it was the oldest event. I filtered the event ID to 4104 and then looked for the oldest event.
<img width="683" height="217" alt="Screenshot 2025-09-30 at 12 52 15 PM" src="https://github.com/user-attachments/assets/cc708209-25ea-4195-9ee9-0ed7454eceee" />
Answer: $Va5w3n8

6: What is the Date and Time this attack took place? (MM/DD/YYYY H:MM:SS [AM/PM])

We can get the information under Date and Time column.

Answer: 8/25/2020 10:09:28 PM

7: What is the Execution Process ID?

Go to the Details tab and click either “Friendly View” or “XML View”
and look for the Execution Process ID. I picked Friendly View as it is easier to see but XML View has it too.

<img width="628" height="353" alt="Screenshot 2025-09-30 at 12 52 22 PM" src="https://github.com/user-attachments/assets/6d22eef1-b8e6-472e-8e6b-f480cce2333f" />

Answer: 6620

8: What is the Group Security ID of the group she enumerated?

I had to search enumeration event ID. It seems like it returned two results, 4798 and 4799. This site explained it very well to me as they sounded extremely similar. 4798 checks what group a user is a part of. 4799 checks what users are in a specific group. Since we are checking for logs that checked an entire group, 4799 is the one we use. Once we filter the event ID with 4799, we look at the details for net1.exe and the TargetSID.

<img width="637" height="361" alt="Screenshot 2025-09-30 at 12 52 28 PM" src="https://github.com/user-attachments/assets/72cb7704-6c22-42c5-9a1f-577d61a6eb55" />

Answer: S-1-5-32-544

9: What is the event ID?

4799 is the answer here because the intern checked the entire group.

Answer: 4799

Thoughts

This was a really tough room for me, coupled by the fact I could not filter the way I wanted with XPath. Furthermore, all my searching was done using the GUI. I really did wish I was able to use PowerShell more. I was able to get some good experience out of this still. I found a few sites that were really helpful and highlighted some key event IDs I should be aware of and how to utilize Event Viewer to help find threats.





