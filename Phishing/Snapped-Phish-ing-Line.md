# Snapped Phish(ing) Line Investigation

![Investigation Disclaimer](https://github.com/user-attachments/assets/a53a8b73-92b0-4c95-a1b3-65b22eaaf828)

## ⚠️ Disclaimer

Based on real-world occurrences and past analysis, this scenario presents a narrative with invented names, characters, and events.

Please note: The phishing kit used in this scenario was retrieved from a real-world phishing campaign. Hence, it is advised that interaction with the phishing artefacts be done only inside the attached VM, as it is an isolated environment.

![Scenario Introduction](https://github.com/user-attachments/assets/9a7d2327-9886-4e5d-9e48-cda3aa444cf5)

## 📖 An Ordinary Midsummer Day...

As an IT department personnel of SwiftSpend Financial, one of your responsibilities is to support your fellow employees with their technical concerns. While everything seemed ordinary and mundane, this gradually changed when several employees from various departments started reporting an unusual email they had received. Unfortunately, some had already submitted their credentials and could no longer log in.

## 🔍 Investigation Approach

You now proceeded to investigate what is going on by:

- Analysing the email samples provided by your colleagues.
- Analysing the phishing URL(s) by browsing it using Firefox.
- Retrieving the phishing kit used by the adversary.
- Using CTI-related tooling to gather more information about the adversary.
- Analysing the phishing kit to gather more information about the adversary.

![VM Connection](https://github.com/user-attachments/assets/3fc743af-e9b9-4e38-88dd-491b1a2a9cd6)

## 🔗 Connecting to the Machine

Start the virtual machine in split-screen view by clicking the green Start Machine button on the upper right section of this task. If the VM is not visible, use the blue Show Split View button at the top-right of the page. Alternatively, using the credentials below, you can connect to the VM via RDP.

**Note:** The phishing emails to be analysed are under the phish-emails directory on the Desktop. Usage of a web browser, text editor and some knowledge of the grep command will help.

## 📧 Email Analysis Findings

![Email Analysis](https://github.com/user-attachments/assets/211d9d42-40d2-41fc-90b7-67a0a5a74db1)

### **Q. Who is the individual who received an email attachment containing a PDF?**
**Answer: `William McClean`**

### **Q. What email address was used by the adversary to send the phishing emails?**
**Answer: `Accounts.Payable@groupmarketingonline.icu`**

## 🔗 URL Investigation

### **Q. What is the redirection URL to the phishing page for the individual Zoe Duncan? (defanged format)**

**Step 1** — Download HTML file attachment from Zoe Duncan's email

**Step 2** — 
![URL Extraction](https://github.com/user-attachments/assets/b97b46ee-6ef9-4982-8306-02b8cf2fdef9)

Copy the first URL & use Cyberchef's defang URL filter —
![URL Defanging](https://github.com/user-attachments/assets/02bfa5f2-8935-458a-b755-af92504a8d7b)

## 🌐 Phishing Kit Discovery

### **Q. What is the URL to the .zip archive of the phishing kit? (defanged format)**

**Hint** — enumerate the URL

Visiting:
- http://kennaroads.buzz/data/Update365/ 
- http://kennaroads.buzz/data/

![Directory Enumeration](https://github.com/user-attachments/assets/50272957-3403-496d-b542-1ec6ea88cb60)

![Phishing Kit Files](https://github.com/user-attachments/assets/4826f5d8-1b57-491a-8a6d-3368416eab58)

![File Discovery](https://github.com/user-attachments/assets/74205bb4-d8f7-4903-bd53-c8dfb8bca533)

**Findings:**
- Files: log.txt, Update365.zip

### **Q. What is the SHA256 hash of the phishing kit archive?**
![Hash Calculation](https://github.com/user-attachments/assets/24527157-9635-4a48-9498-567e34431025)

## 📊 Threat Intelligence Analysis

### **Q. When was the phishing kit archive first submitted? (format: YYYY-MM-DD HH:MM:SS UTC)**

**Step 1** — Visit the VirusTotal site

**Step 2** — Search for the SHA256 hash of the phishing kit archive

![VirusTotal Analysis](https://github.com/user-attachments/assets/e2c25543-c4e4-4c14-9c75-069052be23ab)

### **Q. When was the phishing domain that was used to host the phishing kit archive first registered? (format: YYYY-MM-DD)**

**Step 1** — Since the website that the victims of the phishing attack visited kennarods.buzz search for kennarods.buzz on ThreatBook CTI

![ThreatBook Analysis](https://github.com/user-attachments/assets/43828c7b-f4d7-45a0-8716-5b35ffba56b8)

## 📝 Log File Analysis

### **Q. What was the email address of the user who submitted their password twice?**

Analyzing log.txt
![Log Analysis](https://github.com/user-attachments/assets/e61f52d5-cd73-441f-9584-f13b723e6047)

## 🔐 Credential Collection Analysis

### **Q. What was the email address used by the adversary to collect compromised credentials?**

After analyzing submit.php.

![Submit.php Analysis](https://github.com/user-attachments/assets/e60dd4af-ddb7-4401-923e-39acab7ba07e)

### **Q. The adversary used other email addresses in the obtained phishing kit. What is the email address that ends in "@gmail.com"?**
![Additional Email Discovery](https://github.com/user-attachments/assets/9beb591a-378a-46c3-be10-bb4345294406)

## 🚩 Hidden Flag Discovery

### **Q. What is the hidden flag?**

**Question Hint**
The flag contains a ".txt" extension and, with some adjustments, should be downloadable from the phishing URL. Look for the flag in every subdomain/directory of the phishing URL.

![Flag Discovery Process](https://github.com/user-attachments/assets/e12bbfd1-a15b-425f-b854-a52a6f760f48)

![Final Flag](https://github.com/user-attachments/assets/c206f4a6-67fe-4dec-844a-94989aaf514b)

## 🎯 Investigation Conclusion

This room helps one to understand the process of analyzing phishing emails and phishing kits through log file analysis and OSINT techniques and platforms such as VirusTotal and ThreatBook CTI. Ending with some source code review to capture the adversary's email address.

---

## 🔐 Cybersecurity Badges

<div align="center">
  
![Phishing Analysis](https://img.shields.io/badge/Phishing-Analysis-red)
![Email Forensics](https://img.shields.io/badge/Email-Forensics-green)
![Threat Intelligence](https://img.shields.io/badge/Threat-Intelligence-blue)
![Malware Analysis](https://img.shields.io/badge/Malware-Analysis-orange)
![OSINT](https://img.shields.io/badge/OSINT-Investigation-purple)
![Incident Response](https://img.shields.io/badge/Incident-Response-yellow)
![Log Analysis](https://img.shields.io/badge/Log-Analysis-lightgrey)
![Cyber Investigation](https://img.shields.io/badge/Cyber-Investigation-9cf)

</div>

---

## 🛡️ Skills Demonstrated

- **Phishing Email Analysis**
- **URL Investigation & Defanging**
- **Phishing Kit Retrieval**
- **VirusTotal Analysis**
- **ThreatBook CTI Research**
- **Log File Forensics**
- **Source Code Review**
- **Credential Theft Analysis**
- **Domain Registration Research**

---

<div align="center">

**🔍 Investigation Completed** | **✅ Case Closed** | **🛡️ Threat Contained**

*This investigation provided comprehensive insights into modern phishing campaign analysis and adversary tracking techniques.*

</div>






