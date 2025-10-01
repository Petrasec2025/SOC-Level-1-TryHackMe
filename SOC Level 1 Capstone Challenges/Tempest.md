<img width="1372" height="311" alt="Screenshot 2025-10-01 at 3 09 08 PM" src="https://github.com/user-attachments/assets/43fb513f-c970-4857-9cf7-0472dc34f80c" />
This room is by TryHackMe and ar33zy and aims to introduce the process of analysing endpoint and network logs from a compromised asset.

Task 3 | Preparation — Tools and Artifacts
Q — What is the SHA256 hash of the capture.pcapng file?

Open a Powershell terminal, and navigate to the Incident Files folder:
<img width="678" height="527" alt="Screenshot 2025-10-01 at 3 12 33 PM" src="https://github.com/user-attachments/assets/e13d88b3-eec2-4437-916e-e54a80ebf02d" />
Run the example command: Get-FileHash -Algorithm SHA256.\capture.pcapng

The hash is shown:
<img width="681" height="110" alt="Screenshot 2025-10-01 at 3 12 42 PM" src="https://github.com/user-attachments/assets/f5debd63-27c8-46e8-b903-7c7ace730902" />
Q — What is the SHA256 hash of the sysmon.evtx file?

Reuse the same command and replace the file. The sysmon.evtx is in the same folder, use autocomplete (tab) to select the correct file.

Get-FileHash -Algorithm SHA256.\sysmon.evtx

Q — What is the SHA256 hash of the windows.evtx file?

A final copypasta: Get-FileHash -Algorithm SHA256.\windows.evtx

Task 4 | Initial Access — Malicious Document
We will follow the Investigation Guide and use Sysmon, the significant data source listed.

Go to Tools -> EvtxEcmd in the terminal:

Run the example command to parse the .evtx file to CSV:

.\EvtxECmd.exe -f ‘C:\Users\user\Desktop\Incident Files\sysmon.evtx’ — csv ‘C:\Users\user\Desktop\Incident Files’ — csvf sysmon.csv
<img width="683" height="424" alt="Screenshot 2025-10-01 at 3 12 52 PM" src="https://github.com/user-attachments/assets/90b4e8c4-dab4-4a19-b8c3-417c736dde76" />
Go to Local Disk C: -> Tools -> Timeline Explorer, open sysmon.csv.

Q— The user of this machine was compromised by a malicious document. What is the file name of the document?

The question notes that the malicious document has a .doc extension.

In Sysmon Viewer, filter for .doc, scrolling along columns there is a .doc file listed in the Payload contents column:
<img width="683" height="375" alt="Screenshot 2025-10-01 at 3 13 01 PM" src="https://github.com/user-attachments/assets/7a6a6dfa-1753-44c1-8c54-2634a5fe5e96" />
Q — What is the name of the compromised user and machine?

Check the User name column, reformat for answer input is required:
<img width="683" height="75" alt="Screenshot 2025-10-01 at 3 13 10 PM" src="https://github.com/user-attachments/assets/af4a652b-e61a-4efb-823c-26975745d649" />
Q — What is the PID of the Microsoft Word process that opened the malicious document?

In the Executable Info column, there is a reference to WINWORD.exe. This is the Microsoft Word executable. The PID can be found in the PayloadData1 column for this row:
<img width="677" height="261" alt="Screenshot 2025-10-01 at 3 13 18 PM" src="https://github.com/user-attachments/assets/00340f13-e160-40f1-bc89-cf917e99d002" />
Q — Based on Sysmon logs, what is the IPv4 address resolved by the malicious domain used in the previous question?

The Investigation guide suggests following the child processes of WinWord.exe.

