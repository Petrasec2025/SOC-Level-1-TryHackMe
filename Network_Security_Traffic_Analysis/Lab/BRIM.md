BRIM is an open-source desktop application that processes pcap files and logs files. Its primary focus is providing search and analytics. In this room, you will learn how to use Brim, process pcap files and investigate log files to find the needle in the haystack! This room expects you to be familiar with basic security concepts and processing Zeek log files. We suggest completing the "Network Fundamentals" path and the "Zeek room" before starting working in this room. 

A VM is attached to this room. You don't need SSH or RDP; the room provides a "Split View" feature. Exercise files are located in the folder on the desktop. 
NOTE: DO NOT directly interact with any domains and IP addresses in this room.

<img width="789" height="521" alt="Screenshot 2025-09-25 at 2 53 11 PM" src="https://github.com/user-attachments/assets/552afa44-509a-4816-8ad2-b5010170916c" />

Answer the questions below
Read the task above

<img width="671" height="184" alt="Screenshot 2025-09-25 at 2 49 19 PM" src="https://github.com/user-attachments/assets/0acf3643-cd62-49b9-8fee-882f85f9a149" />

The screen should split in half if it doesn’t go to the top of the page. You will see a blue button labeled Show Split View, click this button.

<img width="679" height="148" alt="Screenshot 2025-09-25 at 2 50 01 PM" src="https://github.com/user-attachments/assets/d06e0999-9e82-45e0-af35-8162cd76a937" />
The screen should be split now, you have to wait for the VM to load. When it is finished loading it will look like it does below. You are ready to continue with the tasks ahead.

<img width="683" height="349" alt="Screenshot 2025-09-25 at 2 50 54 PM" src="https://github.com/user-attachments/assets/6b2c7ba7-aeb7-4af6-a573-d33f204b9eed" />

Task 2 What is Brim?

<img width="949" height="368" alt="Screenshot 2025-09-25 at 2 46 23 PM" src="https://github.com/user-attachments/assets/188a9b52-030f-44d8-a2cc-ffc9f6949c6c" />

What is Brim?

Brim is an open-source desktop application that processes pcap files and logs files, with a primary focus on providing search and analytics. It uses the Zeek log processing format. It also supports Zeek signatures and Suricata Rules for detection.

It can handle two types of data as an input;

Packet Capture Files: Pcap files created with tcpdump, tshark and Wireshark like applications.
Log Files: Structured log files like Zeek logs.
Brim is built on open-source platforms:

Zeek: Log generating engine.
Zed Language: Log querying language that allows performing keywoırd searches with filters and pipelines.
ZNG Data Format: Data storage format that supports saving data streams.
Electron and React: Cross-platform UI.
Why Brim?

Ever had to investigate a big pcap file? Pcap files bigger than one gigabyte are cumbersome for Wireshark. Processing big pcaps with tcpdump and Zeek is efficient but requires time and effort. Brim reduces the time and effort spent processing pcap files and investigating the log files by providing a simple and powerful GUI application.

Brim vs Wireshark vs Zeek

While each of them is powerful and useful, it is good to know the strengths and weaknesses of each tool and which one to use for the best outcome. As a traffic capture analyser, some overlapping functionalities exist, but each one has a unique value for different situations.

The common best practice is handling medium-sized pcaps with Wireshark, creating logs and correlating events with Zeek, and processing multiple logs in Brim.
<img width="674" height="427" alt="Screenshot 2025-09-25 at 2 54 39 PM" src="https://github.com/user-attachments/assets/22ba1499-5f46-4168-a75f-6e07e633337a" />
Task 3 The Basics
Landing Page

Once you open the application, the landing page loads up. The landing page has three sections and a file importing window. It also provides quick info on supported file formats.

Pools: Data resources, investigated pcap and log files.
Queries: List of available queries.
History: List of launched queries.
Pools and Log Details

Pools represent the imported files. Once you load a pcap, Brim processes the file and creates Zeek logs, correlates them, and displays all available findings in a timeline, as shown in the image below.
<img width="906" height="452" alt="Screenshot 2025-09-25 at 2 55 00 PM" src="https://github.com/user-attachments/assets/ba1976a9-ce8a-491a-97f8-eab376a9548f" />
The timeline provides information about capture start and end dates. Brim also provides information fields. You can hover over fields to have more details on the field. The above image shows a user hovering over the Zeek’s conn.log file and uid value. This information will help you in creating custom queries. The rest of the log details are shown in the right pane and provides details of the log file fields. Note that you can always export the results by using the export function located near the timeline.
<img width="436" height="411" alt="Screenshot 2025-09-25 at 2 55 08 PM" src="https://github.com/user-attachments/assets/47484a45-24dd-4efa-acdd-7899ea89c58c" />
You can correlate each log entry by reviewing the correlation section at the log details pane (shown on the left image). This section provides information on the source and destination addresses, duration and associated log files. This quick information helps you answer the “Where to look next?” question and find the event of interest and linked evidence.

You can also right-click on each field to filter and accomplish a list of tasks.

Filtering values
Counting fields
Sorting (A-Z and Z-A)
Viewing details
Performing whois lookup on IP address
Viewing the associated packets in Wireshark
The image below demonstrates how to perform whois lookup and Wireshark packet inspection.

See image
<img width="910" height="502" alt="Screenshot 2025-09-25 at 2 55 20 PM" src="https://github.com/user-attachments/assets/1f80c900-33e4-4c68-bd9a-404366998bc4" />
Queries and History

