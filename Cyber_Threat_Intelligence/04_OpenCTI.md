# 🛰️ OpenCTI TryHackMe Walkthrough  

![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=flat-square) ![Platform](https://img.shields.io/badge/Platform-TryHackMe-blue?style=flat-square&logo=tryhackme) ![Category](https://img.shields.io/badge/Category-Threat%20Intelligence-orange?style=flat-square) ![Tools](https://img.shields.io/badge/Tools-OpenCTI%20|%20MISP%20|%20TheHive-lightgrey?style=flat-square) ![Difficulty](https://img.shields.io/badge/Difficulty-Easy--Medium-yellow?style=flat-square) ![License](https://img.shields.io/badge/License-MIT-purple?style=flat-square)  

---

## Task 1 – Room Overview  

This room will cover the concepts and usage of OpenCTI, an open-source threat intelligence platform. The room will help you understand and answer the following questions:  

- What is OpenCTI and how is it used?  
- How would I navigate through the platform?  
- What functionalities will be important during a security threat analysis?  

**Prerequisites:**  
- MITRE ATT&CK Framework  
- TheHive  
- MISP  
- Threat Intelligence Tools  

![Room Overview](https://github.com/user-attachments/assets/f65119f6-cd76-4b26-8516-ee35f02a32d5)  

---

## Task 2 – Introduction to OpenCTI  

Cyber Threat Intelligence is typically a managerial mystery to handle, with organisations battling with how to input, digest, analyse and present threat data in a way that will make sense. From the rooms linked on the overview, it is clear there are numerous platforms developed to tackle Threat Intelligence.  

**OpenCTI**  
OpenCTI is another open-sourced platform designed to provide organisations with the means to manage CTI through the storage, analysis, visualisation and presentation of threat campaigns, malware, and IOCs.  

**Objective**  
Developed by the collaboration of the French National cybersecurity agency (ANSSI), the platform’s main objective is to create a comprehensive tool that allows users to capitalise on technical and non-technical information while developing relationships between each piece of information and its primary source. OpenCTI can use the MITRE ATT&CK framework to structure data and integrate with tools such as MISP and TheHive.  

![Introduction](https://github.com/user-attachments/assets/f02ad3f5-b549-4ff7-a95b-f529d94417f1)  
![OpenCTI Platform](https://github.com/user-attachments/assets/be5e4510-926a-42bd-9130-e2e9cd121661)  

---

## Task 3 – OpenCTI Data Model  

OpenCTI uses a variety of knowledge schemas in structuring data, the main one being the **Structured Threat Information Expression (STIX2)** standards. STIX is a serialised and standardised language format used in threat intelligence exchange. It allows for the data to be implemented as entities and relationships, effectively tracing the origin of the information.  

![Data Model](https://github.com/user-attachments/assets/16234556-246a-4e2f-b274-1dc0d2d5ba95)  

**Highlight services include:**  
- **GraphQL API:** Connects clients to the database and messaging system.  
- **Write workers:** Python processes to write queries asynchronously from RabbitMQ messaging system.  
- **Connectors:** Python processes used to ingest, enrich, or export data on the platform. Connectors fall under ingestion, enrichment, and export classes.  

![Connectors](https://github.com/user-attachments/assets/750656f5-e48e-445b-a1b0-039d957af05a)  

Refer to the OpenCTI connectors and data model documentation for more details.  

---

## Task 4 – OpenCTI Dashboard 1  

**Login Instructions**  
- URL: Provided in the TryHackMe task (copy and paste into Firefox on AttackBox)  
- Username: `info@tryhack.io`  
- Password: `TryHackMe1234`  

**Steps:**  
1. Start the TryHackMe machine.  
2. Start the AttackBox (fullscreen recommended).  
3. Open Firefox and paste the OpenCTI login URL.  
4. Login using the provided credentials.  

![Start Machine](https://github.com/user-attachments/assets/98603899-9982-42f0-8c80-7fd01fc63a5b)  
![AttackBox](https://github.com/user-attachments/assets/0a640547-8033-4d73-84e6-23313a2a88ee)  
![Login](https://github.com/user-attachments/assets/01eeddd7-2b52-4b6d-843a-12587b81fc6f)  

---

### OpenCTI Dashboard Overview  

The dashboard shows widgets summarising threat data: entities, relationships, reports, and observables ingested within 24 hours.  

**Categories:**  
- **Activities:** Security incidents (reports).  
- **Knowledge:** Tools, victims, threat actors, campaigns.  
- **Analysis:** Reports and external references.  
- **Events:** Malicious activities.  
- **Observations:** Indicators and artefacts.  
- **Threats:** Threat Actors, Intrusion Sets, Campaigns.  
- **Arsenal:** Malware, Attack Patterns, Courses of Action, Tools, Vulnerabilities.  
- **Entities:** Sectors, countries, organisations, individuals.  

![Dashboard](https://github.com/user-attachments/assets/884898df-3fa6-4f79-999d-4fe7989da08c)  
![Activities & Knowledge](https://github.com/user-attachments/assets/7031bb40-ac4a-48ad-bfe0-146db66273d4)  
![Events](https://github.com/user-attachments/assets/d78a59db-16d8-4746-803c-9a415abd1af9)  
![Observations](https://github.com/user-attachments/assets/a130bf7a-90ce-48ca-b37e-fd1541b0857b)  
![Threats](https://github.com/user-attachments/assets/43c5adf2-5c83-44d5-beac-58702ae8870a)  
![Arsenal](https://github.com/user-attachments/assets/5b0cfe7c-2e8a-4923-86d8-cb6fb26c6c9c)  
![Entities](https://github.com/user-attachments/assets/dd8e541a-c628-4004-984a-73d4a080d962)  

**Questions & Answers:**  
- Group using 4H RAT malware: **Putter Panda**  
- Kill-chain phase linked with Command-Line Interface Attack Pattern: **execution-ics**  
- Tab housing Indicators under Activities: **Observations**  

![4H RAT](https://github.com/user-attachments/assets/8fa351bb-e62d-4172-930d-2364740290b3)  

---

## Task 5 – OpenCTI Dashboard 2  

**Navigation Tabs Overview:**  
- **Overview:** General info, entity ID, confidence, relations, reports, external references.  
- **Knowledge:** Linked info: reports, indicators, attack patterns, threats.  
- **Analysis:** Reports where entity observed.  
- **Indicators:** IOC information.  
- **Data:** Exportable files.  
- **History:** Tracks changes made to entity attributes and relations.  

**Questions & Answers:**  
- Intrusion sets associated with Cobalt Strike malware (Good confidence): **CopyKittens, FIN7**  
- Author of the entity: **The MITRE Corporation**  

![Cobalt Strike Knowledge](https://github.com/user-attachments/assets/9e62d88c-789d-422a-9a02-5a3f1197b317)  

---

## 🏁 Conclusion  

Working through this room gave me a **hands-on understanding of OpenCTI** and how it centralizes threat intelligence. I learned to navigate through malware, campaigns, attack patterns, and indicators, exploring relationships between entities and understanding how analysts perform investigations.  

I found the dashboards intuitive and informative, especially when analyzing entities like **Cobalt Strike** and **4H RAT**, and understanding the relationships with threat actors and intrusion sets.  

Overall, this room **strengthened my skills in threat intelligence and investigative analysis**, giving me confidence to use OpenCTI in real-world scenarios. It’s a great starting point for anyone interested in **cyber threat intelligence and SOC workflows**.  