Search for WinWord.exe. There is a column called Map description and rows with the value “Network connection”:
<img width="673" height="202" alt="Screenshot 2025-10-01 at 3 13 27 PM" src="https://github.com/user-attachments/assets/3cb4f9f9-6e4e-4561-89cd-8aa5bda5198f" />
In Payload Data6 there is a DestinationIp value listed:
<img width="677" height="141" alt="Screenshot 2025-10-01 at 3 13 35 PM" src="https://github.com/user-attachments/assets/448bb3ae-fae9-4d09-9953-00c3cfe5d567" />
Q — What is the base64 encoded string in the malicious payload executed by the document?

When Word opens the document the malicious payload runs. This means Word is the parent process for the child executable process.

From the Investigation Guide: Use filters such as ParentProcessID or ProcessID to correlate the relationship of each process.

We need to filter for Word as the ParentProcessID (496):
<img width="683" height="372" alt="Screenshot 2025-10-01 at 3 13 45 PM" src="https://github.com/user-attachments/assets/b648f5f4-04d1-4684-9f95-6e1db64a2281" />

In the Executable Info column, the base64 encoded string is shown (double-click on the row to expand the details):

Press enter or click to view image in full size
<img width="684" height="313" alt="Screenshot 2025-10-01 at 3 13 53 PM" src="https://github.com/user-attachments/assets/333c34de-7c1e-444d-9f9b-fc37bda02917" />
Q — What is the CVE number of the exploit used by the attacker to achieve a remote code execution?

The question hint suggests observing the process that executed the malicious base64 payload.

In the same row as the base64 encoded string, there is an executable named “msdt.exe”

Press enter or click to view image in full size
<img width="712" height="191" alt="Screenshot 2025-10-01 at 3 14 00 PM" src="https://github.com/user-attachments/assets/6047dde6-425a-44f6-818d-3474f3214a4e" />


I Googled CVE msdt.exe. This article outlines: “a remote code execution vulnerability exists when MSDT is called using the URL protocol from a calling application such as Word”.

Task 5 | Initial Access — Stage 2 execution
Q — The malicious execution of the payload wrote a file on the system. What is the full target path of the payload?

The investigation guide states: “Process Creation (Event ID 1) and File Creation (Event ID 11) succeeding the document execution are worth checking”.

Filtering for the doc reveals it was first seen on the system at 2022–06–20 17:12:58.

Looking at Event ID 11 values after this time, the Payload Data4 column shows the target file name. After sifting through, there is one with a file named “update.zip” which felt malware-shaped to me:
<img width="681" height="330" alt="Screenshot 2025-10-01 at 3 14 07 PM" src="https://github.com/user-attachments/assets/2095067b-d97e-4dd0-80c3-3bd8ca1bd653" />
Q — The implanted payload executes once the user logs into the machine. What is the executed command upon a successful login of the compromised user?

Format: Remove the double quotes from the log.

I finally realised I could filter for the word “explorer” for Parent Process and not have to fish out a Parent Process ID (doh).
<img width="684" height="245" alt="Screenshot 2025-10-01 at 3 14 28 PM" src="https://github.com/user-attachments/assets/bfb90d88-c40f-4101-be9c-d2fa88137b71" />

The user who downloaded the suspicious file is benimaru. Filter for benimaru as the user and processes with the Parent Process “explorer.exe”

(From Investigation guide: Child processes of explorer.exe within the event timeframe could be significant.)

In the Executable Info column, there is a PowerShell command executing:
<img width="681" height="184" alt="Screenshot 2025-10-01 at 3 14 36 PM" src="https://github.com/user-attachments/assets/81cf0e20-7d7c-4d1e-934a-d974c81d640c" />
Q — Based on Sysmon logs, what is the SHA256 hash of the malicious binary downloaded for stage 2 execution?

The previous command included an executable named “first.exe.” I filtered for that. The binary “first.exe” has a record in the downloads folder. I took the SHA256 hash from this row.
<img width="691" height="445" alt="Screenshot 2025-10-01 at 3 14 44 PM" src="https://github.com/user-attachments/assets/738bdd91-494c-4675-9ed4-6f1d380dc819" />
Q — The stage 2 payload downloaded establishes a connection to a c2 server. What is the domain and port used by the attacker?

