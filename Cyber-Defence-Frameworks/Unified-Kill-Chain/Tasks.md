# TryHackMe Unified Kill Chain Room 🚀

![TryHackMe Badge](https://img.shields.io/badge/TryHackMe-Cybersecurity-blue?style=for-the-badge)
![Cybersecurity](https://img.shields.io/badge/Cybersecurity-Ethical_Hacking-red?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)

The **Unified Kill Chain (UKC)** is a framework which establishes the phases of an attack, and a means of identifying and mitigating risk to IT assets.

---

## Task 1: Introduction

![Task 1](https://github.com/user-attachments/assets/5c9c9d13-e95f-4c90-aea5-a3e75a66a709)

Understanding the behaviours, objectives and methodologies of a cyber threat is a vital step to establishing a strong cybersecurity defence (known as a cybersecurity posture).

In this room, you will be introduced to the **UKC framework** that is used to help understand how cyber attacks occur.

**Learning Objectives:**

* Understanding why frameworks such as the UKC are important and helpful in establishing a good cybersecurity posture
* Using the UKC to understand an attacker’s motivation, methodologies and tactics
* Understanding the various phases of the UKC
* Discover that the UKC is a framework that is used to complement other frameworks such as MITRE

---

## Task 2: What is a “Kill Chain”

![Task 2](https://github.com/user-attachments/assets/32bf04a7-7324-472b-a5b4-0f9f4b69c013)

Originating from the military, a **“Kill Chain”** is a term used to explain the various stages of an attack. In cybersecurity, it describes the methodology/path attackers use to approach and intrude a target.

**Example:** An attacker scanning, exploiting a web vulnerability, and escalating privileges is a “Kill Chain”.

**Objective:** Understand an attacker’s “Kill Chain” to put defensive measures in place.

**Question:**

* Where does the term “Kill Chain” originate from?
  *Answer hint: The first sentence of this task.*

![Task 2 Screenshot](https://github.com/user-attachments/assets/96b78b4f-93c7-4474-b219-3267b8d3b8ce)

---

## Task 3: What is “Threat Modelling”

![Task 3](https://github.com/user-attachments/assets/b3967eed-302b-4a08-b38e-ab2092071256)

Threat modelling is a series of steps to improve the security of a system, essentially:

1. Identify systems and applications to secure
2. Assess vulnerabilities and potential exploits
3. Create a plan of action to secure systems
4. Implement policies to prevent future vulnerabilities

Threat modelling reduces risk within a system or application and gives an overview of IT assets.

**Frameworks used in Threat Modelling:** STRIDE, DREAD, CVSS

**Question:**

* What is the technical term for a piece of software or hardware in IT?
  *Answer hint: End of the explanatory sentence above.*

![Task 3 Screenshot](https://github.com/user-attachments/assets/7f18bce3-715f-4359-bbf7-11a81215e133)

---

## Task 4: Introducing the Unified Kill Chain

![Task 4](https://github.com/user-attachments/assets/12e775bf-1412-4be6-8383-72d311c8bf48)

* Published in 2017, the UKC complements other frameworks like Lockheed Martin’s and MITRE ATT\&CK.
* **18 phases** of an attack: From reconnaissance to exfiltration, including attacker motivation.
* UKC advantages: Modern, detailed, covers entire attacks, realistic (phases may recur).

![UKC Benefits](https://github.com/user-attachments/assets/a3463b7c-5e5d-41cf-a6d6-3813b6a57389)

**Questions:**

* In what year was the Unified Kill Chain framework released?
* How many phases are there in an attack according to UKC?
* Name of the attack phase where an attacker employs techniques to evade detection?
* Name of the attack phase where an attacker removes data from a network?
* Name of the attack phase where an attacker achieves their objectives?

![Task 4 Screenshots](https://github.com/user-attachments/assets/38da0ba5-7c68-40c8-af4d-bf02b9c53cf7)
![Task 4 Screenshots](https://github.com/user-attachments/assets/344824a0-5499-469c-a285-ebf437189c90)
![Task 4 Screenshots](https://github.com/user-attachments/assets/3c32a5ea-b3b8-467f-8571-47e8ad31de8a)
![Task 4 Screenshots](https://github.com/user-attachments/assets/a66c704a-9a61-40bf-8518-4e7e651a6a54)
![Task 4 Screenshots](https://github.com/user-attachments/assets/70f815cc-13cc-437f-a98f-4c8a93f2889e)

---

## Task 5: Phase – Initial Foothold

![Task 5](https://github.com/user-attachments/assets/6015d836-09d3-4572-bcf4-23c19b95e626)

**Focus:** Attacker gains access to a system/network. Techniques include reconnaissance, persistence, and initial exploitation.

### Phases & MITRE Tactics

* **Reconnaissance (TA0043):** Gather info about target
* **Weaponization (TA0001):** Prepare attack infrastructure
* **Social Engineering (TA0001):** Manipulate employees (e.g., phishing)
* **Exploitation (TA0002):** Exploit vulnerabilities to execute code
* **Persistence (TA0003):** Maintain access (e.g., backdoors, services)
* **Defence Evasion (TA0005):** Evade defenses (firewalls, AV, IDS)
* **Command & Control (TA0011):** Establish attacker communications
* **Pivoting (TA0008):** Access other network systems

**Questions:**

* Example of a tactic to gain foothold using emails? **Answer:** Phishing
* Impersonating an employee to request password reset? **Answer:** Social Engineering
* Setting up Command & Control server infrastructure? **Answer:** Command & Control
* Exploiting a vulnerability on a system? **Answer:** Exploitation
* Moving from one system to another? **Answer:** Pivoting
* Leaving behind a malicious service for re-entry? **Answer:** Persistence

![Task 5 Screenshots](https://github.com/user-attachments/assets/4ae1e605-e090-4eea-80c5-6b42b543fa07)
![Task 5 Screenshots](https://github.com/user-attachments/assets/5001f4ff-3d5d-4625-9dc5-68ba802718f8)
![Task 5 Screenshots](https://github.com/user-attachments/assets/6cd6ab07-7285-4284-8d15-6c70d646749d)

---

## Task 6: Phase – Network Propagation

![Task 6](https://github.com/user-attachments/assets/f078c05c-ea6d-4fb6-af30-8409d4fcf8e0)

* After foothold, attacker seeks further access and privileges.
* **Pivoting (TA0008), Discovery (TA0007), Privilege Escalation (TA0004), Execution (TA0002), Credential Access (TA0006), Lateral Movement (TA0008)**

**Questions:**

* Failed login attempts from admin account? **Answer:** Privilege Escalation
* Mimikatz detected running? **Answer:** Credential Access

![Task 6 Screenshots](https://github.com/user-attachments/assets/7d5da476-7528-4ba1-a71c-4d7f8629532f)

---

## Task 7: Phase – Action on Objectives

![Task 7](https://github.com/user-attachments/assets/5d678fd2-e97b-4dc2-9f06-ff83d5eb46c7)

* **Collection (TA0009), Exfiltration (TA0010), Impact (TA0040), Objectives**

**Questions:**

* Outbound traffic to unknown IP? **Answer:** Exfiltration
* PII released to public, CIA triad affected? **Answer:** Confidentiality

![Task 7 Screenshots](https://github.com/user-attachments/assets/6d85dc96-4d8b-4dc9-a9dd-38ccd0afe68f)

---

## Task 8: Practical

![Task 8](https://github.com/user-attachments/assets/850d82ca-ae4a-4236-8230-6f262e6c5c23)

**Instructions:** Deploy the static site attached and match attacker actions to UKC phases.

**Sample Questions & Answers:**

1. Attacker gathers information → Reconnaissance
2. Installs malicious script → Persistence
3. Hacked machine controlled from attacker server → Command & Control
4. Accesses other servers → Pivoting
5. Steals database → Collection / Exfiltration

**Flag:** `THM{UKC_SCENARIO}`

![Task 8 Screenshots](https://github.com/user-attachments/assets/67dc7737-79a2-4707-b6c3-01af3abed1bb)

---

## Task 9: Conclusion

This room provides a structured view of the **Unified Kill Chain framework**, showing the phases of a cyber attack and how defensive measures can be applied effectively.
