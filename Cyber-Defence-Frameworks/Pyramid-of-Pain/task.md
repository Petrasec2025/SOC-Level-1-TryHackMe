Pyramid of Pain – TryHackMe Lab Report
Task 1: Introduction
<img width="1440" height="283" alt="Screenshot 2025-08-26 at 4 18 06 PM" src="https://github.com/user-attachments/assets/c2c60ef0-09e4-4088-b839-e12c9065bd6f" />

This well-renowned concept is being applied to cybersecurity solutions like Cisco Security, SentinelOne, and SOCRadar to improve the effectiveness of CTI (Cyber Threat Intelligence), threat hunting, and incident response exercises.

Understanding the Pyramid of Pain concept as a Threat Hunter, Incident Responder, or SOC Analyst is important.

Task 2: Hash Values (Trivial)

MD5 (Message Digest, defined by RFC 1321) — was designed by Ron Rivest in 1992 and is a widely used cryptographic hash function with a 128-bit hash value.

SHA-1 (Secure Hash Algorithm 1, defined by RFC 3174) — SHA-1 takes an input and produces a 160-bit hash value string as a 40-digit hexadecimal number. NIST deprecated the use of SHA-1 in 2011 and banned its use for digital signatures.

SHA-2 (Secure Hash Algorithm 2) — SHA-2 Hashing Algorithm was designed by NIST and NSA. The SHA-256 algorithm returns a hash value of 256 bits as a 64-digit hexadecimal number.

A hash is not considered cryptographically secure if two files have the same hash value or digest.

Various online tools can be used to do hash lookups like VirusTotal and Metadefender Cloud — OPSWAT.

As an attacker, modifying a file by even a single bit is trivial, which would produce a different hash value. With so many variations and instances of known malware or ransomware, threat hunting using file hashes as the IOC (Indicators of Compromise) can become difficult.

<img width="691" height="225" alt="Screenshot 2025-08-26 at 4 56 59 PM" src="https://github.com/user-attachments/assets/39f87718-310f-49c8-844c-2ad07c65fe1d" />

Question: Analyse the report associated with the hash b8ef959a9176aef07fdca8705254a163b50b49a17217a4ff0107487f59d4a35d. What is the filename of the sample?
Answer: Sales_Receipt 5606.xls

Task 3: IP Address (Easy)

An IP address is used to identify any device connected to a network. In the Pyramid of Pain, IP addresses are indicated with the color green. Knowledge of IP addresses can help block malicious activity on firewalls.

Adversaries can bypass IP blocking using Fast Flux — a DNS technique used by botnets to hide phishing, malware delivery, and C&C communication behind constantly changing IP addresses.

Question 1: What is the first IP address the malicious process (PID 1632) attempts to communicate with?
Answer: 50.87.136.52

<img width="672" height="86" alt="Screenshot 2025-08-26 at 4 58 17 PM" src="https://github.com/user-attachments/assets/73b29b39-0ed7-4700-adcd-3f7dd268757a" />

Question 2: What is the first domain name the malicious process (PID 1632) attempts to communicate with?
Answer: craftingalegacy.com

Task 4: Domain Names (Simple)

Domain Names map IP addresses to readable strings. They can be:

Domain + TLD: evilcorp.com

Subdomain + Domain + TLD: tryhackme.evilcorp.com

<img width="710" height="206" alt="Screenshot 2025-08-26 at 4 59 04 PM" src="https://github.com/user-attachments/assets/fcb6ef0b-9f4f-40cf-b807-626d467ac3d3" />

Attackers often hide malicious domains using URL shorteners:

bit.ly, goo.gl, ow.ly, s.id, smarturl.it, tiny.pl, tinyurl.com, x.co

Preview shortened URLs by appending + to see the redirect.

<img width="635" height="409" alt="Screenshot 2025-08-26 at 5 00 01 PM" src="https://github.com/user-attachments/assets/10a74247-da1b-4798-b29d-4f6041e6e094" />

Any.Run Analysis Tabs:

HTTP Requests

<img width="677" height="157" alt="Screenshot 2025-08-26 at 5 00 45 PM" src="https://github.com/user-attachments/assets/2092c9d8-c319-451e-867d-d04548157ff5" />

Connections

<img width="673" height="158" alt="Screenshot 2025-08-26 at 5 01 27 PM" src="https://github.com/user-attachments/assets/cc2dcea9-3f6b-4c42-a69f-83af73a0b48a" />

DNS Requests

<img width="669" height="162" alt="Screenshot 2025-08-26 at 5 02 00 PM" src="https://github.com/user-attachments/assets/190ec2ce-25ea-488d-9026-d3559c77d9b1" />

Answers:

First suspicious domain request: craftingalegacy.com

<img width="675" height="50" alt="Screenshot 2025-08-26 at 5 03 03 PM" src="https://github.com/user-attachments/assets/038b9155-186a-4c9e-af5e-0924031407f4" />

Term referring to an address used to access websites: Domain Name

Attack using Unicode characters in a domain: Punycode attack

Redirected website for https://tinyurl.com/bw7t8p4u