Queries help us to correlate finding and find the event of the interest. History stores executed queries.
<img width="488" height="538" alt="Screenshot 2025-09-25 at 2 55 31 PM" src="https://github.com/user-attachments/assets/4aa9e735-bf59-4052-86af-8fc87ec45bb8" />
The image on the left demonstrates how to browse the queries and load a specific query from the library.

Queries can have names, tags and descriptions. Query library lists the query names, and once you double-click, it passes the actual query to the search bar.

You can double-click on the query and execute it with ease. Once you double-click on the query, the actual query appears on the search bar and is listed under the history tab.

The results are shown under the search bar. In this case, we listed all available log sources created by Brim. In this example, we only insert a pcap file, and it automatically creates nine types of Zeek log files.

Brim has 12 premade queries listed under the “Brim” folder. These queries help us discover the Brim query structure and accomplish quick searches from templates. You can add new queries by clicking on the “+” button near the “Queries” menu.
<img width="557" height="141" alt="Screenshot 2025-09-25 at 2 55 38 PM" src="https://github.com/user-attachments/assets/201a24f6-2496-4b4c-9875-87f43500f4ec" />

Answer the questions below
Process the “sample.pcap” file and look at the details of the first DNS log that appear on the dashboard. What is the “qclass_name”?
On the desktop, double-click the Exercise-Files directory icon and Brim icon.
<img width="185" height="484" alt="Screenshot 2025-09-25 at 3 00 13 PM" src="https://github.com/user-attachments/assets/329eb8df-019a-47e0-8d7e-c894c3f88a67" />
When both open, click and drag the sample.pcap file from the Exercise-Files directory to the Brim application.
<img width="679" height="329" alt="Screenshot 2025-09-25 at 3 00 23 PM" src="https://github.com/user-attachments/assets/401e605e-4b37-47b9-8d1d-123ede633351" />
Then Brim will start to import the file.
<img width="674" height="335" alt="Screenshot 2025-09-25 at 3 00 31 PM" src="https://github.com/user-attachments/assets/33df3eb9-28af-4091-b8eb-937c14cd3f36" />
After the sample pcap loads, we first want to go to the view tab. It is the fourth tab on the right at the top of Brim. Click on it and a drop-down menu will appear, then click the Right Pane choice.

Press enter or click to view image in full size
<img width="681" height="144" alt="Screenshot 2025-09-25 at 3 00 40 PM" src="https://github.com/user-attachments/assets/3d5d31a5-bb9f-40de-bc77-01729b53efa3" />
Now that the Right Pane is visible, look at the dashboard in the middle of Brim. We want to look for the DNS entry, it can be found in the seventh result down. Once you find it, click on the entry.
<img width="684" height="287" alt="Screenshot 2025-09-25 at 3 00 49 PM" src="https://github.com/user-attachments/assets/317c93f7-760c-4911-ad02-6a7b1a7e5e5c" />
After you have clicked on the DNS entry, look at the Right Pane which is the Log Details. In the Log Details, we are looking for the qclass_name in the left column. Look down through till you find it, once you do the answer will be found in the column on the right. Type the answer into the TryHackMe answer field, then type submit.
<img width="683" height="338" alt="Screenshot 2025-09-25 at 3 01 00 PM" src="https://github.com/user-attachments/assets/2f5898fb-d483-48ad-86cb-533e98ab43d2" />
Answer: C_INTERNET

Look at the details of the first NTP log that appear on the dashboard. What is the “duration” value?
Head back to the VM and in the dashboard look for NTP, once you find it click on the entry. The details of this entry will show up in the Log Details on the right panel. Go to the Log Details and scroll to the bottom.
<img width="677" height="297" alt="Screenshot 2025-09-25 at 3 01 09 PM" src="https://github.com/user-attachments/assets/5096d7b2-656b-495b-8ae8-e2bbaa41fd01" />
Once you reach the bottom, you will see the Duration column. To the right of this column is the answer. Once you find it, type the answer into the TryHackMe answer field, then click submit.
<img width="292" height="174" alt="Screenshot 2025-09-25 at 3 01 18 PM" src="https://github.com/user-attachments/assets/86dfea91-464e-483b-96fc-606ba6935c16" />
Answer: 0.005

Look at the details of the STATS packet log that is visible on the dashboard. What is the “reassem_tcp_size”?
Head back to the VM and in the dashboard scroll down till find STATS.
<img width="680" height="317" alt="Screenshot 2025-09-25 at 3 01 30 PM" src="https://github.com/user-attachments/assets/6209430d-e46d-4a74-915d-5035693013b7" />
Once you find STATS, click on it. Then look to the Log Details panel on the right. Watching the column on the left as you scroll for the label, reassem_tcp_size.
<img width="677" height="326" alt="Screenshot 2025-09-25 at 3 06 42 PM" src="https://github.com/user-attachments/assets/0c2f43be-7781-47ff-8647-108ed46002e2" />

Once you find the column labeled reassem_tcp_size, look to the right of this column and you will see the answer. Once you find it, type the answer into the TryHackMe answer field, then click submit.

<img width="240" height="123" alt="Screenshot 2025-09-25 at 3 02 21 PM" src="https://github.com/user-attachments/assets/4aeccecd-41db-4291-87b1-7ddf5adc31c2" />
Answer: 540
concluion

