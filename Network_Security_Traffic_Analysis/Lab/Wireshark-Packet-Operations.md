# 🖧 Wireshark: Packet Operations  

![Wireshark](https://img.shields.io/badge/Wireshark-Packet_Analysis-blue?style=flat-square)
![Networking](https://img.shields.io/badge/Networking-Basics-green?style=flat-square)
![TryHackMe](https://img.shields.io/badge/TryHackMe-Lab-orange?style=flat-square)

---

“In this room, we will cover the fundamentals of packet analysis with Wireshark and investigate the event of interest at the packet-level. Note that this is the second room of the Wireshark room trio, and it is suggested to visit the first room ([Wireshark: The Basics](https://tryhackme.com/p/Petras20/https://tryhackme.com/room/wiresharkpacketoperations/)) to practice and refresh your Wireshark skills before starting this one.”

---

## Task 2: Statistics | Summary

**Investigate the resolved addresses. What is the IP address of the hostname starting with “bbc”?**  
**Ans:** 199.232.24.81  
![Resolved Address](https://github.com/user-attachments/assets/3cb9f6c9-ab64-4d75-b386-17292c29a323)

**Number of IPv4 conversations:** 435  
![IPv4 Conversations](https://github.com/user-attachments/assets/1da1cb6e-a945-4bad-97ad-ae68e50a8f66)

**Bytes (k) transferred from “Micro-St” MAC address:** 7474  
![Endpoint Bytes](https://github.com/user-attachments/assets/26351b05-ba03-41b2-b6d5-5a4326a33dc3)

**Number of IP addresses linked with “Kansas City”:** 4  
![Kansas City IPs](https://github.com/user-attachments/assets/8332d58c-b119-4f46-94d0-683dbe7e5862)

**IP address linked with “Blicnet” AS Organisation:** 188.246.82.7  
![Blicnet AS](https://github.com/user-attachments/assets/ade5d1cf-9f44-44f8-a972-aeab5f23a000)

---

## Task 3: Statistics | Protocol Details

**Most used IPv4 destination address:** 10.100.1.33  
![IPv4 Destination](https://github.com/user-attachments/assets/4132fc31-49dd-43aa-bde9-e2013ea4ca95)

**Max service request-response time of DNS packets:** 0.467897  
![DNS Max Response](https://github.com/user-attachments/assets/31354883-f7cd-48d5-9fab-95c73cf1e27c)

**Number of HTTP Requests accomplished by “rad[.]msn[.]com”:** 39  
![HTTP Requests](https://github.com/user-attachments/assets/583cda2a-0069-4a1b-94d0-a5ca429b09a0)

---

## Task 5: Packet Filtering | Protocol Filters

**Number of IP packets:** 84120  
![IP Packets](https://github.com/user-attachments/assets/73b30240-4df9-4737-8abc-1e21bbdd96ef)

**Number of packets with TTL < 10:** 66  
![TTL < 10](https://github.com/user-attachments/assets/2e95539d-38cd-487b-926c-a9d59dac3230)

**Number of packets using TCP port 4444:** 632  
![TCP 4444](https://github.com/user-attachments/assets/762f3bf0-c7ef-4d43-b6ee-53d28f72bf55)

**Number of HTTP GET requests sent to port 80:** 527  
![HTTP GET 80](https://github.com/user-attachments/assets/7f7627cf-1149-4156-89f0-f82849886b8b)

**Number of type A DNS Queries:** 51  
![Type A DNS Queries](https://github.com/user-attachments/assets/f00ac1d6-d35f-4fff-a61a-b0cd50dd033c)

---

## Task 6: Advanced Filtering

**Microsoft IIS servers packets not from port 80:** 21  
![IIS Non-80](https://github.com/user-attachments/assets/23849c32-0cb0-4ad7-b415-c39f62f37302)

**Microsoft IIS servers version 7.5 packets:** 71  
![IIS 7.5](https://github.com/user-attachments/assets/88e10265-838f-4630-b7aa-e1a498e41343)

**Total packets using ports 3333, 4444, 9999:** 2235  
![Ports 3333/4444/9999](https://github.com/user-attachments/assets/0e0e3ae5-55f8-457b-98ef-94357e6e6dca)

**Packets with even TTL numbers:** 77289  
![Even TTL](https://github.com/user-attachments/assets/cfe6a30f-3ec3-4028-8e69-76cd5b8cb114)

**Bad TCP Checksum packets (Checksum Control profile):** 34185  
![Bad TCP Checksum](https://github.com/user-attachments/assets/a7f12e64-bf53-4dab-93b8-64a8f3896004)

**Displayed packets after filtering:** 261  
![Displayed Packets](https://github.com/user-attachments/assets/8cd06e92-4b8d-4e97-b0b9-678d53aea02e)

---

## Conclusion

This lab reinforced **Wireshark fundamentals** and **advanced packet analysis techniques**, including:

- Capturing and dissecting packets (HTTP, TCP, DNS).  
- Using **Statistics** to summarize endpoints, IPv4 conversations, protocols, and resolved addresses.  
- Filtering packets using **Display Filters** and **advanced expressions** (ports, TTL, DNS types, HTTP methods).  
- Identifying issues with **TCP checksums** and analyzing network traffic anomalies.  
- Exporting objects and extracting data from capture files for further investigation.  

After completing this room, you should be comfortable **navigating captures, filtering packets, analyzing protocol-specific information**, and performing **network forensics exercises** using Wireshark.

---