<img width="684" height="298" alt="Screenshot 2025-08-26 at 5 03 53 PM" src="https://github.com/user-attachments/assets/9d8e4842-94dc-497c-a27b-0537361d10cd" />
Task 5: Host Artifacts (Annoying)

Host artifacts include traces left by attackers such as registry entries, processes, files, or other IOCs.

<img width="684" height="185" alt="Screenshot 2025-08-26 at 5 04 00 PM" src="https://github.com/user-attachments/assets/12ed3e3d-2ee9-4278-82e3-0d4df7d67c98" />

Questions:

IP for regidle.exe POST request: 96.126.101.6

<img width="631" height="24" alt="Screenshot 2025-08-26 at 5 05 49 PM" src="https://github.com/user-attachments/assets/c04d9fa6-7e98-4a17-8c21-bebafc8b69a6" />

Malicious executable dropped: G_jugk.exe

<img width="680" height="83" alt="Screenshot 2025-08-26 at 5 06 22 PM" src="https://github.com/user-attachments/assets/df1e7812-8f7a-461c-8bce-e6ffa89fa7b5" />

Vendors detecting host as malicious: 9

<img width="739" height="725" alt="Screenshot 2025-08-26 at 5 07 18 PM" src="https://github.com/user-attachments/assets/2947cd16-945a-4844-84eb-098ca0b532be" />
Task 6: Network Artifacts (Annoying)

Network artifacts are harder to change by attackers and provide high-value indicators (yellow zone of Pyramid of Pain).

User-Agent strings, C2 info, URI patterns, etc., can be detected using Wireshark or TShark.

TShark command example:

tshark --Y http.request -T fields -e http.host -e http.user_agent -r analysis_file.pcap

<img width="678" height="127" alt="Screenshot 2025-08-26 at 5 08 09 PM" src="https://github.com/user-attachments/assets/4188b4b3-47df-48ed-b84c-64b62c0ba75c" />

Browser for the User-Agent string: Internet Explorer

<img width="670" height="246" alt="Screenshot 2025-08-26 at 5 09 20 PM" src="https://github.com/user-attachments/assets/a07b1f4c-133b-4837-962d-618bc707d849" />
<img width="1206" height="468" alt="Screenshot 2025-08-26 at 5 09 59 PM" src="https://github.com/user-attachments/assets/6e57d934-d56c-4ed4-a0d6-57357548a32c" />
Task 7: Tools (Challenging)

Attackers use utilities to create maldocs, backdoors, EXEs, DLLs, payloads, or password crackers.

Threat hunting and detection: VirusTotal, Any.Run, SSDeep (Fuzzy Hashing), SOC Prime.

Fuzzy hashing: determines similarity between files.

Answers:

Method to determine similarity: Fuzzy Hashing

Alternative name: context triggered piecewise hashes

<img width="1440" height="575" alt="Screenshot 2025-08-26 at 5 10 49 PM" src="https://github.com/user-attachments/assets/1d27cb26-2074-4a56-aa23-b4f562d1ab5c" />
Task 8: TTPs (Tough)

TTPs (Tactics, Techniques & Procedures) are hardest for attackers to change and critical for detection.

Exfiltration techniques in MITRE ATT&CK: 9

<img width="124" height="721" alt="Screenshot 2025-08-26 at 5 11 37 PM" src="https://github.com/user-attachments/assets/b2ff5396-0b73-4607-9164-0e4fc4242159" />

Chimera hacking group’s commercial RAT for C2: Cobalt Strike

<img width="1155" height="532" alt="Screenshot 2025-08-26 at 5 12 07 PM" src="https://github.com/user-attachments/assets/ad031821-d7c4-4805-b6d7-68c7ad367be7" />
Task 9: Practical – The Pyramid of Pain

Completed static site flag: THM{PYRAMIDS_COMPLETE}

<img width="665" height="556" alt="Screenshot 2025-08-26 at 5 12 36 PM" src="https://github.com/user-attachments/assets/72eb7680-92f4-4385-a74b-f7c61e67c60c" />
<img width="416" height="191" alt="Screenshot 2025-08-26 at 5 12 43 PM" src="https://github.com/user-attachments/assets/d8aa8aa8-71d5-4d7c-a4dc-9c83ad823f9e" />
Conclusion

Completing the Pyramid of Pain – TryHackMe room strengthened both theoretical understanding and hands-on skills in threat hunting, incident response, and CTI.

Key takeaways:

The significance of the Pyramid of Pain in cybersecurity.

Limitations of relying solely on hash values as IOCs.

Analysis of IPs and domains, including Fast Flux and Punycode attacks.

Investigation of host artifacts (executables, registry changes, processes) and network artifacts (User-Agent strings, POST requests).

Tools and techniques like VirusTotal, Any.Run, SSDeep, SOC Prime, MITRE ATT&CK for malware analysis.

Detecting TTPs as the highest-level indicators to thwart attackers effectively.

Practical experience completing the static site and obtaining the flag: THM{PYRAMIDS_COMPLETE}.

