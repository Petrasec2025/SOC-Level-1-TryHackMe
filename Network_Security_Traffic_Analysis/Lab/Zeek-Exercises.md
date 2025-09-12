Network Forensics Analysis with Zeek
---
![TryHackMe User](https://img.shields.io/badge/TryHackMe-Petras20-blue)
![Completion](https://img.shields.io/badge/Completion-100%25-brightgreen)
![Zeek Log Analysis](https://img.shields.io/badge/Zeek-Log%20Analysis-orange)
![TryHackMe Profile](https://img.shields.io/badge/TryHackMe-Profile-red)


---
<img width="1331" height="551" alt="Screenshot 2025-09-12 at 7 59 50 PM" src="https://github.com/user-attachments/assets/788c6df8-63fd-461a-a141-671e09b8f7ba" />

Task 1 Introduction

#1.1 Read above.

Answer: No answer is needed.
---
Task 2 Anomalous DNS

#2.1 Investigate the dns-tunneling.pcap file. Investigate the dns.log file. What is the number of DNS records linked to the IPv6 address?

Command:

Generate DNS logs

zeek -C -r dns-tunneling.pcap -s dns.log

Search the number of DNS records linked to the IPV6 address

cat dns.log | grep “AAAA” | wc -l

<img width="681" height="70" alt="Screenshot 2025-09-12 at 8 00 58 PM" src="https://github.com/user-attachments/assets/46c84c4e-d964-419c-8e43-a3dcb0e1a43d" />
Answer: 320
---

#2.2 Investigate the conn.log file. What is the longest connection duration?

See the structure of the file.

Head conn.log

Press enter or click to view image in full size

<img width="672" height="337" alt="Screenshot 2025-09-12 at 8 01 09 PM" src="https://github.com/user-attachments/assets/9b84f11b-9bcc-4109-a14b-b5c684837bab" />

Print duration and sort in descending order

<img width="677" height="44" alt="Screenshot 2025-09-12 at 8 02 36 PM" src="https://github.com/user-attachments/assets/c8fc5b5e-b0e3-48d7-a783-fe2567b0324a" />

cat conn.log | zeek-cut duration | sort -n | uniq

<img width="279" height="271" alt="Screenshot 2025-09-12 at 8 02 43 PM" src="https://github.com/user-attachments/assets/081a25c5-39e3-47cf-b24a-a6393dd206f9" />

Answer: 9.420791
---
#2.3 Investigate the dns.log file. Filter all unique DNS queries. What is the number of unique domain queries?

See the structure of the file.

Head dns.log

<img width="677" height="297" alt="Screenshot 2025-09-12 at 8 02 50 PM" src="https://github.com/user-attachments/assets/42ae0591-6575-45c8-bb6e-19848a733931" />

Search all unique domain queries.

Command: cat dns.log | zeek-cut query |rev | cut -d ‘.’ -f 1–2 | rev | sort | uniq

<img width="675" height="149" alt="Screenshot 2025-09-12 at 8 02 58 PM" src="https://github.com/user-attachments/assets/9dbca62a-c568-4d97-ac58-d6fb2573b445" />

Answer: 6
---
#2.4 There is a massive amount of DNS queries sent to the same domain. This is abnormal. Let’s find out which hosts are involved in this activity. Investigate the conn.log file. What is the IP address of the source host?

See the structure of the file.

<img width="686" height="364" alt="Screenshot 2025-09-12 at 8 04 33 PM" src="https://github.com/user-attachments/assets/2cd752eb-c43d-4480-b777-7097462eafb8" />

Find the source ip address.

Command: cat dns.log | zeek-cut id.orig_h

<img width="760" height="474" alt="Screenshot 2025-09-12 at 8 04 41 PM" src="https://github.com/user-attachments/assets/5e8537ad-0ea1-46ab-a16e-d41aeaeeb879" />

Answer: 10.20.57.3
---
Task 3 Phishing

#3.1 Investigate the logs. What is the suspicious source address? Enter your answer in defanged format.

Generate logs.

<img width="682" height="171" alt="Screenshot 2025-09-12 at 8 04 49 PM" src="https://github.com/user-attachments/assets/38099b63-05c1-4498-85e1-a67e121a49f3" />

Check conn.log.

Cat conn.log

<img width="657" height="171" alt="Screenshot 2025-09-12 at 8 04 58 PM" src="https://github.com/user-attachments/assets/8586250e-ae7b-4b91-a8d5-943bc4b2d2b8" />

defanged format: 10[.]6[.]27[.]102

Answer: 10[.]6[.]27[.]102

#3.2 Investigate the http.log file. Which domain address were the malicious files downloaded from? Enter your answer in defanged format.

Verify the format of the file.

<img width="283" height="105" alt="Screenshot 2025-09-12 at 8 05 07 PM" src="https://github.com/user-attachments/assets/3c342986-9545-4cae-9849-3daab72f0105" />

Review the log.

<img width="253" height="90" alt="Screenshot 2025-09-12 at 8 05 14 PM" src="https://github.com/user-attachments/assets/2d96c490-9c2f-419b-94ee-f629a59f0b31" />

Pass to defang format:

Using CyberChef

Link: https://gchq.github.io/CyberChef/#recipe=Defang_URL(true,true,true,'Valid%20domains%20and%20full%20URLs')&input=c21hcnQtZmF4LmNvbQ

Press enter or click to view image in full size

<img width="705" height="305" alt="Screenshot 2025-09-12 at 8 05 21 PM" src="https://github.com/user-attachments/assets/85ea0d86-1e30-48d8-b28b-eb73e098153f" />

Answer: smart-fax[.]com

#3.3 Investigate the malicious document in VirusTotal. What kind of file is associated with the malicious document?

To respond to this question, we should use the next command:

zeek -C -r phishing.pcap file-extract-demo.zeek

<img width="673" height="120" alt="Screenshot 2025-09-12 at 8 05 33 PM" src="https://github.com/user-attachments/assets/3ffc1b02-99c7-4b77-aeda-a6f457c786fb" />

Cat files.log -> view files.log

zeek -C -r phishing.pcap hash-demo.zeek

<img width="677" height="49" alt="Screenshot 2025-09-12 at 8 05 42 PM" src="https://github.com/user-attachments/assets/55908a4f-4d46-436d-8ada-eb61a46a4e95" />

cat files.log | zeek-cut md5

<img width="681" height="91" alt="Screenshot 2025-09-12 at 8 05 52 PM" src="https://github.com/user-attachments/assets/906d022a-8db2-4480-b249-e9f290f71871" />

Extract files

File extract_files/* | nl

<img width="679" height="205" alt="Screenshot 2025-09-12 at 8 06 01 PM" src="https://github.com/user-attachments/assets/fa37c72a-7fbc-445a-a433-cfc9dad7bc51" />

cat files.log | zeek-cut puid conn_uids tx_hosts rx_hosts mine_type extracted | nl

Press enter or click to view image in full size

<img width="677" height="96" alt="Screenshot 2025-09-12 at 8 06 10 PM" src="https://github.com/user-attachments/assets/073d8f9b-c623-4aee-b313-9bb02f2e4cb3" />

Find hash md5

cat files.log | zeek-cut md5 puid conn_uids tx_hosts rx_hosts mine_type extracted | nl

<img width="678" height="194" alt="Screenshot 2025-09-12 at 8 06 18 PM" src="https://github.com/user-attachments/assets/30d59f67-2c28-41e6-9eb5-defa9ce5a27d" />

Search in virustotal: b5243ec1df7d1d5304189e7db2744128

Press enter or click to view image in full size

<img width="657" height="480" alt="Screenshot 2025-09-12 at 8 06 25 PM" src="https://github.com/user-attachments/assets/aa1080d2-f699-4875-a46b-bd8ca6a71090" />


<img width="697" height="213" alt="Screenshot 2025-09-12 at 8 06 34 PM" src="https://github.com/user-attachments/assets/0060dc0a-ceb6-4ae5-a5e9-2ac77bcf5791" />

Answer: VBA

#3.4 Investigate the extracted malicious .exe file. What is the given file name in Virustotal?

Check in the page of Virustotal.

We had the hash md5 from the preview exercise.

Hash md5: 749e161661290e8a2d190b1a66469744127bc25bf46e5d0c6f2e835f4b92db18

Press enter or click to view image in full size

<img width="742" height="246" alt="Screenshot 2025-09-12 at 8 06 41 PM" src="https://github.com/user-attachments/assets/d43841f6-43a6-47ae-97c6-4d57adfd7756" />

Answer: PleaseWaitWindow.exe

#3.5 Investigate the malicious .exe file in VirusTotal. What is the contacted domain name? Enter your answer in defanged format.

Hash md5: 749e161661290e8a2d190b1a66469744127bc25bf46e5d0c6f2e835f4b92db18

Press enter or click to view image in full size

<img width="756" height="547" alt="Screenshot 2025-09-12 at 8 06 48 PM" src="https://github.com/user-attachments/assets/6992f456-943f-45b7-a278-322e7eb46bb8" />

Go to CyberChef

Convert URL in Defang format.

<img width="682" height="375" alt="Screenshot 2025-09-12 at 8 06 57 PM" src="https://github.com/user-attachments/assets/28ca481a-7bd4-4e23-96ff-e4155042ee5a" />

Answer: hopto[.]org

#3.6 Investigate the http.log file. What is the request name of the downloaded malicious .exe file?

Verify the log.

Cat http.log

<img width="678" height="208" alt="Screenshot 2025-09-12 at 8 16 22 PM" src="https://github.com/user-attachments/assets/b617f85b-a311-4085-8cb5-6af51f13486b" />

Search extensions in the file

cat http.log | zeek-cut uri

<img width="679" height="115" alt="Screenshot 2025-09-12 at 8 16 29 PM" src="https://github.com/user-attachments/assets/e0a184f2-68b4-41c4-856c-03bd5384a9dc" />

Answer: knr.exe

Task 4 Log4J

#4.1 Investigate the log4shell.pcapng file with detection-log4j.zeek script. Investigate the signature.log file. What is the number of signature hits?

Generate logs.

zeek -C -r log4shell.pcapng detection-log4j.zeek

<img width="676" height="110" alt="Screenshot 2025-09-12 at 8 16 38 PM" src="https://github.com/user-attachments/assets/292892a3-8819-472f-ba82-67ee220ecb18" />

Count the number of signatures hits.

Command: cat signatures.log | zeek-cut sig_id | wc -l

<img width="955" height="76" alt="Screenshot 2025-09-12 at 8 17 05 PM" src="https://github.com/user-attachments/assets/1d4d0649-1459-4506-9b7c-de4e01fc2607" />

Answer: 3

#4.2 Investigate the http.log file. Which tool is used for scanning?

Check the file.

Head http.log

<img width="684" height="369" alt="Screenshot 2025-09-12 at 8 17 13 PM" src="https://github.com/user-attachments/assets/3cd14350-3a3f-4f8c-8645-fd5635409ff6" />

Filter by the tool

Command: cat http.log | zeek-cut user_agent

<img width="681" height="63" alt="Screenshot 2025-09-12 at 8 17 23 PM" src="https://github.com/user-attachments/assets/ed89c629-7b1d-4e98-8d26-ec1a6797169e" />

Result:

<img width="683" height="182" alt="Screenshot 2025-09-12 at 8 17 30 PM" src="https://github.com/user-attachments/assets/3086bcb4-d0b7-4066-a8b8-9ef4eeacf1f3" />

Answer: nmap

#4.3 Investigate the http.log file. What is the extension of the exploit file?

Search the extension of the exploit file.

<img width="679" height="177" alt="Screenshot 2025-09-12 at 8 17 41 PM" src="https://github.com/user-attachments/assets/76074a9e-9536-4d8d-876e-95bf8e8e4c0c" />

Answer: .class

#4.4 Investigate the log4j.log file. Decode the base64 commands. What is the name of the created file?

Check the file log4j.log

<img width="676" height="152" alt="Screenshot 2025-09-12 at 8 17 48 PM" src="https://github.com/user-attachments/assets/070cd209-c4f7-42d3-844b-d0cedacc3df8" />

Decode the base64 command.

echo ‘d2hpY2ggbmMgPiAvdG1wL3B3bmVkCg==’ | base64 –d

<img width="675" height="61" alt="Screenshot 2025-09-12 at 8 18 04 PM" src="https://github.com/user-attachments/assets/5f628716-6b0c-4485-bf27-73f0f1a8d2b5" />

Answer: pwned

Task 5 Conclusion

Answer: No answer is needed.
