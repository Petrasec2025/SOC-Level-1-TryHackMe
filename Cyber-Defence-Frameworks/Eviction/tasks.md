# TryHackMe — Eviction (SOC Level 1: Cyber Defence Frameworks)

![Eviction Banner](https://github.com/user-attachments/assets/6bd5a96b-6d59-4616-90e9-26dd62c9c050)

**Room Link:** [Eviction on TryHackMe](https://tryhackme.com/room/eviction)  
**MITRE ATT&CK Navigator:** [Eviction Layer](https://static-labs.tryhackme.cloud/sites/eviction/)

---

## Overview

Sunny is a SOC analyst at **E-corp**, which manufactures rare earth metals. She receives a classified intelligence report indicating that **APT28** may target organizations like E-corp. Sunny must use the **MITRE ATT&CK Navigator** to:

- Identify TTPs used by APT28  
- Ensure the network has not been compromised  
- Stop the APT if it has intruded  

![Task 1](https://github.com/user-attachments/assets/e2f9e177-cafd-41cf-84f4-e062b57058f3)

---

## Task 1: Understand the Adversary

### Q1: Technique used by APT for recon and initial access

APT28 often uses **Spearphishing Attachments** to gather intelligence and gain initial access simultaneously.  

**Answer:** `Spearphishing Link`

![Spearphishing Technique](https://github.com/user-attachments/assets/1729c776-6f85-4da1-ad49-0fdb2554a0d0)

---

### Q2: Accounts the APT might compromise

APT28 targets accounts while developing resources via spearphishing.  

**Answer:** `Email Account`

![Email Account Compromise](https://github.com/user-attachments/assets/3da58cbd-50ce-48d7-88f1-6214886e63d5)

---

### Q3: User execution techniques

APT28 may trick users into executing code. Sunny should monitor:

**Answer:** `Malicious File and Malicious Link`

![Malicious File Execution](https://github.com/user-attachments/assets/917f4cd9-afd8-411f-8ea2-d975518dfeda)  
![Malicious Link Execution](https://github.com/user-attachments/assets/dc36811c-25c4-405a-8713-530d00ead0c8)

---

### Q4: Scripting interpreters for execution

Sunny should search for these interpreters if malicious execution occurs:

**Answer:** `PowerShell and Windows Command Shell`

![PowerShell Execution](https://github.com/user-attachments/assets/de550d42-d9df-408d-a696-020736aad0bf)  
![Windows Command Shell Execution](https://github.com/user-attachments/assets/3b51a60c-f31e-43b4-b112-9fc6a5ee1112)

---

### Q5: Registry keys for persistence

APT28 may modify registry keys to maintain persistence. Sunny should observe:

**Answer:** `Registry Run Keys`

![Registry Run Keys](https://github.com/user-attachments/assets/b7af563c-5de7-48b0-87bd-2f13821e1908)

---

### Q6: System binary for proxy execution

APT28 uses system binaries to evade defenses. Sunny should monitor:

**Answer:** `Rundll32`

![Rundll32 Proxy Execution](https://github.com/user-attachments/assets/b580dcbc-a055-4a4a-9905-6e1830306d08)

---

### Q7: Discovery technique using tcpdump

Presence of `tcpdump` indicates network traffic monitoring.  

**Answer:** `Network Sniffing`

![Network Sniffing](https://github.com/user-attachments/assets/0cafed5d-a336-46ac-b613-df671fe34f74)

---

### Q8: Remote services for lateral movement

APT28 may exploit these for lateral movement:

**Answer:** `SMB/Windows Admin Shares`

![SMB Lateral Movement](https://github.com/user-attachments/assets/cb512ad2-5436-4c39-85c2-e3dc17baeaee)

---

### Q9: Likely information repository targeted

APT28 aims to steal intellectual property from:

**Answer:** `SharePoint`

![SharePoint Repository](https://github.com/user-attachments/assets/c98b23c0-9c12-4e79-b01e-cff38a42c404)

---

### Q10: Proxy types for C2 evasion

APT28 may use proxies to avoid detection during exfiltration:

**Answer:** `External Proxy and Multi-hop Proxy`

![Proxy Techniques](https://github.com/user-attachments/assets/48015736-2abd-4112-95c6-7593d3a0d703)

---

## ✅ Conclusion

Sunny successfully thwarted APT28’s attempts to steal E-corp’s intellectual property by analyzing the **MITRE ATT&CK Navigator** and monitoring key TTPs.

![Eviction Completed](https://github.com/user-attachments/assets/dc8cea8b-7cd4-4e8c-b909-613856ec46c3)

---

**Walkthrough Author:** Petras Guilherme Kulyumba  
**GitHub:** [@PetrasCyberExpert](https://github.com/PetrasCyberExpert)  
**Project:** Petrasec2025

