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



