# Osquery Room Walkthrough

![Room Banner](https://github.com/user-attachments/assets/703bae8c-ec4f-47e1-9aa5-f6359c7e2905)

## 🏆 Badges
![Endpoint](https://img.shields.io/badge/Endpoint-Security_Monitoring-0078D6?style=for-the-badge&logo=shield&logoColor=white)
![Database](https://img.shields.io/badge/Database-SQL_Queries-00C800?style=for-the-badge&logo=database&logoColor=white)
![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-FFFF00?style=for-the-badge)
![Platform](https://img.shields.io/badge/Platform-TryHackMe-FF0000?style=for-the-badge&logo=tryhackme&logoColor=white)
![Completion](https://img.shields.io/badge/Completion-100%25-00FF00?style=for-the-badge)
![Tools](https://img.shields.io/badge/Tools-Osquery-800080?style=for-the-badge)

## Overview
We finally finished Sysmon last time. Only a couple more logging related rooms before we move on to the SIEM room!

---

## Task 2 Connect with the Lab

I decided to RDP into this lab.

---

## Task 3 Osquery: Interactive Mode

### Question 1: How many tables are returned when we query "table process" in the interactive mode of Osquery?
First, I opened powershell and typed in osqueryi in the terminal. Doing that should put you in the Osquery tool.

![Osquery Launch](https://github.com/user-attachments/assets/01bc4c8f-b5bf-4e06-89a8-92eae0a4ad5e)

From there, I typed `.table process` and counted the number of results.

![Process Tables](https://github.com/user-attachments/assets/31ebff9e-66b5-45b7-88ac-a2080ff6541d)

**Answer:** `3`

### Question 2: Looking at the schema of the processes table, which column displays the process id for the particular process?
I just kind of know the answer is already "pid" but we can try to figure it out by typing `.schema process` and view all the columns associated in each table. From there, I would search up a few things I don't know, such as pid, uid, and more.

![Process Schema](https://github.com/user-attachments/assets/2e4b68db-a28e-4e7d-93c1-d4998bebd471)

**Answer:** `pid`

### Question 3: Examine the .help command, how many output display modes are available for the .mode command?
For this one, I just looked at the reading as the reading does the .help command for us.

**Answer:** `5`

---

## Task 4 Schema Documentation

### Question 1: In Osquery version 5.5.1, how many tables are returned for the Windows operating system?
We will be using the [Osquery Schema Documentation](https://osquery.io/schema/5.5.1/) for this question. We will filter by "Windows" only.

![Windows Filter](https://github.com/user-attachments/assets/4d78bef8-dfab-4f29-ab5c-a4fca62d4b2a)

After that, the results should show on the top left of the page.

![Windows Table Count](https://github.com/user-attachments/assets/900cb112-c528-4751-b91a-2a057314f5bf)

**Answer:** `56`

### Question 2: In Osquery version 5.5.1, how many tables for MAC OS are available?
This will be very similar to above except we only check MacOS and remove the other two OS options. Answer will be displayed in the same area.

**Answer:** `180`

### Question 3: In the Windows Operating system, which table is used to display the installed programs?
Since it asked for "Windows Operation System," I decided to set my filter to Windows only. From there, I decided to check if there was any table called "programs" and there was!

![Programs Table](https://github.com/user-attachments/assets/75214d60-ecd9-4a24-b85d-cc79614f266c)

**Answer:** `Programs`

### Question 4: In Windows Operating system, which column contains the registry value within the registry table?
Keeping my filter on Windows only, I looked for a table called "registry" and it did exist. From there, I just had to look at the column name and descriptions.

![Registry Data Column](https://github.com/user-attachments/assets/f28b67e7-4ced-47d6-bb33-e97cf046f720)

**Answer:** `Data`

---

## Task 5 Creating SQL queries

### Question 1: Using Osquery, how many programs are installed on this host?
I used the following command `SELECT count(*) FROM programs;`. The count(*) counts the entry in the table called programs.

**Answer:** `19`

### Question 2: Using Osquery, what is the description for the user James?
The following command will help find the answer `SELECT description from users WHERE username='James';`. We are displaying only the description column from the table users. We only want to display results where username column has James.

**Answer:** `Creative Artist`

### Question 3: When we run the following search query, what is the full SID of the user with RID '1009'?
Simply copy the code given in the reading `select path, key, name from registry where key = 'HKEY_USERS';` and paste it into Osquery. SID stands for Security Identifier.

**Answer:** `S-1-5-21-1966530601-3185510712-10604624-1009`

### Question 4: When we run the following search query, what is the Internet Explorer browser extension installed on this machine?
Copy the code given in the reading `select * from ie_extensions;` and paste it in Osquery. It seems like it wants the path of the extension.

**Answer:** `C:\Windows\System32\ieframe.dll`

### Question 5: After running the following query, what is the full name of the program returned?
Copy the code given in the reading `select name,install_location from programs where name LIKE '%wireshark%';` and paste it into Osquery.

**Answer:** `Wireshark 3.6.8 64-bit`

---

## Task 6 Challenge and Conclusion

### Question 1: Which table stores the evidence of process execution in Windows OS?
Looks like we need the documentation for this.

I looked for a long time but couldn't find it. I used the video that is in the room to follow and see how they found it.

**Answer:** `userassist`

### Question 2: One of the users seems to have executed a program to remove traces from the disk; what is the name of that program?
Once I read up on userassist. I found out that it tells us how many times a program has been executed. The question asks what program was executed. This gave me a hint that I need to use userassist. I did `select * from userassist;` to help find my answer.

![DiskWipe Program](https://github.com/user-attachments/assets/7a6e9277-c0cc-49b2-b301-1340a330538a)

**Answer:** `DiskWipe.exe`

### Question 3: Create a search query to identify the VPN installed on this host. What is name of the software?
What I did first was look at documentation for the correct table. Programs may give us what we need. From there, I looked at the schema with `.schema programs`. "Name" is what we may use since it'll help make the results look cleaner. The command I used was `SELECT name from programs;`. This showed a list of programs we have installed. I found a name I'm familiar with.

![ProtonVPN](https://github.com/user-attachments/assets/3bfcf49b-e03b-4226-a504-a843ec8edd1e)

**Answer:** `ProtonVPN`

### Question 4: How many services are running on this host?
I tried 69 first when I did my first command `select count(name) from services where status='RUNNING';` but it was wrong. I then typed `select name, status from services;` to let me see the entire data. There was only two types of services, ones that were running and ones that were stopped. I decided to try `select count(name) from services;` to give me the entire data and enter that and oddly enough, that was the answer. Although I'm fairly certain this should be wrong.

![Services Count](https://github.com/user-attachments/assets/058a18de-00ee-4245-ad30-c80da3ccee80)

**Answer:** `214`

### Question 5: A table autoexec contains the list of executables that are automatically executed on the target machine. There seems to be a batch file that runs automatically. What is the name of that batch file (with the extension .bat)?
I had to google how to use the wildcard (%) since I couldn't get it to work. This site proved helpful. I followed the example codes and came up with `select path from autoexec where path like '%.bat';` for myself. The latter part is basically saying "The path can be anything but it must end in .bat." We got two results! I copied only the program name.

![Batch Files](https://github.com/user-attachments/assets/9ea1b182-cc10-4699-a0ac-4702c61b1f0e)

**Answer:** `batstartup.bat`

### Question 6: What is the full path of the batch file found in the above question? (Last in the List)
We have the answer from the above image. All I had to do is copy the last in the list.

**Answer:** `C:\Users\James\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup\batstartup.bat`

---

## 🎯 Final Badges
![SQL](https://img.shields.io/badge/SQL-Query_Skills-FF69B4?style=for-the-badge)
![Forensics](https://img.shields.io/badge/Forensics-Endpoint_Analysis-000080?style=for-the-badge)
![Room](https://img.shields.io/badge/Room-Osquery-FF4500?style=for-the-badge)
![Windows](https://img.shields.io/badge/Windows-Investigation-008080?style=for-the-badge)

## Thoughts & Conclusion

Wow that was pretty fun. Wasn't too particularly difficult, and was a great refresher for SQL querying that I learned a while back. I still believe the answer regarding the number of services running was wrong but as always, I'm not too sure if I misunderstood or just due to my lack of experience. Only one more Endpoint Security Monitoring room to go!

The room provided excellent hands-on experience with Osquery, teaching valuable skills in endpoint investigation using SQL queries. The practical exercises helped reinforce how to query system information, analyze installed programs, track user activity, and identify potential security threats through systematic database queries.

---

**Room Link:** [https://tryhackme.com/room/osqueryf8](https://tryhackme.com/room/osqueryf8)
