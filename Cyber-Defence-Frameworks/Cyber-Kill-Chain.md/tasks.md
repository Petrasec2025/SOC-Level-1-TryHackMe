# TryHackMe Cyber Kill Chain Room

The Cyber Kill Chain framework is designed for identification and prevention of network intrusions. You will learn what the adversaries need to do in order to achieve their goals.

---

## Task 1: Introduction

![Task 1](https://github.com/user-attachments/assets/cdbe29b7-abd4-4274-a25f-bf4535211350)

The term **kill chain** is a military concept related to the structure of an attack. It consists of target identification, decision and order to attack the target, and finally the target destruction.  

Thanks to **Lockheed Martin**, a global security and aerospace company, which established the **Cyber Kill Chain® framework** for the cybersecurity industry in 2011 based on the military concept. The framework defines the steps used by adversaries or malicious actors in cyberspace. To succeed, an adversary needs to go through all phases of the Kill Chain.

We will go through the attack phases and help you better understand adversaries and their techniques used in the attack to defend yourself.

### Importance of Cyber Kill Chain

The Cyber Kill Chain helps you understand and protect against:

- Ransomware attacks  
- Security breaches  
- Advanced Persistent Threats (APTs)  

As a SOC Analyst, Security Researcher, Threat Hunter, or Incident Responder, you will be able to recognize intrusion attempts and understand the intruder’s goals and objectives.

### Attack Phases

We will explore the following attack phases:

1. Reconnaissance  
2. Weaponization  
3. Delivery  
4. Exploitation  
5. Installation  
6. Command & Control  
7. Actions on Objectives  

**Learning Objectives:** Learn about each phase of the Cyber Kill Chain Framework, and the advantages and disadvantages of the traditional Cyber Kill Chain.  

**Outcome:** Recognize different phases or stages of the attack carried out by an adversary and be able to break the “kill chain.”

---

## Task 2: Reconnaissance

![Reconnaissance](https://github.com/user-attachments/assets/69d20151-2026-4b0a-905b-4a9e4fe8a626)

**Definition:**  
Reconnaissance is discovering and collecting information on the system and the victim. This is the planning phase for the adversaries.

**OSINT (Open-Source Intelligence):**  
OSINT is the first step an attacker completes to carry out further phases of an attack. It involves studying the victim and collecting publicly available information like company size, email addresses, and phone numbers.

### Tools for Reconnaissance

- **theHarvester:** Gathers emails, names, subdomains, IPs, and URLs using multiple public data sources.  
- **Hunter.io:** Email hunting tool to obtain contact information associated with a domain.  
- **OSINT Framework:** Web-based interface providing a collection of OSINT tools based on categories.

Attackers also use social media (LinkedIn, Facebook, Twitter, Instagram) to gather information for phishing attacks.

**Questions:**

1. **Intel Gathering Tool (web-based interface):** OSINT Framework  
2. **Email harvesting definition:** Process of obtaining email addresses from public, paid, or free services.

---

## Task 3: Weaponization

![Weaponization](https://github.com/user-attachments/assets/c22c9516-5bec-4258-a910-3d8964a1c8ef)

After reconnaissance, the attacker crafts a **“weapon of destruction”**.  

**Key Terms:**

- **Malware:** Software designed to damage, disrupt, or gain unauthorized access.  
- **Exploit:** Code that takes advantage of a vulnerability.  
- **Payload:** Malicious code executed on the system.

**Techniques:**

- Create infected Microsoft Office documents with malicious macros or VBA scripts.  
- Purchase malware from the Dark Web.  
- Implant backdoors for Command & Control (C2) execution.  

**Question:**  
**Term for subroutines/functions used for automation or malicious purposes:** `Macro`

---

## Task 4: Delivery

![Delivery](https://github.com/user-attachments/assets/e9bc7e1e-30b4-4a25-93c5-354f1cada295)

**Delivery Phase:** Method for transmitting malware or payload.  

**Methods:**

- **Phishing email / Spearphishing:** Targeted emails containing malware.  
- **USB Drop Attack:** Distribute infected USB drives in public.  
- **Watering Hole Attack:** Compromise a website frequented by a specific group, leading to a drive-by download.

**Question:**  
**Attack targeting a specific group via their frequented website:** `Watering hole attack`

---

## Task 5: Exploitation

**Exploitation Phase:** Attacker exploits vulnerabilities to gain access.  

**Examples:**

- Victim clicks malicious link or opens attachment.  
- Use of zero-day exploits (unknown vulnerabilities).  
- Exploit software, hardware, or human vulnerabilities.

**Question:**  
**Cyberattack targeting unknown software vulnerability:** `Zero-day exploit`

---

## Task 6: Installation

![Installation](https://github.com/user-attachments/assets/c86f70fd-0429-430a-a270-165f560f4587)

**Installation Phase:** Install persistent backdoors to maintain access.

**Techniques:**

- Web shells on servers (`.php`, `.asp`, `.aspx`, `.jsp`).  
- Backdoors via **Meterpreter**.  
- Create/modify Windows services (MITRE T1543.003).  
- Add registry “run keys” or startup folder entries.  
- **Timestomping:** Modify file timestamps to avoid detection.

**Questions:**  

1. **Technique to modify file time attributes:** `Timestomping`  
2. **Malicious script planted on a webserver:** `Web shell`

---

## Task 7: Command & Control

![Command & Control](https://github.com/user-attachments/assets/2d02c9a5-c5f4-4784-8822-04cb8c8d4421)

**C2 Phase:** Attacker remotely controls the victim via malware.

**C2 Channels:**

- HTTP/HTTPS (port 80/443) to blend malicious traffic with legitimate traffic.  
- **DNS Tunneling:** Victim makes regular DNS requests to attacker-controlled servers.

**Question:**  
**C2 communication using DNS requests:** `DNS Tunneling`

---

## Task 8: Actions on Objectives (Exfiltration)

**Actions on Objectives:** Attacker achieves their goal with system access.  

**Possible Actions:**

- Collect credentials.  
- Privilege escalation.  
- Internal reconnaissance.  
- Lateral movement.  
- Exfiltrate sensitive data.  
- Delete backups and shadow copies.  
- Overwrite or corrupt data.

**Question:**  
**Technology in Windows for backups/snapshots:** `Shadow Copy`

---

## Task 9: Practice Analysis

**Scenario:** Target Cyber-attack, Nov 27, 2013.  

**Steps to Build Cyber Kill Chain:**

| Kill Chain Phase | Action |
|-----------------|--------|
| Weaponization | powershell |
| Delivery | spearphishing attachment |
| Exploitation | exploit public-facing application |
| Installation | dynamic linker hijacking |
| Command & Control | fallback channels |
| Exfiltration | data from local system |

**Tip:** Use the provided static site lab to verify answers.  
After completing, the **flag** will appear on the site.

![Practice Analysis](https://github.com/user-attachments/assets/57db215b-0199-46aa-8952-49fa9f141f54)

---

## Task 10: Conclusion

![Conclusion](https://github.com/user-attachments/assets/d45c1025-509c-4167-8318-33cf16579ecc)

- The Cyber Kill Chain is useful for network defense but not perfect.  
- Traditional Cyber Kill Chain (2011) focuses mainly on malware delivery and perimeter security.  
- It may not detect insider threats or sophisticated modern attacks.  
- Recommendation: Combine with frameworks like **MITRE ATT&CK** and **Unified Kill Chain** for comprehensive defense.

---

*End of TryHackMe Cyber Kill Chain Room README*