While looking at the first.exe results, I spotted a reference to an IP address using port 8080 which is commonly used for web servers:
<img width="688" height="164" alt="Screenshot 2025-10-01 at 3 14 54 PM" src="https://github.com/user-attachments/assets/f9cb6e1c-eaaf-478d-a709-1997d0d4328a" />
The question asked for a domain, not an IP. I filtered through the DNS log and there were multiple references to a strange domain which I thought looked like a C2 server possibility.
<img width="681" height="219" alt="Screenshot 2025-10-01 at 3 15 02 PM" src="https://github.com/user-attachments/assets/92bf7ae6-a68c-4543-a535-c31559fae52e" />
Task 6 | Initial Access Malicious Document Traffic
Q — What is the URL of the malicious payload embedded in the document?

The investigation guide suggests finding network events related to the harvested domains and IP addresses

Open the packet capture in Wireshark, and filter for http traffic:

The payload will execute after the document is downloaded. I found the GET request that retrieves the document and looked at the subsequent traffic. There are multiple GET requests to the Index page of a suspicious domain. It’s likely fetching malicious code:
<img width="690" height="136" alt="Screenshot 2025-10-01 at 3 15 10 PM" src="https://github.com/user-attachments/assets/3d492412-c91d-4246-abc4-956bfca39078" />
Click into the packet to find the full URL:
<img width="689" height="170" alt="Screenshot 2025-10-01 at 3 15 17 PM" src="https://github.com/user-attachments/assets/c3fb2999-aef0-4277-9b24-9cd8f0185444" />
Q — What is the encoding used by the attacker on the c2 connection?

If we’re looking for encoding, we’re looking for something like ASCII, Unicode, Binary, Base64, or UTF-8/16.

Filter for the c2 domain in WireShark: http contains "resolvecyber"
<img width="686" height="183" alt="Screenshot 2025-10-01 at 3 15 24 PM" src="https://github.com/user-attachments/assets/a791717f-3aef-4323-a564-56c0a891bb04" />
That looks like base64 to me, check in CyberChef by copying one of the URL queries. The q= Is the URL parameter, followed by base64:
<img width="718" height="356" alt="Screenshot 2025-10-01 at 3 15 31 PM" src="https://github.com/user-attachments/assets/50950735-20c5-417a-a7cc-7bcebba735fd" />
Q — The malicious c2 binary sends a payload using a parameter that contains the executed command results. What is the parameter used by the binary?

This is the URL parameter we highlighted in the previous question.

Q — The malicious c2 binary connects to a specific URL to get the command to be executed. What is the URL used by the binary?

This is shown the the Request URI path of the packets with the malicious binary:
<img width="700" height="184" alt="Screenshot 2025-10-01 at 3 15 38 PM" src="https://github.com/user-attachments/assets/f5b89097-427e-4ba4-b92e-dfcbd5cc478d" />
Q — What is the HTTP method used by the binary?

This is confirmed in the protocol column and filter.

Q — Based on the user agent, what programming language was used by the attacker to compile the binary?

Format: Answer in lowercase

Inspect a packet without an executable in the URL, the user-agent is shown:
<img width="690" height="179" alt="Screenshot 2025-10-01 at 3 15 44 PM" src="https://github.com/user-attachments/assets/f3c3bc88-54ca-4d95-af60-e21b1338c1bd" />
I hadn’t heard of this programming language. I imagine its speedy compiling and support for front-end and back-end would make it useful for this malicious executable.

Task 7 | Discovery — Internal Reconnaissance
Q — The attacker was able to discover a sensitive file inside the machine of the user. What is the password discovered on the aforementioned file?

I updated my filter to http contains "/9ab62b5" look for the executable commands.

