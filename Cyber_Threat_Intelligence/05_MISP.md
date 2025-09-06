# TryHackMe SOC Level 1 Walkthrough: MISP (Cyber Threat Intelligence Module)

![MISP Banner](https://github.com/user-attachments/assets/b21acee7-2e7b-481e-b347-ce5f1279110c)

---

## 🛡️ Overview

This is the **eleventh installment** in my walkthrough series on **TryHackMe’s SOC Level 1 path**, covering the **fifth and final room** in the **Cyber Threat Intelligence module**.  
We explore **MISP (Malware Information Sharing Platform)**, a platform designed to **identify, share, and use threat intelligence** to mitigate potential adversary actions.

**Room Link:** [TryHackMe MISP Room](https://tryhackme.com/room/misp)

---

## 🎯 Room Objectives

This room focuses on:

- Introduction to MISP and its development.
- Use cases for MISP.
- Core features and terminologies.
- Dashboard navigation.
- Event creation and management.
- Feeds and taxonomies.

**Prerequisites:** Familiarity with security concepts. Check out the **Pre-Security Path** and **Jr. Security Analyst Room**.

---

## ⚙️ Task 1: MISP Introduction

### What is MISP?
MISP is an **open-source threat intelligence platform** that helps **collect, store, and share threat information and IOCs** among trusted members.  
It supports **distributed information sharing** across **closed, semi-private, and open communities** and can integrate with **NIDS, SIEM, and log analysis tools**.

**Use Cases:**

- Malware reverse engineering
- Security investigations
- Intelligence analysis
- Law enforcement support
- Risk analysis
- Fraud detection

### Core Functionalities

- **IOC Database:** Store technical/non-technical threat data.
- **Automatic Correlation:** Detect relationships between attributes and indicators.
- **Data Sharing:** Share information within and across MISP instances.
- **Import & Export:** Integrate events with other systems (e.g., NIDS, HIDS, OpenIOC).
- **Event Graph:** Visualize relationships between objects and attributes.
- **API Support:** Integration with other systems for fetching/exporting events.

---

## 📝 Key Terminologies

| Term               | Description                                                                 |
|-------------------|-----------------------------------------------------------------------------|
| Events             | Collection of contextually linked information.                               |
| Attributes         | Individual data points related to an event.                                  |
| Objects            | Custom attribute compositions.                                               |
| Object References  | Relationships between different objects.                                     |
| Sightings          | Time-specific occurrences of an attribute for credibility.                  |
| Tags               | Labels attached to events/attributes.                                        |
| Taxonomies         | Classification libraries to tag, classify, and organize information.        |
| Galaxies           | Knowledge base items used to label events/attributes.                       |
| Indicators         | Information pieces detecting suspicious/malicious activity.                |

---

## 🖥️ Task 2: Using the MISP System

**Login Credentials:**  

Username: Analyst@THM.thm

Password: Analyst12345&
---

**Dashboard Features:**

- **Home:** Return to the main page.  
- **Event Actions:** Create, modify, delete, search, and list events/attributes.  
- **Dashboard:** Custom dashboards with widgets.  
- **Galaxies:** Shortcut to the MISP Galaxies.  
- **Input Filters:** Validation, replacement, and blocklists for data entry.  
- **Global Actions:** Profile, manual, news, organisation contributions.  

**Adding Attributes:**  
Attributes can be **added manually** or imported using **OpenIOC/ThreatConnect**.  

![Add Attribute Example](https://github.com/user-attachments/assets/19360891-e33a-476f-9d31-3b07aec867f4)  

**Adding Files:**  
Files can be added to events for analysis. Check **Malware** for malware files.

![Add File Example](https://github.com/user-attachments/assets/a0444d24-7292-4816-8a6b-397eb24a8dc9)

**Publishing Events:**  
Only an **organisation admin** can publish events to distribution channels.

---

## 📌 Task 3: Questions

**3a. How many distribution options does MISP provide?**  
Answer: **4**

**3b. Who can publish events?**  
Answer: **Organisation admin**

---

## 📡 Task 4: Feeds & Taxonomies

**Feeds:**  
Continuous sources of indicators for proactive threat defense. Managed by the **Site Admin**.

**Taxonomies:**  
Classify events, indicators, and threat actors using **tags**.  

**Tagging Best Practices:**  

- Tag **events** generally; tag **attributes** only for exceptions.  
- **Minimal subset of tags:**  
  - Traffic Light Protocol (TLP)  
  - Confidence  
  - Origin  
  - Permissible Actions Protocol  

![Feeds & Taxonomies](https://github.com/user-attachments/assets/d2dffb10-c245-4e78-80ad-ead9e6021a0f)

---

## 🔍 Task 5: Scenario Event

Investigate a **PupyRAT** event and correlate with your SIEM.

- **5a. Event ID:** 1145  
- **5b. Adversary gains:** remote access  
- **5c. C2 Server IP:** 89.107.62.39  
- **5d. Attack group:** magic hound  
- **5e. Taxonomy tag with 50% certainty:** osint  

![Scenario Event](https://github.com/user-attachments/assets/57581ddc-a728-43fc-b49d-54737300ccc7)

---
## ✅ Task 6: Conclusion

This room on **MISP (Malware Information Sharing Platform)** provided a practical walkthrough of **how threat intelligence is shared and managed** in real-world scenarios. It introduced analysts to the platform’s **dashboard, events, attributes, feeds, taxonomies, and tagging system**, highlighting its use in **incident reporting, malware analysis, and threat correlation**.

You have now learned:

- MISP’s purpose in sharing malware and threat information.
- How to create, tag, and publish events.
- How to use feeds and taxonomies for threat intelligence.
- Best practices for managing threat information within an organization.

**Additional Resources:**

- [MISP Book](https://www.circl.lu/doc/misp/)
- [MISP GitHub](https://github.com/MISP/MISP)
- [CIRCL MISP Training Module 1](https://www.circl.lu/doc/misp/)
- [CIRCL MISP Training Module 2](https://www.circl.lu/doc/misp/)
---

## 🔗 Next Steps

The next module will cover **Network Security & Traffic Analysis**, starting with **Traffic Analysis Essentials** and **Snort**.

---

## 📛 Badges

![TryHackMe](https://img.shields.io/badge/TryHackMe-SOC%20Level%201-blue) ![Cyber Threat Intelligence](https://img.shields.io/badge/Module-Cyber%20Threat%20Intelligence-green) ![MISP](https://img.shields.io/badge/Tool-MISP-red)

---

