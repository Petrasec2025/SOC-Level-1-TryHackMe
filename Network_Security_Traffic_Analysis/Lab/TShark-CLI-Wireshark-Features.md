# TShark: CLI Wireshark Features | TryHackMe Walkthrough

![TryHackMe](https://img.shields.io/badge/TryHackMe-TShark%20CLI%20Wireshark%20Features-red) 
![Difficulty](https://img.shields.io/badge/Difficulty-Easy-green) 
![Category](https://img.shields.io/badge/Category-Forensics-blue) 
![Time](https://img.shields.io/badge/Time-1%20hour-orange)

## Overview
This room covers advanced features of TShark, focusing on translating Wireshark GUI features to the TShark CLI and investigating events of interest. We'll explore statistics, protocol analysis, stream following, object extraction, and advanced filtering techniques.

## Task 1 - Introduction
The task files for this room are located in: `~/Desktop/exercise-files`

## Task 2 - Command-Line Wireshark Features I | Statistics I

### Q1: What is the byte value of the TCP protocol?
**Command:** `tshark -r write-demo.pcap -z io,phs -q`

![Protocol Hierarchy](https://github.com/user-attachments/assets/7c8a63e6-835d-4022-8a66-2d9e95f5c913)

**Answer:** `62`

### Q2: In which packet lengths row is our packet listed?
**Command:** `tshark -r write-demo.pcap -z plen,tree -q`

![Packet Lengths Tree](https://github.com/user-attachments/assets/1bdc7468-952a-4573-8272-ebf0dc3f143e)

**Answer:** `40-79`

### Q3: What is the summary of the expert info?
**Command:** `tshark -r write-demo.pcap -z expert -q`

![Expert Info](https://github.com/user-attachments/assets/0588f090-a60d-46c0-9545-1bbf3295618a)

**Answer:** `Connection establish request (SYN): server port 80`

### Q4: List the communications. What is the IP address that exists in all IPv4 conversations? Enter your answer in defanged format.
**Command:** `tshark -r demo.pcapng -z conv,ip -q`

![IPv4 Conversations](https://github.com/user-attachments/assets/53788dac-f9c3-4130-a8df-1dd5f76f75a2)

**Answer:** `145[.]254[.]160[.]237`

## Task 3 - Command-Line Wireshark Features II | Statistics II

### Q1: Which IP address has 7 appearances? Enter your answer in defanged format.
**Command:** `tshark -r demo.pcapng -z ip_hosts,tree -q`

![IP Hosts](https://github.com/user-attachments/assets/6fe8fbcd-723d-4bd2-8367-c57d5cc85d4b)

**Answer:** `216[.]239[.]59[.]99`

### Q2: What is the "destination address percentage" of the previous IP address?
**Command:** `tshark -r demo.pcapng -z ip_srcdst,tree -q`

![Source Destination Tree](https://github.com/user-attachments/assets/efad06d6-debd-4ef3-9658-9b4711602fb4)

**Answer:** `6.98%`

### Q3: Which IP address constitutes "2.33% of the destination addresses"? Enter your answer in defanged format.
**Command:** `tshark -r demo.pcapng -z dests,tree -q`

![Destinations Tree](https://github.com/user-attachments/assets/7c3ef681-a6f9-4867-ba15-9be9154cdd40)

**Answer:** `145[.]253[.]2[.]203`

### Q4: What is the average "Qname Len" value?
**Command:** `tshark -r demo.pcapng -z dns,tree -q`

![DNS Tree](https://github.com/user-attachments/assets/d3f08efb-76e0-46c7-a7d3-185cb0ff1154)

**Answer:** `29.00`

## Task 4 - Command-Line Wireshark Features III | Streams, Objects and Credentials

### Q1: Follow the "UDP stream 0". What is the "Node 0" value? Enter your answer in defanged format.
**Command:** `tshark -r demo.pcapng -z follow,udp,ascii,0 -q`

![UDP Stream 0](https://github.com/user-attachments/assets/18f03842-abd6-4050-8f64-7e089237e291)

**Answer:** `145[.]254[.]160[.]237:3009`

### Q2: Follow the "HTTP stream 1". What is the "Referer" value? Enter your answer in defanged format.
**Command:** `tshark -r demo.pcapng -z follow,http,ascii,1 -q`

![HTTP Stream 1](https://github.com/user-attachments/assets/34002fe9-1c77-428d-8ff1-9e24e5cff6cf)

**Answer:** `hxxp[://]www[.]ethereal[.]com/download[.]html`

### Q3: What is the total number of detected credentials?
**Command:** `tshark -r credentials.pcap -z credentials -q | wc -l`

**Answer:** `75`

## Task 5 - Advanced Filtering Options | Contains, Matches and Fields

### Q1: What is the HTTP packet number that contains the keyword "CAFE"?
**Command:** `tshark -r demo.pcapng -Y 'http contains "CAFE"'`

![Contains Filter](https://github.com/user-attachments/assets/21ab26a6-1e3a-4afb-8e7e-4dfc6b1b739f)

**Answer:** `27`

### Q2: Filter the packets with "GET" and "POST" requests and extract the packet frame time. What is the first time value found?
**Command:** `tshark -r demo.pcapng -Y 'http.request.method == "GET" || http.request.method == "POST"' -T fields -e frame.time`

![Extract Fields](https://github.com/user-attachments/assets/b2f9890a-3b1b-4aa4-a3ad-bf3fe69c6a0d)

**Answer:** `May 13, 2004 10:17:08.222534000 UTC`

## Task 6 - Use Cases | Extract Information

### Q1: What is the total number of unique hostnames?
**Command:** `tshark -r hostnames.pcapng -T fields -e dhcp.option.hostname | awk NF | sort -r | uniq -c | sort -r | wc -l`

![Extract Hostnames](https://github.com/user-attachments/assets/c4c29422-0549-4405-844b-1bbbb4c13505)

**Answer:** `30`

### Q2: What is the total appearance count of the "prus-pc" hostname?
**Command:** `tshark -r hostnames.pcapng -T fields -e dhcp.option.hostname | grep -c "prus-pc"`

![Hostname Count](https://github.com/user-attachments/assets/41090041-e902-44bd-8173-f7b7acc853f2)

**Answer:** `12`

### Q3: What is the total number of queries of the most common DNS query?
**Command:** `tshark -r dns-queries.pcap -T fields -e dns.qry.name | sort | uniq -c | sort -nr | head -n 1`

![DNS Queries](https://github.com/user-attachments/assets/45445743-dd11-4ac5-9d66-e12ea325f5b6)

**Answer:** `472`

### Q4: What is the total number of the detected "Wfuzz user agents"?
**Command:** `tshark -r user-agents.pcap -Y 'http.user_agent contains "Wfuzz"' | wc -l`

![User Agents](https://github.com/user-attachments/assets/eac5896e-2117-417d-ba6a-a65aa739e46e)

**Answer:** `12`

### Q5: What is the "HTTP hostname" of the nmap scans? Enter your answer in defanged format.
**Command:** `tshark -r user-agents.pcap -T fields -e http.host`

![HTTP Host](https://github.com/user-attachments/assets/d6523199-d721-4894-a909-5b08c7967b99)

**Answer:** `172[.]16[.]172[.]129`

## Conclusion
This room provided comprehensive coverage of TShark's advanced features, demonstrating how to perform Wireshark-like analysis through the command line. Key skills learned include:

- Statistical analysis of packet captures
- Protocol hierarchy examination
- Stream following and analysis
- Object extraction from various protocols
- Advanced filtering using contains/matches operators
- Field extraction and data correlation
- Practical use cases for security analysis

The techniques covered are essential for network forensics and security analysis workflows where GUI tools may not be available or practical.

![Completion Badge](https://img.shields.io/badge/Completed-Successfully-brightgreen)
