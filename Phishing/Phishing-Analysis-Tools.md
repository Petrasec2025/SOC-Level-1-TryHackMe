# Phishing Analysis Tools Room Walkthrough

![Room Banner](https://github.com/user-attachments/assets/bf2f21b1-43f3-4d24-9a7a-70701a66483f)

## 🏆 Badges
![Phishing](https://img.shields.io/badge/Phishing-Analysis_Tools-0078D6?style=for-the-badge&logo=shield&logoColor=white)
![Email Security](https://img.shields.io/badge/Email_Security-Forensics-00C800?style=for-the-badge&logo=mail&logoColor=white)
![Difficulty](https://img.shields.io/badge/Difficulty-Intermediate-FFA500?style=for-the-badge)
![Platform](https://img.shields.io/badge/Platform-TryHackMe-FF0000?style=for-the-badge&logo=tryhackme&logoColor=white)
![Completion](https://img.shields.io/badge/Completion-100%25-00FF00?style=for-the-badge)
![Tools](https://img.shields.io/badge/Tools-PhishTool|AnyRun-800080?style=for-the-badge)

## Overview
Phishing Analysis Tools
Learn the tools used to aid an analyst to investigate suspicious emails.

**Link:** [https://tryhackme.com/room/phishingemails3tryoe](https://tryhackme.com/room/phishingemails3tryoe)

---

## Task 1: Introduction

No answer needed

![Task 1 Introduction](https://github.com/user-attachments/assets/25745ada-1690-46c0-af87-aa150a468667)

---

## Task 2: What information should we collect?

No answer needed

![Task 2 Information Collection](https://github.com/user-attachments/assets/9f5a3460-9420-4221-a283-64dfb03dccc1)

---

## Task 3: Email header analysis

### What is the official site name of the bank that capitai-one.com tried to resemble?
Google the website capitai-one.com

![Capital One Impersonation](https://github.com/user-attachments/assets/18d08306-5cc6-4f44-afae-e859146893b5)

**Answer:** `capitalone.com`

---

## Task 4: Email body analysis

### How can you manually get the location of a hyperlink?

![Hyperlink Location](https://github.com/user-attachments/assets/0fb1c8ee-12e4-4811-b857-7a27fdc8f270)

**Answer:** `Copy Link Location`

---

## Task 5: Malware Sandbox

No answer needed

![Task 5 Malware Sandbox](https://github.com/user-attachments/assets/c5efa7b3-b2f9-47f9-9301-e8ba4bb2d99b)

---

## Task 6: PhishTool

### Look at the Strings output. What is the name of the EXE file?
You can find the answer in the strings section:

![PhishTool Strings Output](https://github.com/user-attachments/assets/c898576e-1a9f-4522-ac39-2d945ef353af)

**Answer:** `#454326_PDF.exe`

---

## Task 7: Phishing Case 1

### What brand was this email tailored to impersonate?
I used phishtool to get informations

![Netflix Impersonation](https://github.com/user-attachments/assets/c8fa95f0-7876-4d14-9052-14ae5b9d1f77)

**Answer:** `Netflix`

### What is the From email address?
![From Email Address](https://github.com/user-attachments/assets/02523cb0-8b11-4fca-b8ec-c14736fbfc72)

**Answer:** `JGQ47wazXe1xYVBrkeDg-JOg7ODDQwWdR@JOg7ODDQwWdR-yVkCaBkTNp.gogolecloud.com`

### What is the originating IP? Defang the IP address.
![Originating IP](https://github.com/user-attachments/assets/1cdecee8-285b-4629-be53-983e4f8d3c68)

I used cyberchef to defang the IP address

![CyberChef Defanging](https://github.com/user-attachments/assets/da822ab1-5c88-442d-90fc-ba892db3f7ac)

**Answer:** `209[.]85[.]167[.]226`

### From what you can gather, what do you think will be a domain of interest? Defang the domain.
You can find this information in the Return-path of the mail:

![Return Path Domain](https://github.com/user-attachments/assets/63d9649b-bf77-453e-9d04-efaca3cfa95e)

Defang it with cyberchef

**Answer:** `etekno[.]xyz`

### What is the shortened URL? Defang the URL.
In the message URLs you have the link

![Shortened URL](https://github.com/user-attachments/assets/79409c7a-6f3c-4fa2-9f8e-eb2266c7435a)

Just defang it with cyberchef

**Answer:** `hxxps[://]t[.]co/yuxfzm8kpg?amp=1`

---

## Task 8: Phishing Case 2

### What does AnyRun classify this email as?
You have the banner on the right of anyrun

![AnyRun Classification](https://github.com/user-attachments/assets/21f7e737-aa09-4ee5-bf1c-d79a5abc4f7b)

**Answer:** `Suspicious activity`

### What is the name of the PDF file?
![PDF File Name](https://github.com/user-attachments/assets/0d93a841-47df-49ba-8bd5-e7f0a4bbded0)

Open the text report

![Text Report](https://github.com/user-attachments/assets/d8c952f5-39ed-463f-a862-db6933a4a7fb)

![PDF Details](https://github.com/user-attachments/assets/af999667-bd5c-44d3-bf71-a70caa0beca3)

**Answer:** `CC6F1A04B10BCB168AEEC8D870B97BD7C20FC161E8310B5BCE1AF8ED420E2C24`

### What two IP addresses are classified as malicious? Defang the IP addresses. (answer: IP_ADDR,IP_ADDR)
On the text report document, find the connections section, get malicious reputation IP

![Malicious IPs](https://github.com/user-attachments/assets/30a730ee-f939-4268-8fd7-1123af7ad871)

![IP Connections](https://github.com/user-attachments/assets/2d728772-61f3-44c4-9d6c-20ec3502f75b)

Defang with cyberchef

**Answer:** `2[.]16[.]107[.]24,2[.]16[.]107[.]83`

### What Windows process was flagged as Potentially Bad Traffic?
![Windows Process](https://github.com/user-attachments/assets/3adb9f8a-f1d8-4ecd-a2e1-be9ca4475620)

**Answer:** `svchost.exe`

---

## Task 9: Phishing Case 3

### What is this analysis classified as?
![Malicious Classification](https://github.com/user-attachments/assets/88daa4af-a29b-40b5-b59a-5829c786f587)

**Answer:** `Malicious activity`

### What is the name of the Excel file?
![Excel File Name](https://github.com/user-attachments/assets/f5a346e2-e600-44b6-ae06-ee06bff7c049)

**Answer:** `CBJ200620039539.xlsx`

### What is the SHA 256 hash for the file?
Open details

![SHA256 Hash](https://github.com/user-attachments/assets/3506d172-9eb5-41c2-b056-3298bf73aba5)

**Answer:** `5F94A66E0CE78D17AFC2DD27FC17B44B3FFC13AC5F42D3AD6A5DCFB36715F3EB`

### What domains are listed as malicious? Defang the URLs & submit answers in alphabetical order. (answer: URL1,URL2,URL3)
![Malicious Domains](https://github.com/user-attachments/assets/a920e8cb-8245-463f-8db3-c2eacf12b3ca)

**Answer:** `biz9holdings[.]com,findresults[.]site,ww38[.]findresults[.]site`

### What IP addresses are listed as malicious? Defang the IP addresses & submit answers from lowest to highest. (answer: IP1,IP2,IP3)
![Malicious IP Addresses](https://github.com/user-attachments/assets/4ab03571-cc71-4f1d-812c-85142b64e652)

**Answer:** `204[.]11[.]56[.]48,103[.]224[.]182[.]251,75[.]2[.]11[.]242`

### What vulnerability does this malicious attachment attempt to exploit?
![Vulnerability Exploit](https://github.com/user-attachments/assets/b7e7fcc9-12a2-414a-9d92-70ad9be8ae09)

**Answer:** `CVE-2017-11882`

---

## Task 10: Conclusion

No Answer Needed

![Task 10 Conclusion](https://github.com/user-attachments/assets/4ac7a1a5-04c4-48f5-a48f-060b87803447)

---

## 🎯 Final Badges
![Case Analysis](https://img.shields.io/badge/Case_Analysis-3_Scenarios-FF69B4?style=for-the-badge)
![Defanging](https://img.shields.io/badge/Defanging-IPs|URLs-000080?style=for-the-badge)
![Room](https://img.shields.io/badge/Room-Phishing_Tools-FF4500?style=for-the-badge)
![Vulnerability](https://img.shields.io/badge/Vulnerability-CVE--2017--11882-008080?style=for-the-badge)

## Conclusion

This room provided comprehensive hands-on experience with essential phishing analysis tools and techniques. Through three detailed case studies, we learned how to:

- **Analyze email headers** to identify suspicious senders and domains
- **Use specialized tools** like PhishTool for email analysis
- **Leverage malware sandboxes** like AnyRun for dynamic analysis
- **Identify malicious indicators** including suspicious IPs, domains, and attachments
- **Defang URLs and IPs** to safely handle malicious indicators
- **Recognize common phishing tactics** and brand impersonation attempts

The practical exercises demonstrated real-world phishing investigation workflows, from initial email analysis to malware examination and indicator extraction. These skills are crucial for SOC analysts and cybersecurity professionals dealing with email-based threats.

---

**Room Link:** [https://tryhackme.com/room/phishingemails3tryoe](https://tryhackme.com/room/phishingemails3tryoe)
