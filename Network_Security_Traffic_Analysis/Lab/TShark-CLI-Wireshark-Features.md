TShark: CLI Wireshark Features|Tryhackme|Walkthrough
Task — 1 Introduction

In our first room, TShark: The Basics, we covered the fundamentals of TShark by focusing on how it operates and how to use it to investigate traffic captures. In this room, we will cover advanced features of TShark by focusing on translating Wireshark GUI features to the TShark CLI and investigate events of interest.

To start the VM, press the green Start Machine button attached to this task. The machine will start in split view. In case it is not showing up, you can press the blue Show Split View button at the top of the page.

The task files for this room are located in the following directory:

~/Desktop/exercise-files
Task — 2 Command-Line Wireshark Features I | Statistics I

Command-Line Wireshark Features I | Statistics

At the beginning of this module, we mentioned that TShark is considered a command line version of Wireshark. In addition to sharing the same display filters, TShark can accomplish several features of Wireshark explained below.

Three important points when using Wireshark-like features:

These options are applied to all packets in scope unless a display filter is provided.
Most of the commands shown below are CLI versions of the Wireshark features discussed in Wireshark: Packet Operations (Task 2).
TShark explains the parameters used at the beginning of the output line.
For example, you will use the phs option to view the protocol hierarchy. Once you use this command, the result will start with the "Packet Hierarchy Statistics" header.
<img width="670" height="426" alt="Screenshot 2025-09-25 at 6 16 27 PM" src="https://github.com/user-attachments/assets/7c8a63e6-835d-4022-8a66-2d9e95f5c913" />
Colourised Output

TShark can provide colourised outputs to help analysts speed up the analysis and spot anomalies quickly. If you are more of a Wireshark person and feel the need for a Wireshark-style packet highlighting this option does that. The colour option is activated with the --color parameter, as shown below.

View in colour
<img width="726" height="254" alt="Screenshot 2025-09-25 at 6 17 31 PM" src="https://github.com/user-attachments/assets/91974b1b-a6db-4bab-8f98-f1b1cbcd6d6d" />
 Statistics | Protocol Hierarchy

Protocol hierarchy helps analysts to see the protocols used, frame numbers, and size of packets in a tree view based on packet numbers. As it provides a summary of the capture, it can help analysts decide the focus point for an event of interest. Use the -z io,phs -q parameters to view the protocol hierarchy.

View protocol hierarchy
<img width="682" height="357" alt="Screenshot 2025-09-25 at 6 17 39 PM" src="https://github.com/user-attachments/assets/f2b25f49-3c57-4593-b8cf-14c689c43a4a" />
After viewing the entire packet tree, you can focus on a specific protocol as shown below. Add the udp keyword to the filter to focus on the UDP protocol.

View protocol hierarchy
Statistics | Packet Lengths Tree

The packet lengths tree view helps analysts to overview the general distribution of packets by size in a tree view. It allows analysts to detect anomalously big and small packets at a glance! Use the -z plen,tree -q parameters to view the packet lengths tree.

View packet lengths tree
<img width="679" height="396" alt="Screenshot 2025-09-25 at 6 20 06 PM" src="https://github.com/user-attachments/assets/1bdc7468-952a-4573-8272-ebf0dc3f143e" />

Statistics | Endpoints

The endpoint statistics view helps analysts to overview the unique endpoints. It also shows the number of packets associated with each endpoint. If you are familiar with Wireshark, you should know that endpoints can be viewed in multiple formats. Similar to Wireshark, TShark supports multiple source filtering options for endpoint identification. Use the -z endpoints,ip -q parameters to view IP endpoints. Note that you can choose other available protocols as well.

Filters for the most common viewing options are explained below.

Press enter or click to view image in full size
<img width="675" height="453" alt="Screenshot 2025-09-25 at 6 20 13 PM" src="https://github.com/user-attachments/assets/f8412fbb-d75c-40f0-99f3-a752f6630821" />

View IPv4 endpoints

<img width="678" height="250" alt="Screenshot 2025-09-25 at 6 20 21 PM" src="https://github.com/user-attachments/assets/917a894a-f43b-4dc2-af0f-dcc9d250345b" />
Statistics | Conversations

The conversations view helps analysts to overview the traffic flow between two particular connection points. Similar to endpoint filtering, conversations can be viewed in multiple formats. This filter uses the same parameters as the “Endpoints” option. Use the -z conv,ip -q parameters to view IP conversations.

