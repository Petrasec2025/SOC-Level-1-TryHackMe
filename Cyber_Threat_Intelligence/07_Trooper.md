# TryHackMe SOC Level 1 Walkthrough: Who’s The Threat? Room (Cyber Threat Intelligence Module)

![Who's The Threat Banner](https://github.com/user-attachments/assets/ae80a199-38a6-4227-a3fd-0a717b7d8669)

---

## 🛡️ Overview

The **Who’s The Threat? Room** is part of the **SOC Level 1 path** on TryHackMe and focuses on identifying **Threat Actors, TTPs (Tactics, Techniques, Procedures), and malware used in attacks**.  

In this room, you take on the role of a **CTI Analyst** investigating **APT X**, also known as **Tropic Trooper**, a sophisticated threat group targeting multinational technology companies.  

Key skills practiced:

- Malware identification and analysis  
- Mapping TTPs to **MITRE ATT&CK framework**  
- Using **OpenCTI** and **ATT&CK Navigator**  
- Cyber Threat Intelligence reporting  

**Room Link:** [TryHackMe Who’s The Threat?](https://tryhackme.com/room/whosthethreat)

---

## ⚙️ Tools Required

- **Virtual Machine**: Start with the green “Start Machine” button. Wait ~7 minutes to load.  
- **Platforms Accessed**:  
  - OpenCTI: `http://MACHINE_IP:8080`  
  - MITRE ATT&CK Navigator: `http://MACHINE_IP:4200`  

---

## 🎯 Task Walkthrough & Answers

### 1. Kind of phishing campaign used by APT X
**Answer:** spear-phishing emails  

---

### 2. Malware used by APT X
**Answer:** USBferry  

---

### 3. Malware’s STIX ID
**Answer:** malware — 5d0ea014–1ce9–5d5c-bcc7-f625a07907d0  

---

### 4. USB-based initial access technique
**Answer:** Replication Through Removable Media (T1071.001)  

---

### 5. Identity of APT X
**Answer:** Tropic Trooper  

---

### 6. Number of Attack Pattern techniques associated with the APT
**Answer:** 39  

---

### 7. Tool linked to the APT
**Answer:** BITSAdmin  

---

### 8. Sub-technique under Valid Accounts
**Answer:** Local Accounts  

---

### 9. Tactics the above technique falls under
**Answer:** Initial Access, Persistence, Defense Evasion, Privilege Escalation  

---

### 10. Technique under Collection tactic
**Answer:** Automated Collection  

---

## 📌 Key Takeaways

This room helps understand **real-world cyber threat intelligence workflows**:

- Using reports and CTI platforms to **identify threat actors**.  
- Mapping **TTPs to MITRE ATT&CK techniques**.  
- Analyzing malware **USBferry** for targeting **air-gapped networks**.  
- Understanding **defensive measures**, including:  
  - Spear-phishing awareness and training  
  - USB device control and endpoint protection  
  - Multi-factor authentication (MFA)  
  - Network monitoring and EDR  
  - Incident response planning  

This challenge reinforces the importance of **understanding attackers’ mindsets** to develop effective defenses.

---

## 🔗 Additional Resources

- [OpenCTI](https://www.opencti.io/)  
- [MITRE ATT&CK Framework](https://attack.mitre.org/)  
- [TrendMicro Tropic Trooper Report, May 2020](https://www.trendmicro.com/)  

---

## 📛 Badges

![TryHackMe](https://img.shields.io/badge/TryHackMe-SOC%20Level%201-blue) ![Cyber Threat Intelligence](https://img.shields.io/badge/Module-Cyber%20Threat%20Intelligence-green) ![Who's The Threat? Room](https://img.shields.io/badge/Room-Who's%20The%20Threat-red)

---

## 📝 Conclusion

The **Who’s The Threat? Room** provides a hands-on experience in **CTI analysis**, showcasing how to identify sophisticated threat actors like **Tropic Trooper**, map their **TTPs**, and understand the techniques they use to compromise networks.  

By combining **OpenCTI, MITRE ATT&CK, and real-world reporting**, learners develop the ability to **analyze threats, track malware, and recommend mitigation strategies**—skills essential for SOC analysts and cybersecurity professionals.  

Cybersecurity is about **anticipating attackers’ moves** and building resilient defenses, and this room is an excellent step toward mastering that mindset.

![SOC Level 1](https://github.com/user-attachments/assets/7c937f2c-5234-4059-a187-83519905f748)