I broke the GET requests into a separate column and pasted them into CyberChef:
<img width="686" height="383" alt="Screenshot 2025-10-01 at 3 15 51 PM" src="https://github.com/user-attachments/assets/d2116127-551d-4497-8cdf-362b30314cde" />
I updated my filter to look for "/9ab62b5?q=” and exported the selected packets as a CSV so I could look at just the GET requests in Timeline Explorer.

To do this, select the packets -> File -> Export Packet Dissections -> As CSV.
<img width="708" height="227" alt="Screenshot 2025-10-01 at 3 15 57 PM" src="https://github.com/user-attachments/assets/77c45897-4c7c-4a21-ae7d-3af2cf96234d" />
I opened the CSV in Timeline Explorer and decoded the base64 strings using CyberChef to find the exposed password:
<img width="687" height="343" alt="Screenshot 2025-10-01 at 3 16 03 PM" src="https://github.com/user-attachments/assets/6bc4b102-9db1-4c64-a71b-ce066cdf00f6" />
<img width="687" height="310" alt="Screenshot 2025-10-01 at 3 16 26 PM" src="https://github.com/user-attachments/assets/add12dcf-9397-4170-a8a0-8f26f4e892f4" />
Q — The attacker then enumerated the list of listening ports inside the machine. What is the listening port that could provide a remote shell inside the machine?

To decode all the commands, use Wordpad to remove all non-base64 characters with “find and replace”.
<img width="690" height="352" alt="Screenshot 2025-10-01 at 3 16 31 PM" src="https://github.com/user-attachments/assets/9df6e37e-0cb5-4145-8317-7e7fcab2f743" />

Then paste the strings into CyberChef and decode:

<img width="727" height="367" alt="Screenshot 2025-10-01 at 3 16 40 PM" src="https://github.com/user-attachments/assets/bde5440f-cf8c-414a-a295-dc16da59cedc" />
In the netstat scan, port 5985 is listening. Port 5985 is used by Windows Remote management so it could be used for a remote shell.

Q — The attacker then established a reverse socks proxy to access the internal services hosted inside the machine. What is the command executed by the attacker to establish the connection?

I couldn’t find any commands that show this path in the base64 decode, so I went back to the Sysmon CSV file to see if there were any references to “socks”

Press enter or click to view image in full size
<img width="689" height="136" alt="Screenshot 2025-10-01 at 3 16 45 PM" src="https://github.com/user-attachments/assets/b45e3878-b1a8-4e68-baae-d902120a6451" />
Q — What is the SHA256 hash of the binary used by the attacker to establish the reverse socks proxy connection?

In Timeline Explorer the SHA256 hash is shown in column Payload Data3 in the same row.

Q — What is the name of the tool used by the attacker based on the SHA256 hash? Provide the answer in lowercase.

Look up the hash value on VirusTotal:
<img width="664" height="367" alt="Screenshot 2025-10-01 at 3 19 51 PM" src="https://github.com/user-attachments/assets/3bd6486a-47b4-410b-8fe0-39f94b5d8b0d" />
Q — The attacker then used the harvested credentials from the machine. Based on the succeeding process after the execution of the socks proxy, what service did the attacker use to authenticate?

Format: Answer in lowercase

To find the succeeding process, I removed the “socks” filter and scrolled down:
<img width="679" height="190" alt="Screenshot 2025-10-01 at 3 19 58 PM" src="https://github.com/user-attachments/assets/5995c225-4476-48b2-a051-bc037b1514ed" />
Google confirmed that wsmprovhost.exe is Powershell but that’s not the answer.

I then Googled “what service uses wsmprovhost.exe” and got the answer, with persistent Googling.

Task 8 | Privilege Escalation — Exploiting Privileges
Q — After discovering the privileges of the current user, the attacker then downloaded another binary to be used for privilege escalation. What is the name and the SHA256 hash of the binary?

Format: binary name,SHA256 hash

