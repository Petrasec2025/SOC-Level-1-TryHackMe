# TShark Challenge II: Directory Curiosity | TryHackMe Walkthrough

![TryHackMe](https://img.shields.io/badge/TryHackMe-TShark%20Challenge%20II%3A%20Directory%20Curiosity-red) 
![Difficulty](https://img.shields.io/badge/Difficulty-Medium-yellow) 
![Category](https://img.shields.io/badge/Category-Forensics-blue) 
![Time](https://img.shields.io/badge/Time-45%20minutes-orange)

## Introduction
This room presents you with a challenge to investigate some traffic data as a part of the SOC team. We recommend completing the TShark: The Basics and TShark: CLI Wireshark Features rooms first, which will teach you how to use the tool in depth.

**NOTE:** Exercise files contain real examples. DO NOT interact with them outside of the given VM. Direct interaction with samples and their contents (files, domains, and IP addresses) outside the given VM can pose security threats to your machine.

## Case: Directory Curiosity!
An alert has been triggered: "A user came across a poor file index, and their curiosity led to problems".

The case was assigned to you. Inspect the provided directory-curiosity.pcap located in `~/Desktop/exercise-files` and retrieve the artefacts to confirm that this alert is a true positive.

Your tools: TShark, VirusTotal.

## Investigation Questions

### 1. What is the name of the malicious/suspicious domain?
Investigate the DNS queries and domains using VirusTotal to identify the malicious domain.

![DNS Investigation](https://github.com/user-attachments/assets/811c5786-e8fc-4f0c-b627-50a5111005a8)

**Answer:** `jx2-bavuong[.]com`

### 2. What is the total number of HTTP requests sent to the malicious domain?
Count the HTTP requests targeting the malicious domain.

![HTTP Requests Count](https://github.com/user-attachments/assets/d0884e9e-302b-43b8-ba49-282553957159)

**Answer:** `14`

### 3. What is the IP address associated with the malicious domain?
Identify the IP address linked to the malicious domain.

![IP Address Identification](https://github.com/user-attachments/assets/cf48ac63-bc5c-440c-9edb-73e4a0664d0e)

**Answer:** `141[.]164[.]41[.]174`

### 4. What is the server info of the suspicious domain?
Extract server information from the HTTP headers.

![Server Information](https://github.com/user-attachments/assets/f6f82631-5c39-4dc7-8a1b-a2210382f153)

**Answer:** `Apache/2.2.11 (Win32) DAV/2 mod_ssl/2.2.11 OpenSSL/0.9.8i PHP/5.2.9`

### 5. What is the number of listed files?
Follow the first TCP stream in ASCII format and investigate the output.

![TCP Stream Analysis](https://github.com/user-attachments/assets/347d9700-3d84-4c63-951a-4026ab66edc5)

**Answer:** `3`

### 6. What is the filename of the first file?
Identify the first file listed in the directory index.

**Answer:** `123[.]php`

### 7. What is the name of the downloaded executable file?
Export all HTTP traffic objects using the command:
```bash
tshark -r directory-curiosity.pcap --export-objects http,/home/ubuntu/Desktop/exercise-files -q
```

![Exported Objects](https://github.com/user-attachments/assets/812c060e-4f87-4351-bb86-efcd17b65845)

**Answer:** `vlauto[.]exe`

### 8. What is the SHA256 value of the malicious file?
Calculate the SHA256 hash of the downloaded executable.

![SHA256 Calculation](https://github.com/user-attachments/assets/ef5076fe-22af-480f-a1ad-cbfa3c744827)

**Answer:** `b4851333efaf399889456f78eac0fd532e9d8791b23a86a19402c1164aed20de`

### 9. What is the "PEiD packer" value?
Search the SHA256 value on VirusTotal to get PEiD packer information.

![VirusTotal PEiD](https://github.com/user-attachments/assets/cdf96e33-4d71-44c5-bf2a-eec192443ddf)

**Answer:** `.NET executable`

### 10. What does the "Lastline Sandbox" flag this as?
Check the Lastline Sandbox analysis on VirusTotal.

![Lastline Sandbox](https://github.com/user-attachments/assets/2064212c-944d-481e-b02d-988777d5bdc1)

**Answer:** `MALWARE TROJAN`

## Conclusion
This investigation revealed a sophisticated malware delivery campaign where:

- A user accidentally discovered a poorly secured file directory
- The malicious domain `jx2-bavuong[.]com` hosted suspicious content
- An executable file `vlauto.exe` was downloaded, identified as a .NET packed Trojan
- The malware had a SHA256 hash of `b4851333efaf399889456f78eac0fd532e9d8791b23a86a19402c1164aed20de`
- Multiple security vendors flagged the file as malicious

The case was confirmed as a true positive alert, demonstrating the importance of proper directory indexing and user awareness about exploring unknown file systems.

![Completion Badge](https://img.shields.io/badge/Challenge-Completed-brightgreen) 
![Skills](https://img.shields.io/badge/Skills-Malware%20Analysis%2C%20Network%20Forensics%2C%20Threat%20Intelligence-success)
