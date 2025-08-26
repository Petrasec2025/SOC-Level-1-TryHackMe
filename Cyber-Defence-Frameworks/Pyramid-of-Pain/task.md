
<img width="1440" height="283" alt="Screenshot 2025-08-26 at 4 18 06 PM" src="https://github.com/user-attachments/assets/c2c60ef0-09e4-4088-b839-e12c9065bd6f" />

Task 1 Introduction

This well-renowned concept is being applied to cybersecurity solutions like Cisco Security, SentinelOne, and SOCRadar to improve the effectiveness of CTI (Cyber Threat Intelligence), threat hunting, and incident response exercises.

Understanding the Pyramid of Pain concept as a Threat Hunter, Incident Responder, or SOC Analyst is important.

Task 2 Hash Values (Trivial)

MD5 (Message Digest, defined by RFC 1321) — was designed by Ron Rivest in 1992 and is a widely used cryptographic hash function with a 128-bit hash value.

SHA-1 (Secure Hash Algorithm 1, defined by RFC 3174) -SHA-1 takes an input and produces a 160-bit hash value string as a 40 digit hexadecimal number. NIST deprecated the use of SHA-1 in 2011 and banned its use for digital signatures.

The SHA-2 (Secure Hash Algorithm 2) — SHA-2 Hashing Algorithm was designed by The National Institute of Standards and Technology (NIST) and the National Security Agency (NSA). The SHA-256 algorithm returns a hash value of 256-bits as a 64 digit hexadecimal number.

A hash is not considered to be cryptographically secure if two files have the same hash value or digest.

Various online tools can be used to do hash lookups like VirusTotal and Metadefender Cloud — OPSWAT.

As an attacker, modifying a file by even a single bit is trivial, which would produce a different hash value. With so many variations and instances of known malware or ransomware, threat hunting using file hashes as the IOC (Indicators of Compromise) can become difficult.

Press enter or click to view image in full size

<img width="691" height="225" alt="Screenshot 2025-08-26 at 4 56 59 PM" src="https://github.com/user-attachments/assets/39f87718-310f-49c8-844c-2ad07c65fe1d" />
Analyse the report associated with the hash “b8ef959a9176aef07fdca8705254a163b50b49a17217a4ff0107487f59d4a35d” here. What is the filename of the sample?

Sales_Receipt 5606.xls

Task 3 IP Address (Easy)

An IP address is used to identify any device connected to a network. We rely on IP addresses to send and receive the information over the network.

In the Pyramid of Pain, IP addresses are indicated with the color green. From a defense standpoint, knowledge of the IP addresses an adversary uses can be valuable. A common defense tactic is to block, drop, or deny inbound requests from IP addresses on your parameter or external firewall.

One of the ways an adversary can make it challenging to successfully carry out IP blocking is by using Fast Flux.

According to Akamai, Fast Flux is a DNS technique used by botnets to hide phishing, web proxying, malware delivery, and malware communication activities behind compromised hosts acting as proxies. The purpose of using the Fast Flux network is to make the communication between malware and its command and control server (C&C) challenging to be discovered by security professionals.

So, the primary concept of a Fast Flux network is having multiple IP addresses associated with a domain name, which is constantly changing.

Read the following report to answer this question. What is the first IP address the malicious process (PID 1632) attempts to communicate with?

50.87.136.52

