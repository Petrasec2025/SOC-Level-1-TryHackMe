<img width="1408" height="164" alt="Screenshot 2025-09-30 at 4 21 29 PM" src="https://github.com/user-attachments/assets/1aec805c-bb80-47d6-b1e9-f8be75a3e1e4" />
Hey all, this is the thirty-eighth installment in my walkthrough series on TryHackMe’s SOC Level 1 path which covers the seventh and final room in this module on Security Information and Event Management, where we will come to understand how SIEM works and get comfortable creating simple and advanced search queries to look for specific answers from the ingested logs.

In this challenge room, we will investigate a compromised host.

Link: https://tryhackme.com/room/benign

Don’t be scared of this one guys… it’s benign…

Task 1: Introduction
We will investigate host-centric logs in this challenge room to find suspicious process execution. To learn more about Splunk and how to investigate the logs, look at the rooms splunk101 and splunk201.

Room Machine
Before moving forward, deploy the machine. When you deploy the machine, it will be assigned an IP. Access this room via the AttackBox, or via the VPN at MACHINE_IP. The machine will take up to 3-5 minutes to start. ll the required logs are ingested in the index win_eventlogs.

Answer the questions below:

1.1 Connect with the lab.

For this room, launch the Machine using the green icon and either start the AttackBox to connect or loadup your VPN:
<img width="700" height="569" alt="Screenshot 2025-09-30 at 4 23 13 PM" src="https://github.com/user-attachments/assets/628069c8-7534-4e46-a4ea-cc03542eb14b" />
Answer: No answer needed

Task 2: Scenario: Identify and Investigate an Infected Host
One of the client’s IDS indicated a potentially suspicious process execution indicating one of the hosts from the HR department was compromised. Some tools related to network information gathering / scheduled tasks were executed which confirmed the suspicion. Due to limited resources, we could only pull the process execution logs with Event ID: 4688 and ingested them into Splunk with the index win_eventlogs for further investigation.

About the Network Information
The network is divided into three logical segments. It will help in the investigation.

IT Department

James
Moin
Katrina
HR department

Haroon
Chris
Diana
Marketing department

Bell
Amelia
Deepak
Answer the questions below:

2.1 How many logs are ingested from the month of March, 2022?

Nice little warm-up to make sure we’re awake. Set the date range appropriately:
<img width="678" height="461" alt="Screenshot 2025-09-30 at 4 23 22 PM" src="https://github.com/user-attachments/assets/f6ba0d5f-d554-4bb0-aa1f-8e133820aa79" />
Answer: 13959

2.2 Imposter Alert: There seems to be an imposter account observed in the logs, what is the name of that user?

If we just click on the field ‘UserName’ we’ll see 10/11 results and nothing looks amiss, let’s get the extra name:
<img width="696" height="388" alt="Screenshot 2025-09-30 at 4 23 32 PM" src="https://github.com/user-attachments/assets/a38dbb8c-6194-45ba-a564-5cabe0ff3c94" />
<img width="676" height="91" alt="Screenshot 2025-09-30 at 4 23 43 PM" src="https://github.com/user-attachments/assets/a916ac4e-2724-463a-b331-0cdb562bff16" />
<img width="685" height="566" alt="Screenshot 2025-09-30 at 4 23 53 PM" src="https://github.com/user-attachments/assets/03d82ffa-968d-4fdd-8716-bbfc19d45635" />
Answer: Amel1a

2.3 Which user from the HR department was observed to be running scheduled tasks?

I found this by running the following command, there will be a better way but I’m not experienced enough in Splunk to get it and all the EventIDs are the same for this
<img width="680" height="80" alt="Screenshot 2025-09-30 at 4 24 03 PM" src="https://github.com/user-attachments/assets/8979ca31-1363-4246-bc67-9f562acc3f29" />
From here I sorted by the “CommandLine” field which made it pretty obvious as there’s only 5 commands:
<img width="692" height="621" alt="Screenshot 2025-09-30 at 4 24 11 PM" src="https://github.com/user-attachments/assets/015b921d-93ac-42ac-8ba6-94e3b66ce524" />
<img width="681" height="516" alt="Screenshot 2025-09-30 at 4 24 22 PM" src="https://github.com/user-attachments/assets/b0db5118-e73a-4e46-84d1-5f852f755cdb" />
Answer: Chris.fort

