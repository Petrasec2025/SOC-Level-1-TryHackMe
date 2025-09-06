# 🛰️ Cyber Threat Intelligence (CTI) Lab Walkthrough

![Status](https://img.shields.io/badge/Status-Completed-brightgreen)  
![Level](https://img.shields.io/badge/Difficulty-Easy-blue)  
![Platform](https://img.shields.io/badge/Platform-TryHackMe-orange)

---

## 📌 Introduction
This lab introduces **Cyber Threat Intelligence (CTI)** and the frameworks used to share intelligence across organisations.  
As a security analyst, CTI is vital for investigating and reporting adversary attacks with stakeholders and external communities.  

**Learning Objectives:**
- Understand the basics of CTI and its classifications.  
- Explore the CTI lifecycle used during threat investigations.  
- Apply CTI standards and frameworks (MITRE ATT&CK, TAXII, STIX, etc.).  
- Perform practical analysis to build a threat profile.  

---

## 🧪 Task 1 – Introduction
This task covers the fundamentals of CTI and its role in security operations.

📷 Screenshot:  
![Task 1](screenshots/<img width="1338" height="265" alt="Screenshot 2025-09-06 at 5 48 43 PM" src="https://github.com/user-attachments/assets/48208e1f-a91e-415e-a1bf-c4bf3cf54370" />
)

---

## 🧪 Task 2 – Cyber Threat Intelligence

CTI can be defined as **evidence-based knowledge about adversaries**: indicators, tactics, motivations, and actionable advice.  

- **Data**: Discrete indicators (IP addresses, URLs, hashes).  
- **Information**: Combined data answering specific questions.  
- **Intelligence**: Contextual analysis of data + information to reveal adversary patterns.  

📷 Screenshot:  
![Task 2.1](screenshots/<img width="490" height="454" alt="Screenshot 2025-09-06 at 5 46 59 PM" src="https://github.com/user-attachments/assets/ec0633e8-4f77-45da-8e92-3b1975792aa4" />
)

### Threat Intelligence Classifications
1. **Strategic** – High-level intel for business risk decisions.  
2. **Technical** – Artefacts like IPs, hashes, malware samples.  
3. **Tactical** – TTPs (Tactics, Techniques, Procedures).  
4. **Operational** – Adversary motives and intent.  

📷 Screenshot:  
![Task 2.2](screenshots/<img width="595" height="588" alt="Screenshot 2025-09-06 at 5 49 58 PM" src="https://github.com/user-attachments/assets/f33b5c5f-b635-44ac-9f8b-a96bcc22f050" />
)

✅ **Key Questions:**
- What does CTI stand for? → *Cyber Threat Intelligence*  
- IP addresses & hashes fall under which classification? → *Technical Intelligence*  

📷 Screenshot:  
![Task 2.3](screenshots/<img width="710" height="66" alt="Screenshot 2025-09-06 at 5 50 55 PM" src="https://github.com/user-attachments/assets/299f446a-b610-44ab-969e-dd5831dabd6c" />
)

---

## 🧪 Task 3 – CTI Lifecycle

CTI follows a **six-phase cycle**:  

1. **Direction** – Define objectives & scope.  
2. **Collection** – Gather data (internal/external).  
3. **Processing** – Sort, correlate, and format data.  
4. **Analysis** – Extract insights & define action.  
5. **Dissemination** – Share intel with stakeholders.  
6. **Feedback** – Refine based on stakeholder response.  

📷 Screenshot:  
![Task 3.1](screenshots/<img width="980" height="621" alt="Screenshot 2025-09-06 at 5 52 34 PM" src="https://github.com/user-attachments/assets/5d9f41c5-8a98-48e7-a16d-f958e0714f96" />

)

✅ **Key Questions:**
- At which phase is data made usable? → *Processing*  
- When do analysts define investigation questions? → *Direction*  

📷 Screenshot:  
![Task 3.2](screenshots/<img width="720" height="113" alt="Screenshot 2025-09-06 at 5 53 16 PM" src="https://github.com/user-attachments/assets/ea62529b-39f5-4acf-859a-8b3b4e87a6f5" />
)

---

## 🧪 Task 4 – CTI Standards & Frameworks

### 🔹 MITRE ATT&CK
Knowledge base of adversary behavior (TTPs).  
📷 Screenshot:  
![MITRE ATT&CK](screenshots/<img width="690" height="379" alt="Screenshot 2025-09-06 at 5 53 30 PM" src="https://github.com/user-attachments/assets/c0025c25-24ad-4684-b479-cca8de5540d5" />
)

### 🔹 TAXII
Protocol for secure intel sharing.  
- **Collection model** – Request/response.  
- **Channel model** – Publish/subscribe.  

### 🔹 STIX
Standardized language for sharing cyber threat information.  

### 🔹 Cyber Kill Chain (Lockheed Martin)
Stages of an attack: Recon → Weaponization → Delivery → Exploitation → Installation → C2 → Actions on Objectives.  
📷 Screenshot:  
![Kill Chain](screenshots/<img width="990" height="381" alt="Screenshot 2025-09-06 at 5 55 02 PM" src="https://github.com/user-attachments/assets/465cd89e-1677-4c9d-816d-77d46293c934" />
)

### 🔹 Diamond Model
Focus on **Adversary**, **Victim**, **Infrastructure**, and **Capabilities**.  
📷 Screenshot:  
![Diamond Model](screenshots/<img width="823" height="501" alt="Screenshot 2025-09-06 at 5 56 14 PM" src="https://github.com/user-attachments/assets/7a8129ab-b7db-40a5-8f7f-8021886691ed" />
)

✅ **Key Questions:**
- TAXII supports which models? → *Collection and Channel*  
- If adversary is extracting data, kill chain stage? → *Actions on Objectives*  

---

## 🧪 Task 5 – Practical Analysis

In this hands-on section, I built a threat profile using alert logs.  

📷 Screenshot:  
![Task 5](screenshots/<img width="717" height="500" alt="Screenshot 2025-09-06 at 5 56 40 PM" src="https://github.com/user-attachments/assets/856377ad-3eea-4340-b700-82808ee76e40" />
)

### Key Findings:
- **Source email address** → `vipivillain@badbank.com`  
- **Downloaded file** → `flbpfuh.exe`  
- **Extraction IP** → Found in outbound traffic alerts  
- **Threat actor’s email** → `vipivillain@badbank.com`  
- **Software tool used** → `flbpfuh.exe`  
- **Compromised account** → `Administrator`  
- **Victim** → `John Doe`  

📷 Final Flag:  
<img width="322" height="86" alt="Screenshot 2025-09-06 at 6 01 41 PM" src="https://github.com/user-attachments/assets/6dab2f48-e06c-40f4-b5a5-5ed45332f234" />

THM{NOW_I_CAN_CTI}

🎉 Lab Completed Successfully 🎉  

---

## 📝 Conclusion

Through this lab, I strengthened my ability to connect **theory and practice in CTI**.  

**What I Gained:**  
- I now clearly understand the difference between **data, information, and intelligence**.  
- I became more confident with the **CTI lifecycle** and how it applies to SOC workflows.  
- I practiced analyzing real alert logs and mapping them to frameworks like the **Kill Chain, Diamond Model, and MITRE ATT&CK**.  

**Challenges I Faced:**  
- At first, it was tricky to differentiate between **tactical** and **technical intelligence**.  
- Juggling multiple frameworks (STIX, TAXII, ATT&CK, Kill Chain) required me to slow down and organise my notes.  
- During the practical analysis, correlating indicators across alerts took careful attention.  

👉 Overall, this exercise improved my CTI skills and gave me confidence in handling structured threat intelligence investigations.  

---

