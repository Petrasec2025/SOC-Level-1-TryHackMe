# MITRE TryHackMe Walkthrough

This repository contains my complete walkthrough for the **[MITRE TryHackMe Room](https://tryhackme.com/room/mitre)**.  
The room introduces the resources MITRE has made available for the cybersecurity community, including ATT&CK®, CAR, Engage, D3FEND, and Adversary Emulation Plans.

---

## Task 1: Introduction to MITRE

**#1.1** Read above.  
✅ No answer is needed.

---

## Task 2: Basic Terminology

**#2.1** Read above.  
✅ No answer is needed.

---

## Task 3: ATT&CK® Framework

### #3.1 Besides blue teamers, who else will use the ATT&CK Matrix?  
Answer: **Red Teamers**  
<img src="https://github.com/user-attachments/assets/391b4221-20ce-4d91-a8e1-6acf99d81c09" width="700">

---

### #3.2 What is the ID for this technique?  
Technique: **Phishing**  
Answer: **T1566**  
<img src="https://github.com/user-attachments/assets/59e699de-024c-4b74-b2ec-5f2d1873938f" width="700">

---

### #3.3 Mitigation for identifying social engineering techniques  
Answer: **User Training**  
<img src="https://github.com/user-attachments/assets/00a37b7b-bf50-4dc0-970b-60c0e4bce61d" width="700">

---

### #3.4 What are the data sources for Detection?  
Answer: **Application Log,File,Network Traffic**  
<img src="https://github.com/user-attachments/assets/cec7d995-f5f5-488f-a90c-cf63286b34b5" width="700">

---

### #3.5 What groups have used spear-phishing in their campaigns?  
Answer: **Axiom,Gold SOUTHFIELD**  
<img src="https://github.com/user-attachments/assets/6b5d0979-874c-4dd5-8b81-1ecf63e507c5" width="700">

---

### #3.6 Associated groups for Axiom  
Answer: **Group 72**  
<img src="https://github.com/user-attachments/assets/7a994745-c802-436f-9e16-aa47d7e05abd" width="700">

---

### #3.7 Software associated with Axiom that lists phishing  
Answer: **Hikit**  
<img src="https://github.com/user-attachments/assets/82628be0-cbf4-4a8c-9166-c58a8224fb55" width="700">

---

### #3.8 Description of this software  
Answer:  
> Hikit is malware that has been used by Axiom for late-stage persistence and exfiltration after the initial compromise.  
<img src="https://github.com/user-attachments/assets/a4523696-fb79-432b-af63-aa4b13a142ba" width="600">

---

### #3.9 Group overlap  
Answer: **Winnti Group**  
<img src="https://github.com/user-attachments/assets/6ec02303-9097-41db-82d9-c4c134feb310" width="700">

---

### #3.10 Number of techniques attributed to this group  
Answer: **15**  
<img src="https://github.com/user-attachments/assets/b65b7630-9c64-4544-9ff1-b15d9f4f51f1" width="700">

---

## Task 4: CAR Knowledge Base

### #4.1 What is the pseudocode a representation of?  
Answer: **Splunk search**  
<img src="https://github.com/user-attachments/assets/7993ae86-d2c3-4be7-a447-d1b8d25560c3" width="600">

---

### #4.2 What tactic has an ID of TA0003?  
Answer: **Persistence**  
<img src="https://github.com/user-attachments/assets/c9d39c3f-49e5-45d2-8de2-9247ac161a63" width="400">

---

### #4.3 Library of Zeek (BRO) scripts  
Answer: **BZAR**  
<img src="https://github.com/user-attachments/assets/c2d40c72-6e90-400f-b0f9-75600a63b617" width="700">

---

### #4.4 Technique for running executables with same hash, different names  
Answer: **Masquerading**  
<img src="https://github.com/user-attachments/assets/3f4c878d-7d16-4e5c-b42a-c5bb00434e1e" width="700">

---

### #4.5 Additional info provided in CAR-2013–05–004 besides Implementations  
Answer: **[Content from screenshot]**  
<img src="https://github.com/user-attachments/assets/3ad22263-3405-4482-ba6c-bbf88fcb199a" width="600">

---

## Task 5: MITRE Engage

### #5.1 Under Prepare, what is ID SAC0002?  
Answer: **Persona Creation**  
<img src="https://github.com/user-attachments/assets/362bc040-5177-47cf-a3af-497485c839d4" width="700">

---

### #5.2 Resource to aid Persona Creation  
Answer: **Persona Profile Worksheet**  
<img src="https://github.com/user-attachments/assets/ca422fa1-5f9b-4103-b4d6-739554ee864e" width="600">

---

### #5.3 Which engagement activity baits a specific response?  
Answer: **Lures**  
<img src="https://github.com/user-attachments/assets/8b5ca9f8-479f-4443-85a2-3b1d4d7f0db4" width="500">

---

### #5.4 Definition of Threat Model  
Answer:  
> A risk assessment that models organizational strengths and weaknesses.  
<img src="https://github.com/user-attachments/assets/fd2e85f7-aac6-49dc-bc54-36fabf7f5e0b" width="600">

---

## Task 6: MITRE D3FEND

### #6.1 First ATT&CK technique in Lookup  
Answer: **Data Obfuscation**  
<img src="https://github.com/user-attachments/assets/cbc3ccec-3416-4676-a1a3-44e7f10feaa7" width="600">

---

### #6.2 What does Data Obfuscation produce?  
Answer: **Outbound Internet Network Traffic**  
<img src="https://github.com/user-attachments/assets/e9e22f2b-e3aa-42ae-a21d-be4f97d41540" width="500">

---

## Task 7: ATT&CK® Emulation Plans

### #7.1 APT3 Emulation Plan Phase 1 (first listed)  
Answer: **C2 Setup**  
<img src="https://github.com/user-attachments/assets/30fd8d3b-520e-4305-86e3-a7ef99eba116" width="600">

---

### #7.2 Persistence binary replaced with cmd.exe  
Answer: **sethc.exe**  
<img src="https://github.com/user-attachments/assets/4e58c37d-d914-42f1-9e6b-34149f3bfd6a" width="700">

---

### #7.3 APT29 Scenario 1 Infrastructure C2 frameworks  
Answer: **Pupy,Metasploit Framework**  
<img src="https://github.com/user-attachments/assets/83832d82-6ea5-47a9-ac24-2bcbc1bad69f" width="600">

---

### #7.4 APT29 Scenario 2 Infrastructure C2 framework  
Answer: **PoshC2**  
<img src="https://github.com/user-attachments/assets/f6278f8d-ab83-4146-b146-744b74e1be6d" width="700">

---

### #7.5 Sandworm Scenario 1 Webshell + Software ID  
Answer: **P.A.S., S0598**  
<img src="https://github.com/user-attachments/assets/74f4d8db-0ce2-48b0-a101-d912efaa0d63" width="700">

---

## Task 8: ATT&CK® and Threat Intelligence

### #8.1 APT group targeting Aviation sector since 2013  
Answer: **APT33**  
<img src="https://github.com/user-attachments/assets/cbddde4e-fe60-4799-bf9b-0c20986b27ef" width="700">

---

### #8.2 Cloud-related attribution for APT33  
Answer: **Ruler**  
<img src="https://github.com/user-attachments/assets/a7be2641-2e7b-4ce0-83fa-6c55f780772c" width="700">

---

### #8.4 Mitigation using SMS for implementation  
Answer: **Multi-factor Authentication**  
<img src="https://github.com/user-attachments/assets/f0d9125f-7221-49bb-b612-876d3855fce6" width="600">

---

### #8.5 Platforms affected by Valid Accounts: Cloud Accounts  
Answer: **Azure AD, Google Workspace, IaaS, Office 365, SaaS**  
<img src="https://github.com/user-attachments/assets/f10e48d9-900f-4019-8629-2c68fef0f7a6" width="700">

---

## Task 9: Conclusion

This walkthrough demonstrates the usage of MITRE’s resources:  
- **ATT&CK® Framework** (Adversary Tactics, Techniques, Procedures)  
- **CAR Knowledge Base** (Analytics for detections)  
- **MITRE Engage** (Adversary engagement activities)  
- **D3FEND** (Defensive techniques)  
- **Adversary Emulation Plans** (APT playbooks)  

📘 Completing this room helps strengthen both **offensive (red team)** and **defensive (blue team)** cybersecurity skills.

---

## References
- [MITRE ATT&CK](https://attack.mitre.org/)  
- [MITRE CAR](https://car.mitre.org/)  
- [MITRE Engage](https://engage.mitre.org/)  
- [MITRE D3FEND](https://d3fend.mitre.org/)  
- [MITRE Adversary Emulation Library](https://github.com/center-for-threat-informed-defense/adversary_emulation_library)  












