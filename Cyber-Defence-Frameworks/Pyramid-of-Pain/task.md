Pyramid of Pain – TryHackMe Lab Report
Task 1: Introduction

This well-renowned concept is applied to cybersecurity solutions like Cisco Security, SentinelOne, and SOCRadar to improve the effectiveness of CTI (Cyber Threat Intelligence), threat hunting, and incident response exercises.

Understanding the Pyramid of Pain concept is important for Threat Hunters, Incident Responders, and SOC Analysts.

<div align="center"> <img width="800" alt="Pyramid of Pain Screenshot" src="https://github.com/user-attachments/assets/c2c60ef0-09e4-4088-b839-e12c9065bd6f" /> </div>
Task 2: Hash Values (Trivial)
Hash Algorithms Overview

MD5 (Message Digest) – 128-bit hash, RFC 1321, designed by Ron Rivest, 1992.

SHA-1 (Secure Hash Algorithm 1) – 160-bit hash (40-digit hex), RFC 3174. Deprecated by NIST in 2011.

SHA-2 (SHA-256) – 256-bit hash (64-digit hex), designed by NIST & NSA.

Note: Even a single-bit modification changes the hash. Relying solely on hashes for threat hunting can be limiting.

Hash lookup tools: VirusTotal, Metadefender Cloud (OPSWAT)

<div align="center"> <img width="700" alt="Hash Screenshot" src="https://github.com/user-attachments/assets/39f87718-310f-49c8-844c-2ad07c65fe1d" /> </div>

Question: Analyse the report for hash b8ef959a9176aef07fdca8705254a163b50b49a17217a4ff0107487f59d4a35d.
Answer: Sales_Receipt 5606.xls

Task 3: IP Address (Easy)

IP addresses identify devices on a network. In the Pyramid of Pain, IP addresses are green.

Note: IP blocking can be bypassed using Fast Flux, a DNS technique used by botnets.

Questions:

First IP address the malicious process (PID 1632) communicates with:
Answer: 50.87.136.52

<div align="center"> <img width="650" alt="IP Screenshot" src="https://github.com/user-attachments/assets/73b29b39-0ed7-4700-adcd-3f7dd268757a" /> </div>

First domain name the malicious process (PID 1632) communicates with:
Answer: craftingalegacy.com

Task 4: Domain Names (Simple)

Domain names map IPs to human-readable text:

Domain + TLD: evilcorp.com

Subdomain + Domain + TLD: tryhackme.evilcorp.com

<div align="center"> <img width="700" alt="Domain Screenshot" src="https://github.com/user-attachments/assets/fcb6ef0b-9f4f-40cf-b807-626d467ac3d3" /> </div>

Malicious domains often use URL shorteners:
bit.ly, goo.gl, ow.ly, s.id, smarturl.it, tiny.pl, tinyurl.com, x.co

Preview shortened URLs by appending +.

<div align="center"> <img width="630" alt="URL Shortener Screenshot" src="https://github.com/user-attachments/assets/10a74247-da1b-4798-b29d-4f6041e6e094" /> </div>
Any.Run Analysis Tabs

HTTP Requests: <img width="670" alt="HTTP Requests Screenshot" src="https://github.com/user-attachments/assets/2092c9d8-c319-451e-867d-d04548157ff5" />

Connections: <img width="670" alt="Connections Screenshot" src="https://github.com/user-attachments/assets/cc2dcea9-3f6b-4c42-a69f-83af73a0b48a" />

DNS Requests: <img width="670" alt="DNS Requests Screenshot" src="https://github.com/user-attachments/assets/190ec2ce-25ea-488d-9026-d3559c77d9b1" />

Answers:

First suspicious domain request: craftingalegacy.com
<img width="670" alt="Suspicious Domain Screenshot" src="https://github.com/user-attachments/assets/038b9155-186a-4c9e-af5e-0924031407f4" />

Term for address used to access websites: Domain Name

Attack using Unicode in domains: Punycode attack

Redirected website for https://tinyurl.com/bw7t8p4u
<img width="680" alt="Redirect Screenshot" src="https://github.com/user-attachments/assets/9d8e4842-94dc-497c-a27b-0537361d10cd" />

Task 5: Host Artifacts (Annoying)

Host artifacts include registry entries, processes, files, or IOCs left by attackers.