View IPv4 conversations

<img width="680" height="240" alt="Screenshot 2025-09-25 at 6 20 28 PM" src="https://github.com/user-attachments/assets/ac69918e-3768-48e2-97de-f80411f8aac6" />
Statistics | Expert Info

The expert info view helps analysts to view the automatic comments provided by Wireshark. If you are unfamiliar with the “Wireshark Expert Info”, visit task 4 in the Wireshark: The Basics room of the Wireshark module. Use the -z expert -q parameters to view the expert information.

View expert info
<img width="683" height="375" alt="Screenshot 2025-09-25 at 6 20 37 PM" src="https://github.com/user-attachments/assets/bd7d81d9-e3af-4fc7-a5b3-e27660d5586c" />
Q1 : Use the “write-demo.pcap” to answer the questions.

What is the byte value of the TCP protocol?
To find the answer just run this command tshark -r write-demo.pcap -z io,phs -q you will find the answer
<img width="673" height="590" alt="Screenshot 2025-09-25 at 6 20 46 PM" src="https://github.com/user-attachments/assets/e9ad90a5-0592-4f58-a04a-eda8a4f88fa5" />
Answer : 62

Q2 : In which packet lengths row is our packet listed?

To find the answer just run this command tshark -r write-demo.pcap -z plen,tree -q you will find the answer
<img width="679" height="592" alt="Screenshot 2025-09-25 at 6 20 55 PM" src="https://github.com/user-attachments/assets/b31d762a-18d1-43e8-b490-6df27486fd86" />
Answer: 40–79

Q3 : What is the summary of the expert info?

To find the answer just run this command tshark -r write-demo.pcap -z expert -q you will find the answer

Press enter or click to view image in full size
<img width="672" height="540" alt="Screenshot 2025-09-25 at 6 21 06 PM" src="https://github.com/user-attachments/assets/0588f090-a60d-46c0-9545-1bbf3295618a" />
Answer: Connection establish request (SYN): server port 80

Q4 : Use the “demo.pcapng” to answer the question.

List the communications. What is the IP address that exists in all IPv4 conversations?
Enter your answer in defanged format.
To find the answer just run this command tshark -r demo.pcapng -z conv,ip -q and find the common ip address that’s been in the result now they have asked us to defang the answer so please visit this website “https://gchq.github.io/CyberChef/” in the Recipe add defang IP Address and enter the IP Address as 145.254.160.237 you will find the answer
<img width="817" height="695" alt="Screenshot 2025-09-25 at 6 21 17 PM" src="https://github.com/user-attachments/assets/53788dac-f9c3-4130-a8df-1dd5f76f75a2" />
Answer: 145[.]254[.]160[.]237

Task — 3 Command-Line Wireshark Features II | Statistics II

Command-Line Wireshark Features II | Specific Filters for Particular Protocols

There are plenty of filters designed for multiple protocols. The common filtering options for specific protocols are explained below. Note that most of the commands shown below are CLI versions of the Wireshark features discussed in Wireshark: Packet Operations (Task 3)

Statistics | IPv4 and IPv6

This option provides statistics on IPv4 and IPv6 packets, as shown below. Having the protocol statistics helps analysts to overview packet distribution according to the protocol type. You can filter the available protocol types and view the details using the -z ptype,tree -q parameters.

Sample IPv4 protocol types

<img width="654" height="223" alt="Screenshot 2025-09-25 at 6 21 26 PM" src="https://github.com/user-attachments/assets/f89d387b-ea89-4a81-ab5f-d225eb8d575f" />
Having the summary of the hosts in a single view is useful as well. Especially when you are working with large captures, viewing all hosts with a single command can help you to detect an anomalous host at a glance. You can filter all IP addresses using the parameters given below.

IPv4: -z ip_hosts,tree -q
IPv6: -z ipv6hosts,tree -q
Available hosts

<img width="670" height="226" alt="Screenshot 2025-09-25 at 6 21 34 PM" src="https://github.com/user-attachments/assets/8e05f3d6-e22d-4e57-bdc8-b7d5ce18331e" />
For complex cases and in-depth analysis, you will need to correlate the finding by focusing on the source and destination addresses. You can filter all source and destination addresses using the parameters given below.

IPv4: -z ip_srcdst,tree -q
IPv6: -z ipv6_srcdst,tree -q
Source and destination addresses
<img width="681" height="332" alt="Screenshot 2025-09-25 at 6 21 45 PM" src="https://github.com/user-attachments/assets/9077cff0-f5df-44e1-af40-14f0998d81f7" />

