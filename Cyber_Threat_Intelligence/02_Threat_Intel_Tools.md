# 🔍 OSINT Threat Intelligence Lab

![Status](https://img.shields.io/badge/Status-Completed-brightgreen) ![Level](https://img.shields.io/badge/Difficulty-Easy-blue) ![Platform](https://img.shields.io/badge/Platform-TryHackMe-orange)

---

## 📌 Introduction

Explore different OSINT tools used to conduct security threat assessments and investigations.

---

## 🧪 Task 1 – Room Outline

This room will cover the concepts of Threat Intelligence and various open-source tools that are useful.  

**Learning Objectives:**
- Understanding the basics of threat intelligence & its classifications.  
- Using **UrlScan.io** to scan for malicious URLs.  
- Using **Abuse.ch** to track malware and botnet indicators.  
- Investigate phishing emails using **PhishTool**.  
- Using **Cisco Talos Intelligence** platform for intel gathering.  

📷 Screenshot:  
![Task 1 Room Outline](<img width="1368" height="268" alt="Screenshot 2025-09-06 at 6 39 25 PM" src="https://github.com/user-attachments/assets/29613afe-1d0f-4629-9fb8-74d632cc448a" />)

---

## 🧪 Task 2 – Threat Intelligence

Threat Intelligence is the analysis of data and information using tools and techniques to generate meaningful patterns on how to mitigate against potential risks associated with existing or emerging threats targeting organisations, industries, sectors, or governments.

**To mitigate risks, we can ask:**
- Who’s attacking you?  
- What’s their motivation?  
- What are their capabilities?  
- What artefacts and indicators of compromise should you look out for?  

### Threat Intelligence Classifications
Threat Intel is geared towards understanding the relationship between your operational environment and your adversary.  

- **Strategic Intel:** High-level intel that looks into the organisation’s threat landscape and maps out risk areas based on trends, patterns, and emerging threats that may impact business decisions.  
- **Technical Intel:** Looks into evidence and artefacts of attack used by an adversary. Incident Response teams can use this intel to create a baseline attack surface to analyse and develop defence mechanisms.  
- **Tactical Intel:** Assesses adversaries’ tactics, techniques, and procedures (TTPs). This intel can strengthen security controls and address vulnerabilities through real-time investigations.  
- **Operational Intel:** Looks into an adversary’s specific motives and intent to perform an attack. Security teams may use this intel to understand the critical assets available in the organisation (people, processes, and technologies) that may be targeted.  

📷 Screenshot:  
![Threat Intel Classifications](<img width="552" height="556" alt="Screenshot 2025-09-06 at 6 42 31 PM" src="https://github.com/user-attachments/assets/319ee461-0c14-4342-82a3-90a5fdb8855d" />)

---

## 🧪 Task 3 – UrlScan.io

Urlscan.io is a free service developed to assist in scanning and analysing websites. It automates browsing and crawling to record activities and interactions.  

📷 Screenshots:  
![UrlScan Interface](<img width="785" height="581" alt="Screenshot 2025-09-06 at 6 43 23 PM" src="https://github.com/user-attachments/assets/dbb7af8e-91b0-4c0b-87ee-9747a51e4b81" />)  
![UrlScan Scan Results](<img width="772" height="627" alt="Screenshot 2025-09-06 at 6 43 16 PM" src="https://github.com/user-attachments/assets/4e11f07f-b864-40f9-9e23-d3a3ea6e5ed7" />)

### Scan Results
URL scan results provide information in the following key areas:  

- **Summary:** General info about the URL, including IP, domain registration, page history, and a screenshot of the site.  
- **HTTP:** HTTP connections made by the scanner, including fetched data and file types.  
- **Redirects:** Any detected HTTP or client-side redirects.  
- **Links:** Outgoing links from the homepage.  
- **Behaviour:** Variables and cookies detected; helps identify frameworks used.  
- **Indicators:** IPs, domains, and hashes associated with the site (do not imply malicious activity).  

📷 Screenshot:  
![UrlScan Key Areas](<img width="1360" height="763" alt="Screenshot 2025-09-06 at 6 44 18 PM" src="https://github.com/user-attachments/assets/a0e656f2-be69-4b9f-9bde-cb0993c9d743" />)

**Note:** Data can vary day to day due to dynamic internet activity.

---

## 🧪 Scenario – Scan TryHackMe Domain

You have been tasked to perform a scan on TryHackMe's domain. The results are displayed below.  

📷 Screenshot:  
![TryHackMe Scan](<img width="1346" height="750" alt="Screenshot 2025-09-06 at 6 57 28 PM" src="https://github.com/user-attachments/assets/45bc35e5-17e2-405a-96d0-3004be8d58b1" />)

**Information Recorded:**  
- Domains & IP addresses contacted  
- Resources requested from domains  
- Web page snapshot  
- Technologies used  
- Metadata  

**Views:**  
- **Most Recent Scans** – historical results  
- **Current Live Scans** – live results

---

## 🧪 Questions

> *Answers are in the screenshots. Follow along to locate them yourself.*

1. **What is TryHackMe’s Cisco Umbrella Rank?**  
📷 Screenshot:  
![Cisco Umbrella Rank](<img width="531" height="143" alt="Screenshot 2025-09-06 at 6 46 31 PM" src="https://github.com/user-attachments/assets/d7c8fac4-8cdf-4eef-9002-ebacd190e4ec" />)

2. **How many domains did UrlScan.io identify?**  
📷 Screenshot:  
![Domains Identified](<img width="628" height="155" alt="Screenshot 2025-09-06 at 6 46 36 PM" src="https://github.com/user-attachments/assets/b5f6e045-0418-4fbb-a7b6-4a61054003d3" />)

3. **What is the main domain registrar listed?**  
📷 Screenshot:  
![Domain Registrar](<img width="496" height="116" alt="Screenshot 2025-09-06 at 6 46 41 PM" src="https://github.com/user-attachments/assets/dd13ace6-7372-4aa3-9a40-df0e1b6e5823" />)

4. **What is the main IP address identified?**  
📷 Screenshot:  
![Main IP Address](<img width="540" height="143" alt="Screenshot 2025-09-06 at 6 46 47 PM" src="https://github.com/user-attachments/assets/d4f92729-53e0-478a-bb08-efc6e51b52a8" />)

---

## 📝 Conclusion

Working through this room was both informative and engaging.  

- I learned how to use **UrlScan.io** to gather detailed information about domains and websites, including IP addresses, domain registration, and technologies in use.  
- The exercises helped me understand how to classify **threat intelligence** into strategic, technical, tactical, and operational categories.  
- By following the screenshots and analyzing the outputs, I became more confident in identifying key indicators and metadata from a target domain.  
- Overall, the room reinforced my skills in **OSINT-based threat intelligence** and gave me hands-on experience that I can directly apply in real-world investigations.  

I found the room easy to follow, and it clearly demonstrated the importance of structured OSINT workflows in cybersecurity.