2.4 Which user from the HR department executed a system process (LOLBIN) to download a payload from a file-sharing host.

I found this pretty easily this time by going to the CommandLine and displaying rare values:
<img width="697" height="546" alt="Screenshot 2025-09-30 at 4 24 41 PM" src="https://github.com/user-attachments/assets/66c47ad3-3fb7-4c2b-90d4-0c201d8bb396" />
The query for this is:
<img width="685" height="83" alt="Screenshot 2025-09-30 at 4 24 50 PM" src="https://github.com/user-attachments/assets/f7ddfdda-2474-4596-a5a5-2ae7f077e84f" />
This looks a lot like what we’re looking for. We see the lolbin they used, certutil. We see a file, “benign.exe” and a c2 server it’s reaching out to:
<img width="691" height="366" alt="Screenshot 2025-09-30 at 4 25 00 PM" src="https://github.com/user-attachments/assets/83434133-6d85-452a-b739-ceb39f6da087" />
Searching by it gives us one result:
<img width="708" height="304" alt="Screenshot 2025-09-30 at 4 25 10 PM" src="https://github.com/user-attachments/assets/647cef1d-9168-418d-8e32-58e5a8b6a68a" />
Answer: haroon

2.5 To bypass the security controls, which system process (lolbin) was used to download a payload from the internet?

We answered this with the previous question:
<img width="690" height="201" alt="Screenshot 2025-09-30 at 4 25 17 PM" src="https://github.com/user-attachments/assets/6fdfb85b-56b5-41d4-973f-e7e8884ea5aa" />
Answer: certutil.exe

2.6 What was the date that this binary was executed by the infected host? format (YYYY-MM-DD)

Also answered in question 2.4
<img width="714" height="465" alt="Screenshot 2025-09-30 at 4 25 26 PM" src="https://github.com/user-attachments/assets/28419c15-0cb0-4ecd-89d0-4c01195f6748" />
Answer: 2022–03–04

2.7 Which third-party site was accessed to download the malicious payload?

Also answered in 2.4…
<img width="687" height="233" alt="Screenshot 2025-09-30 at 4 25 33 PM" src="https://github.com/user-attachments/assets/0d94ddc2-85c1-4c1b-8b5b-120873e3a9bc" />
Answer: controlc.com

2.8 What is the name of the file that was saved on the host machine from the C2 server during the post-exploitation phase?

Noticing a pattern?
<img width="672" height="419" alt="Screenshot 2025-09-30 at 4 25 41 PM" src="https://github.com/user-attachments/assets/fcb340d0-0063-49e7-ac09-d0ea1de61753" />

Answer: benign.exe

2.9 The suspicious file downloaded from the C2 server contained malicious content with the pattern THM{……….}; what is that pattern?

Grab the flag from the site:
<img width="659" height="544" alt="Screenshot 2025-09-30 at 4 25 49 PM" src="https://github.com/user-attachments/assets/5a877402-a0e8-4a30-885c-45de7c889e31" />
Answer: THM{KJ&*H^B0}

2.10 What is the URL that the infected host connected to?

Again, reference question 2.4:
<img width="715" height="350" alt="Screenshot 2025-09-30 at 4 25 57 PM" src="https://github.com/user-attachments/assets/b9ab8b7d-346a-4535-b085-dada8f836361" />

Answer: https://controlc.com/e4d11035

This concludes the Benign room as well as the Security Information and Event Management module, the fifth of seven modules in this SOC Level 1 Path on TryHackMe. This was a fun room and was very approachable and appropriate for our skill level. We got to see a fun example of an on startup process creation which resulted in reaching out to a c2 server to download a payload.

Thanks for joining me on this walkthrough and I’ll see you in the next one, DFIR: An Introduction, where we will also begin our next module, Digital Forensics and Incident Response. See you there!
