
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