In some cases, you will need to focus on the outgoing traffic to spot the used services and ports. You can filter all outgoing traffic by using the parameters given below.

IPv4: -z dests,tree -q
IPv6: -z ipv6_dests,tree -q
Destinations and ports
<img width="691" height="350" alt="Screenshot 2025-09-25 at 6 21 53 PM" src="https://github.com/user-attachments/assets/6b8f74dd-c299-4d2f-9d1d-951d626db217" />
Statistics | DNS

This option provides statistics on DNS packets by summarising the available info. You can filter the packets and view the details using the -z dns,tree -q parameters.

DNSstatistics
<img width="676" height="288" alt="Screenshot 2025-09-25 at 6 22 02 PM" src="https://github.com/user-attachments/assets/b79169df-db74-4038-9fec-c6deeb6259c9" />
Statistics | HTTP

This option provides statistics on HTTP packets by summarising the load distribution, requests, packets, and status info. You can filter the packets and view the details using the parameters given below.

Packet and status counter for HTTP: -z http,tree -q
Packet and status counter for HTTP2: -z http2,tree -q
Load distribution: -z http_srv,tree -q
Requests: -z http_req,tree -q
Requests and responses: -z http_seq,tree -q
HTTPpacket statistics
<img width="677" height="300" alt="Screenshot 2025-09-25 at 6 22 10 PM" src="https://github.com/user-attachments/assets/4cb51ef4-403a-48c4-a9e6-19a14872166b" />

Q1 : Use the “demo.pcapng” to answer the questions.

Which IP address has 7 appearances?
Enter your answer in defanged format.
To find the answer just run this command shark -r demo.pcapng -z ip_hosts,tree -q and check for count Burst rate to be 7 as mentioned in the question as 7 appearances you will get the IP Address now you have to use CyberChef to defang the IP Address (I have given the link for CyberChef above) you will find the answer
<img width="680" height="365" alt="Screenshot 2025-09-27 at 12 33 29 AM" src="https://github.com/user-attachments/assets/6fe8fbcd-723d-4bd2-8367-c57d5cc85d4b" />
<img width="687" height="306" alt="Screenshot 2025-09-27 at 12 33 41 AM" src="https://github.com/user-attachments/assets/66de8a9c-1920-4158-a26e-d271c7bd9e6c" />
Answer: 216[.]239[.]59[.]99

Q2: What is the “destination address percentage” of the previous IP address?

To find the answer just run this command tshark -r demo.pcapng -z ip_srcdst,tree -q you will find the answer

Press enter or click to view image in full size
<img width="683" height="595" alt="Screenshot 2025-09-27 at 12 33 52 AM" src="https://github.com/user-attachments/assets/efad06d6-debd-4ef3-9658-9b4711602fb4" />

Answer: 6.98%

Q3 : Which IP address constitutes “2.33% of the destination addresses”?

Enter your answer in defanged format.
To find the answer just run this command tshark -r demo.pcapng -z dests,tree -q from the result shown find the percentage that as 2.33% in the IP Address of it and now you have to use CyberChef to defang the IP Address (I have given the link for CyberChef above) you will find the answer

<img width="681" height="600" alt="Screenshot 2025-09-27 at 12 35 34 AM" src="https://github.com/user-attachments/assets/7c3ef681-a6f9-4867-ba15-9be9154cdd40" />
<img width="676" height="566" alt="Screenshot 2025-09-27 at 12 35 47 AM" src="https://github.com/user-attachments/assets/82bed0b4-d279-428e-bdf4-f0c2926b8476" />
<img width="704" height="312" alt="Screenshot 2025-09-27 at 12 35 57 AM" src="https://github.com/user-attachments/assets/b9abe6e1-fe5e-4b11-a8c2-8919d8e8b238" />

Answer: 145[.]253[.]2[.]203

Q4: What is the average “Qname Len” value?

To find the answer just run this command tshark -r demo.pcapng -z dns,tree -q and in the result find Qname Len now you can get the Average burst rate that will be your answer
<img width="679" height="594" alt="Screenshot 2025-09-27 at 12 36 13 AM" src="https://github.com/user-attachments/assets/d3f08efb-76e0-46c7-a7d3-185cb0ff1154" />
Answer: 29.00
Task — 4 Command-Line Wireshark Features III | Streams, Objects and Credentials

