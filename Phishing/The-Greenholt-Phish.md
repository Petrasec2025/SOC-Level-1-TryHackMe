# Greenholt Phish Investigation

![SOC Analyst](https://github.com/user-attachments/assets/c69137ae-8401-4205-bd85-5e4bc9a636c0)

*Just another day as a SOC Analyst*

## Case Overview

A Sales Executive at Greenholt PLC received a suspicious email from a customer claiming to be unexpected. The email contained unusual elements including generic greetings, unexpected money transfer references, and an unsolicited attachment.

## Investigation Process

### Email Analysis
![Email Header](https://github.com/user-attachments/assets/f66e5c8b-4873-48e2-97a5-059b16b42683)

### Email Content Examination
![Email Content](https://github.com/user-attachments/assets/d8d37d30-a8a7-40a9-b06a-a8d447eedca5)

## Investigation Findings

### Question 1: Transfer Reference Number
![Transfer Reference](https://github.com/user-attachments/assets/67a4444a-3e2e-415f-9a03-3bef503e8883)
**Answer: 09674321**

### Question 2: Email Sender Name
![Sender Name](https://github.com/user-attachments/assets/e3fefad1-7150-4136-9003-983c95fa82fc)
**Answer: Mr. James Jackson**

### Question 3: Sender Email Address
![Sender Email](https://github.com/user-attachments/assets/4b246d2f-d733-4138-a2dc-111bcf5e42c0)
**Answer: info.mutawamarine@mail.com**

### Question 4: Originating IP Address
![Originating IP](https://github.com/user-attachments/assets/06666460-24fc-4561-b865-4f2bbbebf1bc)
**Answer: 192.119.71.157**

### Question 5: IP Address Owner
![IP Owner](https://github.com/user-attachments/assets/0360b910-3579-43e9-b3b6-355778b10b5e)
**Answer: Hostwinds LLC**

### Question 6: SPF Record
![SPF Record](https://github.com/user-attachments/assets/9d5e27c1-0063-4729-b89c-49605820fae9)
**Answer: v=spf1 include:spf.protection.outlook.com -all**

### Question 7: DMARC Record
![DMARC Record](https://github.com/user-attachments/assets/0083acfc-a82e-4335-9aea-247d27b6ab76)
**Answer: v=DMARC1; p=quarantine; fo=1**

### Question 8: Attachment Name
![Attachment Name](https://github.com/user-attachments/assets/a5f23fda-b492-40d6-a2ee-d89cd544d5c9)
**Answer: SWT_#09674321____PDF__.CAB**

### Question 9: SHA256 Hash
![SHA256 Hash](https://github.com/user-attachments/assets/51ed2514-0270-4f0c-ab39-aaac276ab9c3)
**Answer: 2e91c533615a9bb8929ac4bb76707b2444597ce063d84a4b33525e25074fff3f**

### Question 10: File Size
![File Size](https://github.com/user-attachments/assets/68e3767a-82f5-421e-996e-27609a0a17f3)
**Answer: 400.26 KB**

### Question 11: Actual File Extension
![Actual Extension](https://github.com/user-attachments/assets/4c989408-ce40-4df4-9ea6-b7b5819aa945)
**Answer: RAR**

## Investigation Conclusion

The room has been successfully solved. The most interesting part of this investigation was analyzing the email headers and identifying the true nature of the malicious attachment through hash analysis and file extension examination.

---

## 🔐 Cybersecurity Badges

<div align="center">
  
![SOC Analyst](https://img.shields.io/badge/SOC-Analyst-blue)
![Email Forensics](https://img.shields.io/badge/Email-Forensics-green)
![Threat Hunting](https://img.shields.io/badge/Threat-Hunting-red)
![Malware Analysis](https://img.shields.io/badge/Malware-Analysis-orange)
![Network Security](https://img.shields.io/badge/Network-Security-purple)
![Incident Response](https://img.shields.io/badge/Incident-Response-yellow)
![Digital Forensics](https://img.shields.io/badge/Digital-Forensics-lightgrey)
![Cyber Investigation](https://img.shields.io/badge/Cyber-Investigation-9cf)

</div>

---

## 🎯 Skills Demonstrated

- **Email Header Analysis**
- **SPF/DMARC Record Verification**
- **IP Address Investigation**
- **File Hash Analysis**
- **Malicious Attachment Identification**
- **Threat Intelligence Gathering**
- **Incident Documentation**

---

**"SECURING DIGITAL ASSETS OF LIFE"**

*For more details: [Connect on LinkedIn](https://www.linkedin.com/in/petras-kulyumba-34a786283/)*

---
<div align="center">
  
*🔍 Investigation Completed | ✅ Case Closed | 🛡️ Threat Neutralized*

</div>
