# 🛡️ YARA Rule Mastery - TryHackMe Room Guide

![YARA Logo](https://github.com/user-attachments/assets/1009ff9b-a571-4a8e-8e01-54cc74d2ce6b)

![Platform](https://img.shields.io/badge/Platform-TryHackMe-blue?logo=tryhackme&logoColor=white) ![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-success?style=flat&logo=hackthebox) ![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=flat) ![Tools](https://img.shields.io/badge/Tools-YARA%20%7C%20LOKI%20%7C%20yarGen%20%7C%20Valhalla-orange?style=flat&logo=virustotal) ![License](https://img.shields.io/badge/License-MIT-lightgrey?style=flat)

---

## 📖 Overview
This guide covers the TryHackMe **YARA** room, which teaches pattern matching with YARA rules for malware detection.  

**YARA** (Yet Another Ridiculous Acronym) is a powerful tool developed by **Victor M. Alvarez** and **VirusTotal** for identifying malware based on binary and textual patterns.

---

## 🎯 Key Learning Objectives
- Understand **YARA rule syntax** and structure  
- Create **basic to advanced YARA rules**  
- Use YARA with tools like **LOKI** and **yarGen**  
- Analyze suspicious files with **YARA rules**  
- Leverage threat intelligence platforms like **Valhalla**

---

## 📝 Room Tasks & Solutions

### 🔹 Task 2: What is Yara?
- **2.1** Base-16 numbering system Yara can detect → `hexadecimal`  
- **2.2** Would `"Enter your Name"` be a string in an application? → `Yay`

---

### 🔹 Task 8: Using LOKI and its Yara rule set
- **8.1** File 1 detection → `suspicious`  
- **8.2** Yara rule matched → `webshell_metaslsoft`  
- **8.3** Classification → `Web shell`  
- **8.4** Matched string → `str1`  
- **8.5** Hack tool name/version → `b374k 2.2`  
- **8.6** Number of strings flagged → `1`  
- **8.7** File 2 detection → `benign`  
- **8.8** Web shell name/version → `b374k 3.2.3`

---

### 🔹 Task 9: Creating Yara rules with yarGen
- **9.1** Command → `yara file2.yar file2/1ndex.php`  
- **9.2** Did Yara flag file 2? → `Yay`  
- **9.3** Copy Yara rule → *(no answer needed)*  
- **9.4** Did Loki flag file 2 with new rule? → `Yay`  
- **9.5** Variable name → `Zepto`  
- **9.6** Number of strings → `20`  
- **9.7** File size limit → `700KB`

---

### 🔹 Task 10: Valhalla
- **10.1** File 1 attributed to APT group? → `Yay`  
- **10.2** First Yara rule for file 2 → `Webshell_b374k_rule1`  
- **10.3** Scanner provider → `THOR APT Scanner`  
- **10.4** Every AV detected file 2? → `Nay`  
- **10.5** Another extension besides `.PHP` → `.EXE`  
- **10.6** JavaScript library used → `Zepto`  
- **10.7** Is this rule in Loki’s default Yara file? → `Nay`

---

## 🛠️ Tools Covered
- **[YARA](https://github.com/VirusTotal/yara)** → Pattern matching tool for malware identification  
- **[LOKI](https://github.com/Neo23x0/Loki)** → IOC scanner with YARA capabilities  
- **[yarGen](https://github.com/Neo23x0/yarGen)** → YARA rule generator from malware samples  
- **[Valhalla](https://valhalla.nextron-systems.com/)** → Online YARA rule repository  

---

## 📌 Key Concepts
- YARA rules have three main parts: **meta**, **strings**, and **conditions**  
- Detects **hexadecimal patterns**, **strings**, and **file characteristics**  
- Combine conditions with logical operators (`and`, `or`, `not`)  
- File size constraints + multiple string matching improve accuracy  

---

## ✅ Conclusion
This TryHackMe room provides **hands-on practice** with YARA rule creation, testing, and implementation. By working with real malware samples and security tools, you’ll build practical **threat hunting** and **malware detection** skills using pattern matching techniques.

---

## 📚 Additional Resources
- [🔗 YARA GitHub Repository](https://github.com/VirusTotal/yara)  
- [🔗 Valhalla YARA Rules](https://valhalla.nextron-systems.com/)  
- [🔗 LOKI Scanner](https://github.com/Neo23x0/Loki)  
- [🔗 yarGen Rule Generator](https://github.com/Neo23x0/yarGen)  

---

⚠️ **Note:** Always analyze malware samples in **isolated environments** and follow proper **security protocols**.  