<div align="center"> <img width="680" alt="Host Artifacts Screenshot" src="https://github.com/user-attachments/assets/12ed3e3d-2ee9-4278-82e3-0d4df7d67c98" /> </div>

Questions:

IP for regidle.exe POST request: 96.126.101.6
<img width="630" alt="Regidle POST Screenshot" src="https://github.com/user-attachments/assets/c04d9fa6-7e98-4a17-8c21-bebafc8b69a6" />

Malicious executable dropped: G_jugk.exe
<img width="680" alt="Malicious EXE Screenshot" src="https://github.com/user-attachments/assets/df1e7812-8f7a-461c-8bce-e6ffa89fa7b5" />

Vendors detecting host as malicious: 9
<img width="740" alt="Vendors Screenshot" src="https://github.com/user-attachments/assets/2947cd16-945a-4844-84eb-098ca0b532be" />

Task 6: Network Artifacts (Annoying)

Network artifacts (yellow zone of Pyramid of Pain) are harder for attackers to change. Examples: User-Agent strings, C2 info, URI patterns.

TShark command to extract User-Agent strings:

tshark --Y http.request -T fields -e http.host -e http.user_agent -r analysis_file.pcap

<div align="center"> <img width="680" alt="TShark Screenshot" src="https://github.com/user-attachments/assets/4188b4b3-47df-48ed-b84c-64b62c0ba75c" /> </div>

Browser for the User-Agent string: Internet Explorer
<img width="670" alt="User Agent Browser Screenshot" src="https://github.com/user-attachments/assets/a07b1f4c-133b-4837-962d-618bc707d849" />
<img width="1200" alt="User Agent Wireshark Screenshot" src="https://github.com/user-attachments/assets/6e57d934-d56c-4ed4-a0d6-57357548a32c" />

Task 7: Tools (Challenging)

Attackers use utilities for maldocs, backdoors, EXEs, DLLs, payloads, or password crackers.

Threat hunting and detection tools: VirusTotal, Any.Run, SSDeep (Fuzzy Hashing), SOC Prime.

Method to determine file similarity: Fuzzy Hashing

Alternative name: context triggered piecewise hashes

<div align="center"> <img width="1440" alt="Fuzzy Hashing Screenshot" src="https://github.com/user-attachments/assets/1d27cb26-2074-4a56-aa23-b4f562d1ab5c" /> </div>
Task 8: TTPs (Tough)

TTPs = Tactics, Techniques & Procedures (MITRE ATT&CK Matrix). Detection is critical because attackers cannot easily change TTPs.

Exfiltration techniques in MITRE ATT&CK: 9
<img width="125" alt="Exfiltration Screenshot" src="https://github.com/user-attachments/assets/b2ff5396-0b73-4607-9164-0e4fc4242159" />

Chimera hacking group’s commercial RAT: Cobalt Strike
<img width="1155" alt="Cobalt Strike Screenshot" src="https://github.com/user-attachments/assets/ad031821-d7c4-4805-b6d7-68c7ad367be7" />

Task 9: Practical – The Pyramid of Pain

Completed static site flag: THM{PYRAMIDS_COMPLETE}

<div align="center"> <img width="665" alt="Static Site Screenshot" src="https://github.com/user-attachments/assets/72eb7680-92f4-4385-a74b-f7c61e67c60c" /> <img width="420" alt="Flag Screenshot" src="https://github.com/user-attachments/assets/d8aa8aa8-71d5-4d7c-a4dc-9c83ad823f9e" /> </div>
Conclusion

Completing the Pyramid of Pain – TryHackMe room strengthened both theoretical understanding and hands-on skills in threat hunting, incident response, and CTI.

Key takeaways:

Importance of the Pyramid of Pain in cybersecurity.

Limitations of relying solely on hash values as IOCs.

Analysis of IPs and domains, including Fast Flux and Punycode attacks.

Investigation of host artifacts (executables, registry, processes) and network artifacts (User-Agent strings, POST requests).

Tools and techniques: VirusTotal, Any.Run, SSDeep, SOC Prime, MITRE ATT&CK.

Detecting TTPs as high-level indicators to thwart attackers.

Practical experience completing the static site and obtaining the flag: THM{PYRAMIDS_COMPLETE}.