Command-Line Wireshark Features III | Streams, Objects and Credentials

There are plenty of filters designed for multiple purposes. The common filtering options for specific operations are explained below. Note that most of the commands shown below are CLI versions of the Wireshark features discussed in the Wireshark module

Follow Stream

This option helps analysts to follow traffic streams similar to Wireshark. The query structure is explained in the table given below.

Press enter or click to view image in full size
<img width="671" height="163" alt="Screenshot 2025-09-27 at 12 38 24 AM" src="https://github.com/user-attachments/assets/f7da678c-b8b8-4053-83cf-d4698165b671" />
Note: Streams start from “0”. You can filter the packets and follow the streams by using the parameters given below.

TCP Streams: -z follow,tcp,ascii,0 -q
UDP Streams: -z follow,udp,ascii,0 -q
HTTP Streams: -z follow,http,ascii,0 -q
Follow TCP stream
<img width="677" height="456" alt="Screenshot 2025-09-27 at 12 38 36 AM" src="https://github.com/user-attachments/assets/208e5cf6-4e3f-483e-8264-19682f8a97b1" />
Export Objects

This option helps analysts to extract files from DICOM, HTTP, IMF, SMB and TFTP. The query structure is explained in the table given below.
<img width="674" height="195" alt="Screenshot 2025-09-27 at 12 38 44 AM" src="https://github.com/user-attachments/assets/eedba24f-46cb-42d4-8f98-7c55dde04fc9" />
You can filter the packets and follow the streams by using the parameters given below.

--export-objects http,/home/ubuntu/Desktop/extracted-by-tshark -q
Export objects
<img width="682" height="200" alt="Screenshot 2025-09-27 at 12 38 52 AM" src="https://github.com/user-attachments/assets/24755e1f-dfb2-40cb-a63f-28724c9f8de1" />

Credentials

This option helps analysts to detect and collect cleartext credentials from FTP, HTTP, IMAP, POP and SMTP. You can filter the packets and find the cleartext credentials using the parameters below.

-z credentials -q
ind cleartext credentials
<img width="675" height="344" alt="Screenshot 2025-09-27 at 12 39 04 AM" src="https://github.com/user-attachments/assets/f6604de6-bb91-4ed4-ad12-ba8314da83a4" />
Q1 : Use the “demo.pcapng” to answer the questions.

Follow the “UDP stream 0”.
What is the “Node 0” value?
Enter your answer in defanged format.
To find the answer just run this commad tshark -r demo.pcapng -z follow,udp,ascii,0 -q you will get the IP Address and now you have to use CyberChef to defang the IP Address (I have given the link for CyberChef above) you will find the answer
<img width="675" height="251" alt="Screenshot 2025-09-27 at 12 39 15 AM" src="https://github.com/user-attachments/assets/18f03842-abd6-4050-8f64-7e089237e291" />
<img width="687" height="317" alt="Screenshot 2025-09-27 at 12 39 24 AM" src="https://github.com/user-attachments/assets/f0ca16a4-0c9d-455e-a29a-c6a4be266156" />

Answer: 145[.]254[.]160[.]237:3009

Q2 : Follow the “HTTP stream 1”.