I searched for “wsmprovhost.exe” in Timeline Explorer to see subsequent downloads. There is one and the SHA256 hash checked out as malicious in VirusTotal:
<img width="693" height="238" alt="Screenshot 2025-10-01 at 3 20 04 PM" src="https://github.com/user-attachments/assets/be2b07ba-dcb1-4499-9742-da3bfe8987ab" />
Q — Based on the SHA256 hash of the binary, what is the name of the tool used?

Format: Answer in lowercase

Check out the names section on VirusTotal:
<img width="683" height="326" alt="Screenshot 2025-10-01 at 3 20 11 PM" src="https://github.com/user-attachments/assets/d234a9b2-d1e7-47f6-8579-fe6b6fca299c" />
Q — The tool exploits a specific privilege owned by the user. What is the name of the privilege?

Check out this GitHub repo that pops up after Googling “printspoofer user privilege exploit”.

Q — Then, the attacker executed the tool with another binary to establish a c2 connection. What is the name of the binary?

I searched for child processes of the “spf.exe” binary:
<img width="692" height="102" alt="Screenshot 2025-10-01 at 3 20 18 PM" src="https://github.com/user-attachments/assets/d0956fd1-0a7d-4a3b-b553-8c0e60ff9100" />
Q — The binary connects to a different port from the first c2 connection. What is the port used?

The original port used was 80 and we know the IP the binary connects to is 167[.]71[.]222[.]162.

Filter for both values in WireShark and the other port is shown:
<img width="702" height="195" alt="Screenshot 2025-10-01 at 3 20 24 PM" src="https://github.com/user-attachments/assets/b4895a16-43bf-4148-9a90-ae22f8e13810" />
Task 9 | Actions on Objective — Fully-owned Machine
Q — Upon achieving SYSTEM access, the attacker then created two users. What are the account names?

Format: Answer in alphabetical order — comma delimited

The command to add a user isnet user, looking through the base64 decoded commands and the new usernames are shown:
<img width="683" height="297" alt="Screenshot 2025-10-01 at 3 20 32 PM" src="https://github.com/user-attachments/assets/1f18882e-9a59-4a09-be42-ae2cbc79ca07" />
Q — Prior to the successful creation of the accounts, the attacker executed commands that failed in the creation attempt. What is the missing option that made the attempt fail?

Looking through the decoded commands, I could see messages stating errors with net user commands, so I tried /add as without this the user addition won’t work:
<img width="675" height="233" alt="Screenshot 2025-10-01 at 3 20 39 PM" src="https://github.com/user-attachments/assets/62859841-aa10-4022-b775-7bd7aaf41363" />
Q — Based on windows event logs, the accounts were successfully created. What is the event ID that indicates the account creation activity?

To check, Google “windows event ID succesful user creation”

Q — The attacker added one of the accounts in the local administrator’s group. What is the command used by the attacker?

Scrolling down the Executable column, there is a local group administrators command:
<img width="692" height="213" alt="Screenshot 2025-10-01 at 3 20 44 PM" src="https://github.com/user-attachments/assets/00ded84c-7f7a-4eae-8835-67050f70c566" />
Q — Based on windows event logs, the account was successfully added to a sensitive group. What is the event ID that indicates the addition to a sensitive local group?

Googling the hint prompt returns the correct event ID.

Q — After the account creation, the attacker executed a technique to establish persistent administrative access. What is the command executed by the attacker to achieve this?

My understanding is that sc.exe is used to control services in the Windows command line. I looked for this in the Sysmon log, there are 2 references.

Looking through the base64 converted commands, only the 2nd version was successful. The successful command is the answer to this question:
<img width="687" height="230" alt="Screenshot 2025-10-01 at 3 20 51 PM" src="https://github.com/user-attachments/assets/5a6168df-e2f8-4293-9b71-0632f297148c" />
Phew! This room challenged my new analysis skills. The struggle improved my understanding of parent and child processes, the purpose of key Windows processes and event IDs.

Thank you for reading.



















