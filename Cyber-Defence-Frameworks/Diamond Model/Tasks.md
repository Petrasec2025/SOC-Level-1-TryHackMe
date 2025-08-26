# Diamond Model – SOC Level 1 🛡️
*Cyber Defence Frameworks – TryHackMe*

![Diamond Model](https://github.com/user-attachments/assets/0f82eda4-3ee6-4094-8c13-2e123f87da38)

**Room Link:** [TryHackMe Diamond Model](https://tryhackme.com/r/room/p/Petras20)

---

## Introduction

The **Diamond Model of Intrusion Analysis** was developed by cybersecurity professionals — **Sergio Caltagirone, Andrew Pendergast, and Christopher Betz** in 2013.

The model consists of **four core features**:

- **Adversary**
- **Infrastructure**
- **Capability**
- **Victim**

It establishes the **fundamental atomic element** of any intrusion activity. Additional axes include **Social, Political, and Technology** components.

### Why “Diamond Model”?

The four core features are **edge-connected**, forming the shape of a diamond.  
It enables:

- Real-time intelligence integration
- Event correlation automation
- Classification into adversary campaigns
- Forecasting adversary operations
- Planning mitigation strategies

![Diamond Model Diagram](https://github.com/user-attachments/assets/69b98f64-adfb-4611-81a1-0c0919d698d2)

### Benefits of Learning the Diamond Model

- Identify elements of an intrusion
- Analyze **Advanced Persistent Threats (APT)**
- Explain cyber incidents to **non-technical audiences**
- Apply structured analysis to breaches, intrusions, and attacks

---

## Task 1 – Adversary

An **adversary** is also known as an **attacker, hacker, or threat actor**.  

- Responsible for using **capabilities against victims** to achieve intent
- Knowledge of the adversary is often **unknown during initial discovery**
- Distinguish between **adversary operator** and **adversary customer**

### Key Terms

- **Adversary Operator** – Person(s) conducting the intrusion  
- **Adversary Customer** – Entity benefiting from the cyberattack  

**Questions:**

1. Term for person/group intending malicious actions?  
   **Answer:** Adversary Operator  

2. Term for person/group benefiting from the attack?  
   **Answer:** Adversary Customer

---

## Task 2 – Victim

A **victim** is the target of the adversary and can include:

- Organizations, individuals, IPs, domains, emails, etc.
- Victim Persona: People/organizations targeted
- Victim Assets: Systems, networks, accounts, email addresses  

**Example:** Spear-phishing targeting a specific employee.

**Question:**

- Term for organizations/people being targeted?  
  **Answer:** Victim Personae

---

## Task 3 – Capability

**Capability** includes skills, tools, and techniques used by the adversary (TTPs).  

- Can range from **manual attacks** to **malware development**
- **Capability Capacity** – vulnerabilities exploited by a capability
- **Adversary Arsenal** – Set of capabilities belonging to an adversary

**Question:**

- Term for set of tools/capabilities of an adversary?  
  **Answer:** Adversary Arsenal

---

## Task 4 – Infrastructure

**Infrastructure** refers to the **physical or logical resources** used by the adversary:

- Software, hardware, C2 servers, IPs, domains, emails, USB devices
- **Type 1 Infrastructure** – Controlled/owned by adversary
- **Type 2 Infrastructure** – Controlled by intermediaries to obfuscate attribution
- **Service Providers** – Critical support (ISPs, domain registrars, email providers)

**Questions:**

1. Malicious domains and compromised emails?  
   **Answer:** Type 2 Infrastructure  

2. Infrastructure most likely owned by adversary?  
   **Answer:** Type 1 Infrastructure

---

## Task 5 – Event Meta Features

Meta-features add intelligence to the Diamond Model:

1. **Timestamp** – Date/time of event
2. **Phase** – Stage of intrusion (Reconnaissance, Weaponization, Delivery, Exploitation, Installation, Command & Control, Actions on Objective)
3. **Result** – Success, Failure, Unknown; can map to CIA triad
4. **Direction** – Flow of events (Victim→Infrastructure, Infrastructure→Victim, etc.)
5. **Methodology** – General classification (Phishing, DDoS, Breach, etc.)
6. **Resources** – External resources required (software, knowledge, hardware, funds, access)

**Questions:**

1. “Every malicious activity contains two or more phases…” → **Phase**  
2. Label event as success/failure/unknown → **Result**  
3. “Every intrusion event requires one or more external resources…” → **Resources**

![Meta Features](https://github.com/user-attachments/assets/fe95e109-55da-4d91-965d-6bff23b3f89a)

---

## Task 6 – Social-Political Component

- Describes **adversary needs and intent** (financial gain, hacktivism, espionage)
- Scenario: Victim provides product (e.g., computing resources) and adversary gains benefit

---

## Task 7 – Technology Component

- Shows relationship between **capability and infrastructure**
- Example: **Watering-hole attack** – adversary compromises websites frequented by target victims

---

## Task 8 – Practice Analysis

- Deploy the static site attached in the task
- Extract information to populate the Diamond Model
- Complete all **eight areas of the diamond**

**Flag:**  
`THM{DIAMOND_MODEL_ATTACK_CHAIN}`

![Practice Screenshots 1](https://github.com/user-attachments/assets/dca83328-5ea7-43a1-88af-43dd27daa9d8)  
![Practice Screenshots 2](https://github.com/user-attachments/assets/f2707f30-78f9-4cce-a80f-8cc643a17a22)  
![Practice Screenshots 3](https://github.com/user-attachments/assets/94b02d26-44f4-4893-9be4-5ca6d59db2e5)  
![Practice Screenshots 4](https://github.com/user-attachments/assets/3b2984fc-ab27-44ca-8087-f31f40401740)  
![Practice Screenshots 5](https://github.com/user-attachments/assets/6c0fd640-178f-472c-ba9e-7e119a9696b1)  
![Practice Screenshots 6](https://github.com/user-attachments/assets/43e78182-07b1-4891-bcc0-85dba62ac105)  
![Practice Screenshots 7](https://github.com/user-attachments/assets/d475aa47-d2d3-4d0d-a580-6d9991dfda0f)  
![Practice Screenshots 8](https://github.com/user-attachments/assets/b7703a1f-ea2a-4b2a-adbc-f9f0063d74a2)  
![Practice Screenshots 9](https://github.com/user-attachments/assets/b3583728-d947-459b-b701-683eb0ac93af)  
![Practice Screenshots 10](https://github.com/user-attachments/assets/88332482-2dba-4e4a-9e7c-32cc6d00ab8c)

---

## Conclusion

This room provided a **practical and structured approach** to cyber intrusion analysis. Key takeaways:

- Break down attacks into **Adversary, Victim, Capability, Infrastructure**
- Use meta-features (**Phase, Result, Resources**) to enhance analysis
- Social-Political and Technology components help understand motives and methods
- Useful for communicating with **non-technical stakeholders**
- Reinforces **threat hunting, incident response, and intrusion analysis skills**

The Diamond Model is a **valuable tool** for real-world cybersecurity operations.

---