What is the “Referer” value?
Enter your answer in defanged format.
To find the answer just run the command tshark -r demo.pcapng -z follow,http,ascii,1 -q search for the Referer Value put that Referer Value on CyberChef (I have given the link for CyberChef above) as this is an URL you need to change the Recipe to Defang URL now paste the result URL you will find the answer
<img width="679" height="595" alt="Screenshot 2025-09-27 at 12 39 36 AM" src="https://github.com/user-attachments/assets/34002fe9-1c77-428d-8ff1-9e24e5cff6cf" />
<img width="682" height="313" alt="Screenshot 2025-09-27 at 12 39 47 AM" src="https://github.com/user-attachments/assets/ca7f8bf0-995e-41c2-a814-dc3a16eaa83d" />
Answer: hxxp[://]www[.]ethereal[.]com/download[.]html

Q3 : Use the “credentials.pcap” to answer the question.

What is the total number of detected credentials?
To find the answer just run this command tshark -r credentials.pcap -z credentials -q | wc -l you will get count of credentials as they said in the hint to Exclude the banner lines! so now you have to run this command tshark -r credentials.pcap -z credentials -q | nl to find how many lines have the banner as per the result count for the banner is 4 so just substract it from the previous result i.e 79–4 = 75
<img width="678" height="62" alt="Screenshot 2025-09-27 at 12 40 00 AM" src="https://github.com/user-attachments/assets/fee0f14f-4fc4-485b-9d05-f2a4fefc5248" />
<img width="674" height="611" alt="Screenshot 2025-09-27 at 12 40 09 AM" src="https://github.com/user-attachments/assets/4c035965-b7e8-4f4c-b3ba-3c26c1931b87" />
<img width="680" height="594" alt="Screenshot 2025-09-27 at 12 40 19 AM" src="https://github.com/user-attachments/assets/88065fa5-d02a-4352-8589-899fbd85feb2" />
Answer: 75

Task — 5 Advanced Filtering Options | Contains, Matches and Fields

Advanced Filtering Options | Contains, Matches and Extract Fields

Accomplishing in-depth packet analysis sometimes ends up with a special filtering requirement that cannot be covered with default filters. TShark supports Wireshark’s “contains” and “matches” operators, which are the key to the advanced filtering options. You can visit the Wireshark: Packet Operations room (Task 6) if you are unfamiliar with these filters.

A quick recap from the Wireshark: Packet Operations room:

Press enter or click to view image in full size
<img width="676" height="264" alt="Screenshot 2025-09-27 at 12 46 04 AM" src="https://github.com/user-attachments/assets/96e534db-30f3-43c7-83c7-c47cf748ff21" />
Note: The “contains” and “matches” operators cannot be used with fields consisting of “integer” values.
Tip: Using HEX and regex values instead of ASCII always has a better chance of a match.

Extract Fields

This option helps analysts to extract specific parts of data from the packets. In this way, analysts have the opportunity to collect and correlate various fields from the packets. It also helps analysts manage the query output on the terminal. The query structure is explained in the table given below.
<img width="676" height="86" alt="Screenshot 2025-09-27 at 12 46 11 AM" src="https://github.com/user-attachments/assets/9c6a3fe9-6100-4801-8b99-1d7d0c1a350b" />

Note: You need to use the -e parameter for each field you want to display.

You can filter any field by using the field names as shown below.

-T fields -e ip.src -e ip.dst -E header=y
Extract fields
<img width="682" height="200" alt="Screenshot 2025-09-27 at 12 46 21 AM" src="https://github.com/user-attachments/assets/0961f241-3326-4193-a98f-83f39a6dae5d" />
Filter: “contains”
<img width="669" height="253" alt="Screenshot 2025-09-27 at 12 46 30 AM" src="https://github.com/user-attachments/assets/fa14f2de-4dd8-4592-9e9f-cc1c012762ef" />
Contains filter
<img width="674" height="154" alt="Screenshot 2025-09-27 at 12 46 44 AM" src="https://github.com/user-attachments/assets/11330779-32f3-4d2a-927d-5f5a4cfbef8b" />
<img width="670" height="276" alt="Screenshot 2025-09-27 at 12 46 54 AM" src="https://github.com/user-attachments/assets/b5fdcd92-eb4a-4cac-bb19-95bfc0a7ca05" />

Matches filter
<img width="682" height="204" alt="Screenshot 2025-09-27 at 12 47 01 AM" src="https://github.com/user-attachments/assets/b47d28d2-1674-43bc-87f6-fa3299001022" />
Q1 : Use the “demo.pcapng” to answer questions.

What is the HTTP packet number that contains the keyword “CAFE”?
To find the answer just run this command tshark -r demo.pcapng -Y ‘http contains “CAFE”’ you will find the answer
<img width="677" height="62" alt="Screenshot 2025-09-27 at 12 47 08 AM" src="https://github.com/user-attachments/assets/21ab26a6-1e3a-4afb-8e7e-4dfc6b1b739f" />
Answer: 27

Q2 : Filter the packets with “GET” and “POST” requests and extract the packet frame time.

What is the first time value found?
To find the answer just run this command tshark -r demo.pcapng -Y ‘http.request.method == “GET” || http.request.method == “POST”’ -T fields -e frame.time you will find the answer
<img width="678" height="57" alt="Screenshot 2025-09-27 at 12 47 16 AM" src="https://github.com/user-attachments/assets/b2f9890a-3b1b-4aa4-a3ad-bf3fe69c6a0d" />
Answer: May 13, 2004 10:17:08.222534000 UTC

Task — 6 Use Cases | Extract Information

Use Cases

When investigating a case, a security analyst should know how to extract hostnames, DNS queries, and user agents to hunt low-hanging fruits after viewing the statistics and creating an investigation plan. The most common four use cases for every security analyst are demonstrated below. If you want to learn more about the mentioned protocols and benefits of the extracted info, please refer to the Wireshark Traffic Analysis room.

Extract Hostnames
<img width="681" height="237" alt="Screenshot 2025-09-27 at 12 53 08 AM" src="https://github.com/user-attachments/assets/3c6bc437-1baf-4569-ae7a-6855ba67cd88" />
The above example shows how to extract hostnames from DHCP packets with TShark. However, the output is hard to manage when multiple duplicate values exist. A skilled analyst should know how to use native Linux tools/utilities to manage and organise the command line output, as shown below.

Extract hostnames
<img width="679" height="158" alt="Screenshot 2025-09-27 at 12 53 16 AM" src="https://github.com/user-attachments/assets/ec13f4a3-0dc4-469e-84d9-c19b5e477724" />
Now the output is organised and ready to process/use. The logic of the query is explained below.
<img width="661" height="395" alt="Screenshot 2025-09-27 at 12 53 26 AM" src="https://github.com/user-attachments/assets/f160eb78-296b-403d-abcd-b8dcd5f605c9" />
Extract DNS Queries

Matches filter
<img width="688" height="238" alt="Screenshot 2025-09-27 at 12 53 33 AM" src="https://github.com/user-attachments/assets/167d6800-5bf2-43cd-8806-514e7c1c3fbd" />
Extract User Agents

Matches filter

<img width="677" height="197" alt="Screenshot 2025-09-27 at 12 53 40 AM" src="https://github.com/user-attachments/assets/49850e90-9eeb-4995-a7a0-bfa7915bc6fc" />
Q1 : Use the “hostnames.pcapng” to answer the questions.

What is the total number of unique hostnames?
To find the answer just run this command tshark -r hostnames.pcapng -T fields -e dhcp.option.hostname | awk NF | sort -r | uniq -c | sort -r | wc -l you will find the answer
<img width="677" height="63" alt="Screenshot 2025-09-27 at 12 53 49 AM" src="https://github.com/user-attachments/assets/c4c29422-0549-4405-844b-1bbbb4c13505" />
Answer: 30

Q2 : What is the total appearance count of the “prus-pc” hostname?

To find the answer just run this command tshark -r hostnames.pcapng -T fields -e dhcp.option.hostname | grep -c “prus-pc” you will find the answer

<img width="676" height="87" alt="Screenshot 2025-09-27 at 12 53 57 AM" src="https://github.com/user-attachments/assets/41090041-e902-44bd-8173-f7b7acc853f2" />
Answer: 12

Q3 : Use the “dns-queries.pcap” to answer the question.

What is the total number of queries of the most common DNS query?
To find the answer just run this command tshark -r dns-queries.pcap -T fields -e dns.qry.name | sort | uniq -c | sort -nr | head -n 1 you will find the answer

<img width="677" height="67" alt="Screenshot 2025-09-27 at 12 54 06 AM" src="https://github.com/user-attachments/assets/45445743-dd11-4ac5-9d66-e12ea325f5b6" />

Answer: 472

Q4 : Use the “user-agents.pcap” to answer questions.

What is the total number of the detected “Wfuzz user agents”?
To find the answer just run this command tshark -r user-agents.pcap -Y ‘http.user_agent contains “Wfuzz”’ | wc -l you will find the answer

<img width="681" height="69" alt="Screenshot 2025-09-27 at 12 54 15 AM" src="https://github.com/user-attachments/assets/eac5896e-2117-417d-ba6a-a65aa739e46e" />
Answer: 12

Q5 : What is the “HTTP hostname” of the nmap scans?

Enter your answer in defanged format.
To find the answer run this command tshark -r user-agents.pcap -T fields -e http.host now from the result you will get the HTTP hostname and you will find a common IP Address now use that IP Address on CyberChef website to defang the IP Address (I have given the link for CyberChef above) you will find the answer
<img width="672" height="585" alt="Screenshot 2025-09-27 at 12 54 25 AM" src="https://github.com/user-attachments/assets/d6523199-d721-4894-a909-5b08c7967b99" />
<img width="679" height="303" alt="Screenshot 2025-09-27 at 12 54 35 AM" src="https://github.com/user-attachments/assets/9105e7c8-59f3-46ba-b351-f1da40f283b2" />
Answer: 172[.]16[.]172[.]129