Press enter or click to view image in full size
<img width="672" height="86" alt="Screenshot 2025-08-26 at 4 58 17 PM" src="https://github.com/user-attachments/assets/73b29b39-0ed7-4700-adcd-3f7dd268757a" />
Read the following report to answer this question. What is the first domain name the malicious process ((PID 1632) attempts to communicate with?

craftingalegacy.com

Task 4 Domain Names (Simple)

Domain Names can be thought as simply mapping an IP address to a string of text. A domain name can contain a domain and a top-level domain (evilcorp.com) or a sub-domain followed by a domain and top-level domain (tryhackme.evilcorp.com).
<img width="710" height="206" alt="Screenshot 2025-08-26 at 4 59 04 PM" src="https://github.com/user-attachments/assets/fcb6ef0b-9f4f-40cf-b807-626d467ac3d3" />
To detect the malicious domains, proxy logs or web server logs can be used.

Attackers usually hide the malicious domains under URL Shorteners. A URL Shortener is a tool that creates a short and unique URL that will redirect to the specific website specified during the initial step of setting up the URL Shortener link. According to Cofense, attackers use the following URL Shortening services to generate malicious links:

bit.ly, goo.gl , ow.ly , s.id, smarturl.it, tiny.pl, tinyurl.com , x.co

You can see the actual website the shortened link is redirecting you to by appending “+” to it (see the examples below). Type the shortened URL in the address bar of the web browser and add the above characters to see the redirect URL.

Press enter or click to view image in full size
<img width="635" height="409" alt="Screenshot 2025-08-26 at 5 00 01 PM" src="https://github.com/user-attachments/assets/10a74247-da1b-4798-b29d-4f6041e6e094" />
Viewing Connections in Any.run:
Because Any.run is a sandboxing service that executes the sample, we can review any connections such as HTTP requests, DNS requests or processes communicating with an IP address.

HTTP Requests:

This tab shows the recorded HTTP requests since the detonation of the sample. This can be useful to see what resources are being retrieved from a webserver, such as a dropper or a callback.

<img width="677" height="157" alt="Screenshot 2025-08-26 at 5 00 45 PM" src="https://github.com/user-attachments/assets/2092c9d8-c319-451e-867d-d04548157ff5" />
Connections:

This tab shows any communications made since the detonation of the sample. This can be useful to see if a process communicates with another host. For example, this could be C2 traffic, uploading/downloading files over FTP, etc.
<img width="673" height="158" alt="Screenshot 2025-08-26 at 5 01 27 PM" src="https://github.com/user-attachments/assets/cc2dcea9-3f6b-4c42-a69f-83af73a0b48a" />
DNS Requests:

This tab shows the DNS requests made since the detonation of the sample. Malware often makes DNS requests to check for internet connectivity (I.e. if It can’t reach the internet/call home, then it’s probably being sandboxed or is useless).
<img width="669" height="162" alt="Screenshot 2025-08-26 at 5 02 00 PM" src="https://github.com/user-attachments/assets/190ec2ce-25ea-488d-9026-d3559c77d9b1" />
Answer the questions below

Go to this report on app.any.run and provide the first suspicious domain request you are seeing, you will be using this report to answer the remaining questions of this task.

craftingalegacy.com
<img width="675" height="50" alt="Screenshot 2025-08-26 at 5 03 03 PM" src="https://github.com/user-attachments/assets/038b9155-186a-4c9e-af5e-0924031407f4" />
What term refers to an address used to access websites?

Domain Name

What type of attack uses Unicode characters in the domain name to imitate the a known domain?

Punycode attack

Provide the redirected website for the shortened URL using a preview: https://tinyurl.com/bw7t8p4u

Press enter or click to view image in full size
<img width="684" height="298" alt="Screenshot 2025-08-26 at 5 03 53 PM" src="https://github.com/user-attachments/assets/9d8e4842-94dc-497c-a27b-0537361d10cd" />
Task 5 Host Artifacts (Annoying)

Host artifacts are the traces or observables that attackers leave on the system, such as registry values, suspicious process execution, attack patterns or IOCs (Indicators of Compromise), files dropped by malicious applications, or anything exclusive to the current threat.
<img width="684" height="185" alt="Screenshot 2025-08-26 at 5 04 00 PM" src="https://github.com/user-attachments/assets/12ed3e3d-2ee9-4278-82e3-0d4df7d67c98" />

A process named regidle.exe makes a POST request to an IP address based in the United States (US) on port 8080. What is the IP address?

96.126.101.6
<img width="631" height="24" alt="Screenshot 2025-08-26 at 5 05 49 PM" src="https://github.com/user-attachments/assets/c04d9fa6-7e98-4a17-8c21-bebafc8b69a6" />
The actor drops a malicious executable (EXE). What is the name of this executable?

G_jugk.exe
<img width="680" height="83" alt="Screenshot 2025-08-26 at 5 06 22 PM" src="https://github.com/user-attachments/assets/df1e7812-8f7a-461c-8bce-e6ffa89fa7b5" />

Look at this report by Virustotal. How many vendors determine this host to be malicious?

9
<img width="739" height="725" alt="Screenshot 2025-08-26 at 5 07 18 PM" src="https://github.com/user-attachments/assets/2947cd16-945a-4844-84eb-098ca0b532be" />

Task 6 Network Artifacts (Annoying)

Network Artifacts also belong to the yellow zone in the Pyramid of Pain. This means if you can detect and respond to the threat, the attacker would need more time to go back and change his tactics or modify the tools, which gives you more time to respond and detect the upcoming threats or remediate the existing ones.

A network artifact can be a user-agent string, C2 information, or URI patterns followed by the HTTP POST requests.An attacker might use a User-Agent string that hasn’t been observed in your environment before or seems out of the ordinary. The User-Agent is defined by RFC2616 as the request-header field that contains the information about the user agent originating the request.

Network artifacts can be detected in Wireshark PCAPs (file that contains the packet data of a network) by using a network protocol analyzer such as TShark or exploring IDS (Intrusion Detection System) logging from a source such as Snort.
<img width="678" height="127" alt="Screenshot 2025-08-26 at 5 08 09 PM" src="https://github.com/user-attachments/assets/4188b4b3-47df-48ed-b84c-64b62c0ba75c" />
Let’s use TShark to filter out the User-Agent strings by using the following command: tshark --Y http.request -T fields -e http.host -e http.user_agent -r analysis_file.pcap

Command Breakdown
tshark: The terminal-based version of Wireshark, a network protocol analyzer.
--Y http.request: This option applies a display filter to only show packets that are HTTP requests.
-T fields: Specifies that the output should be in a custom field format.
-e http.host: Adds the HTTP host field to the output, which shows the host of the HTTP request.
-e http.user_agent: Adds the HTTP user-agent field to the output, which shows the user-agent string (typically identifying the client software making the request).
-r analysis_file.pcap: Reads the packets from the specified PCAP file (analysis_file.pcap).
What This Command Does
When you run this command, tshark processes the given PCAP file, applies the HTTP request filter, and then extracts and displays only the HTTP host and user-agent fields for each matching packet. The output will be a list of hosts and user-agents from the HTTP requests in the capture file.
<img width="668" height="158" alt="Screenshot 2025-08-26 at 5 09 01 PM" src="https://github.com/user-attachments/assets/3ddb1b48-3fbc-45f6-82db-84477af3ba84" />
What browser uses the User-Agent string shown in the screenshot above?

Internet Explorer
<img width="670" height="246" alt="Screenshot 2025-08-26 at 5 09 20 PM" src="https://github.com/user-attachments/assets/a07b1f4c-133b-4837-962d-618bc707d849" />
<img width="1206" height="468" alt="Screenshot 2025-08-26 at 5 09 59 PM" src="https://github.com/user-attachments/assets/6e57d934-d56c-4ed4-a0d6-57357548a32c" />

Task 7 Tools (Challenging)

Attackers would use the utilities to create malicious macro documents (maldocs) for spearphishing attempts, a backdoor that can be used to establish C2 (Command and Control Infrastructure), any custom .EXE, and .DLL files, payloads, or password crackers.

Antivirus signatures, detection rules, and YARA rules can be great weapons for you to use against attackers at this stage.

MalwareBazaar and Malshare are good resources to provide you with access to the samples, malicious feeds, and YARA results — these all can be very helpful when it comes to threat hunting and incident response.

For detection rules, SOC Prime Threat Detection Marketplace is a great platform, where security professionals share their detection rules for different kinds of threats including the latest CVE’s that are being exploited in the wild by adversaries.

Fuzzy hashing is also a strong weapon against the attacker’s tools. Fuzzy hashing helps you to perform similarity analysis — match two files with minor differences based on the fuzzy hash values. One of the examples of fuzzy hashing is the usage of SSDeep; on the SSDeep official website, you can also find the complete explanation for fuzzy hashing.For detection rules, SOC Prime Threat Detection Marketplace is a great platform, where security professionals share their detection rules for different kinds of threats including the latest CVE’s that are being exploited in the wild by adversaries.

Fuzzy hashing is also a strong weapon against the attacker’s tools. Fuzzy hashing helps you to perform similarity analysis — match two files with minor differences based on the fuzzy hash values. One of the examples of fuzzy hashing is the usage of SSDeep; on the SSDeep official website, you can also find the complete explanation for fuzzy hashing.

Provide the method used to determine similarity between the files.

Fuzzy Hashing

Provide the alternative name for fuzzy hashes without the abbreviation.

context triggered piecewise hashes
<img width="1440" height="575" alt="Screenshot 2025-08-26 at 5 10 49 PM" src="https://github.com/user-attachments/assets/1d27cb26-2074-4a56-aa23-b4f562d1ab5c" />
Task 8 TTPs (Tough)

TTPs stands for Tactics, Techniques & Procedures. This includes the whole MITRE ATT&CK Matrix, which means all the steps taken by an adversary to achieve his goal, starting from phishing attempts to persistence and data exfiltration.

If you can detect and respond to the TTPs quickly, you leave the adversaries almost no chance to fight back.

For, example if you could detect a Pass-the-Hash attack using Windows Event Log Monitoring and remediate it, you would be able to find the compromised host very quickly and stop the lateral movement inside your network.

Navigate to ATT&CK Matrix webpage. How many techniques fall under the Exfiltration category?

9

<img width="124" height="721" alt="Screenshot 2025-08-26 at 5 11 37 PM" src="https://github.com/user-attachments/assets/b2ff5396-0b73-4607-9164-0e4fc4242159" />

Chimera is a China-based hacking group that has been active since 2018. What is the name of the commercial, remote access tool they use for C2 beacons and data exfiltration?

Cobalt Strike

<img width="1155" height="532" alt="Screenshot 2025-08-26 at 5 12 07 PM" src="https://github.com/user-attachments/assets/ad031821-d7c4-4805-b6d7-68c7ad367be7" />

Task 9 Practical: The Pyramid of Pain

Complete the static site. What is the flag?

THM{PYRAMIDS_COMPLETE}
<img width="665" height="556" alt="Screenshot 2025-08-26 at 5 12 36 PM" src="https://github.com/user-attachments/assets/72eb7680-92f4-4385-a74b-f7c61e67c60c" />
<img width="416" height="191" alt="Screenshot 2025-08-26 at 5 12 43 PM" src="https://github.com/user-attachments/assets/d8aa8aa8-71d5-4d7c-a4dc-9c83ad823f9e" />

Conclusion

Completing the Pyramid of Pain – TryHackMe room allowed me to strengthen both my theoretical understanding and hands-on technical skills in threat hunting, incident response, and cyber threat intelligence (CTI).

From this room, I learned:

The significance of the Pyramid of Pain in cybersecurity and how different indicators of compromise (IOCs) affect attackers differently.

Why hash values are trivial for attackers to change and the limitations of relying solely on them for detection.

How IP addresses and domains can be analyzed, including detecting malicious activity such as Fast Flux networks and Punycode attacks.

How to investigate host artifacts (executables, registry changes, processes) and network artifacts (User-Agent strings, POST requests) using tools like Wireshark and TShark.

The role of tools and techniques like VirusTotal, Any.Run, SSDeep (fuzzy hashing), SOC Prime, and MITRE ATT&CK in analyzing malware and attacker behaviors.

The importance of detecting Tactics, Techniques & Procedures (TTPs), which are the hardest for adversaries to change, making them the most powerful indicators for defenders.

Gained practical experience by completing the static site challenge and earning the flag THM{PYRAMIDS_COMPLETE}.

Overall, this room reinforced my ability to detect, analyze, and respond to threats effectively while emphasizing the value of focusing on higher-level adversary behaviors (TTPs) rather than just low-level indicators.

