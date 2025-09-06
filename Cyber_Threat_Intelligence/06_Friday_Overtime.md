# TryHackMe SOC Level 1 Walkthrough: Friday Overtime Room (Cyber Threat Intelligence Module)

![Friday Overtime Banner](https://github.com/user-attachments/assets/4e549e49-7163-40a4-b289-77d4754f927a)

---

## 🛡️ Overview

This walkthrough covers the **Friday Overtime Room** from **TryHackMe’s SOC Level 1 path**, part of the **Cyber Threat Intelligence module**.  
In this room, you take on the role of a **CTI Analyst** at PandaProbe Intelligence and investigate **malware artefacts** reported by **SwiftSpend Finance**, a financial company.  

The exercise focuses on **analyzing malware samples, extracting hashes, identifying malware frameworks, and linking findings to MITRE ATT&CK techniques** in a secure, isolated virtual environment.

**Room Link:** [TryHackMe Friday Overtime Room](https://tryhackme.com/room/fridayovertime)

---

## 🎯 Scenario

It’s a **Friday evening**, and while most are heading home, you are tasked with analyzing **malware samples** sent by SwiftSpend Finance. The scenario emphasizes:

- Downloading malware samples in a **secure VM environment**.
- Running automated and **manual malware analysis**.
- Correlating findings with **global threat intelligence databases**.
- Reporting **mitigation and recovery steps**.

**VM Access:** Start the virtual machine in split-screen mode via the **Start Machine** button.  
**DocIntel Platform Credentials:**

- Username: Analyst@THM.thm  
- Password: Analyst12345&

---

## ⚙️ Task Walkthrough & Answers

### 1. Who shared the malware samples?
**Answer:** Oliver Bennett  

---

### 2. SHA1 hash of `pRsm.dll` in `samples.zip`
- Password to unzip: `Panda321!`  
**Answer:** 9d1ecbbe8637fed0d89fca1af35ea821277ad2e8  

---

### 3. Malware framework utilizing these DLLs
**Answer:** MgBot  

---

### 4. MITRE ATT&CK Technique linked to `pRsm.dll`
**Answer:** T1123  

---

### 5. CyberChef defanged URL of the malicious download (first seen 2020-11-02)
**Answer:** hxxp[://]update[.]browser[.]qq[.]com/qmbs/QQ/QQUrlMgr_QQ88_4296[.]exe  

---

### 6. CyberChef defanged IP of the C&C server (first detected 2020-09-14)
**Answer:** 122[.]10[.]90[.]12  

---

### 7. SHA1 hash of SpyAgent spyware targeting Android (Nov 16, 2022)
**Answer:** 1c1fe906e822012f6235fcc53f601d006d15d7be  

---

## ✅ Room Conclusion

This room provided a **realistic simulation** of a **CTI analyst’s workflow** in responding to a malware alert. You learned:

- How to **securely download and analyze malware samples**.
- Extracting and computing **hashes** for malware artefacts.
- Linking malware to **specific frameworks** like MgBot.
- Mapping findings to **MITRE ATT&CK techniques**.
- Using **CyberChef** for URL and IP defanging.
- Correlating malware intelligence with **global databases** for proactive defense.

This practical approach reinforces the **importance of CTI platforms** and hands-on **malware analysis in financial security**.

---

## 🔗 Additional Resources

- [VirusTotal](https://www.virustotal.com/)
- [ESET Blog on Evasive Panda APT Group](https://www.welivesecurity.com/2023/04/26/evasive-panda-apt-group-malware-updates-popular-chinese-software/)
- [MITRE ATT&CK Framework](https://attack.mitre.org/)

---

## 📛 Badges

![TryHackMe](https://img.shields.io/badge/TryHackMe-SOC%20Level%201-blue) ![Cyber Threat Intelligence](https://img.shields.io/badge/Module-Cyber%20Threat%20Intelligence-green) ![Friday Overtime Room](https://img.shields.io/badge/Room-Friday%20Overtime-red)

---

