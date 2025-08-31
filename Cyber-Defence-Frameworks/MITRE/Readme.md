# MITRE Cybersecurity Resources - TryHackMe Writeup

[![TryHackMe](https://img.shields.io/badge/TryHackMe-Cybersecurity-blue)](https://tryhackme.com/room/mitre)
[![MITRE ATT&CK](https://img.shields.io/badge/MITRE-ATT&CK-orange)](https://attack.mitre.org/)
[![CAR Knowledge Base](https://img.shields.io/badge/MITRE-CAR-green)](https://car.mitre.org/)
[![D3FEND](https://img.shields.io/badge/MITRE-D3FEND-red)](https://d3fend.mitre.org/)
[![Engage](https://img.shields.io/badge/MITRE-Engage-lightblue)](https://engage.mitre.org/)

This repository contains my notes and solutions for the **MITRE room** on TryHackMe, covering MITRE ATT&CK, CAR, D3FEND, adversary emulation plans, threat intelligence, and MITRE Engage.

---

## 📚 Table of Contents

- [Introduction](#introduction)  
- [ATT&CK Framework](#attack-framework)  
- [CAR Knowledge Base](#car-knowledge-base)  
- [MITRE Engage](#mitre-engage)  
- [D3FEND](#d3fend)  
- [Adversary Emulation Plans](#adversary-emulation-plans)  
- [Threat Intelligence](#threat-intelligence)  
- [Conclusion](#conclusion)  
- [Author](#author)  

---

## Introduction

The **MITRE room** on TryHackMe explores the resources MITRE provides for the cybersecurity community.  
It highlights frameworks, analytics, and engagement methodologies to simulate, detect, and prevent cyber threats.

🔗 Lab link: [TryHackMe MITRE Room](https://tryhackme.com/room/mitre)  

---

## ATT&CK Framework

- **Users:** Blue Teamers and Red Teamers  
- **Example Technique:** Phishing  
  - **ID:** T1566  
  - **Mitigation:** User Training  
  - **Detection Data Sources:** Application Log, File, Network Traffic  
  - **Groups Using This Technique:** Axiom, Gold SOUTHFIELD  
  - **Associated Groups:** Group 72  
  - **Associated Software:** Hikit  
  - **Software Description:** Hikit is malware used by Axiom for late-stage persistence and exfiltration after the initial compromise.  
  - **Overlapping Group:** Winnti Group  
  - **Number of Techniques:** 15  

**Visual ATT&CK Matrix (Summary):**  
| Tactic          | Technique           | ID    |
|-----------------|------------------|-------|
| Initial Access  | Phishing          | T1566 |
| Execution       | Masquerading      | T1036 |
| Persistence     | C2 Setup          | T1071 |

---

## CAR Knowledge Base

- **CAR-2020-09-001 Pseudocode Representation:** Splunk Search  
- **Tactic with ID TA0003:** Persistence  
- **Zeek (BRO) Script Library:** BZAR  
- **Technique for executables with same hash but different names:** Masquerading  
- **Additional Analyst Information (CAR-2013-05-004):** Unit Tests  

---

## MITRE Engage

- **Prepare ID SAC0002:** Persona Creation  
- **Resource for Engagement Activity:** Persona Profile Worksheet  
- **Activity that provokes adversary response:** Lures  
- **Threat Model Definition:** A risk assessment that models organizational strengths and weaknesses  

---

## D3FEND

- **First ATT&CK Technique in Lookup:** Data Obfuscation  
- **Produces:** Outbound Internet Network Traffic  

---

## Adversary Emulation Plans

- **APT3 Phase 1:** C2 Setup  
- **Persistence:** `sethc.exe` replaced by `cmd.exe`  
- **APT29 Scenario 1 C2 Frameworks:** Pupy, Metasploit Framework  
- **APT29 Scenario 2 C2 Framework:** PoshC2  
- **Sandworm Scenario 1 Webshell:** P.A.S., S0598  

---

## Threat Intelligence

- **APT Group targeting the sector since 2013:** APT33  
- **Cloud Focus:** Cloud Accounts  
- **Associated Tool:** Ruler  
- **Mitigation Method:** Multi-factor Authentication  
- **Affected Platforms:** Azure AD, Google Workspace, IaaS, Office 365, SaaS  

---

## Conclusion

This repository serves as a **detailed write-up** for MITRE TryHackMe exercises, useful for understanding MITRE frameworks, cyber threat emulation, and defensive tactics.

---

## Author

**Petras Guilherme Kulyumba**  
Certified Cybersecurity Professional | Ethical Hacker | CompTIA Security+  
GitHub: [@Petrasec2025](https://github.com/Petrasec2025)  
