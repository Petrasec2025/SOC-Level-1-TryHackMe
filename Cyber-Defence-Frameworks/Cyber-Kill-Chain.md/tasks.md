# 🛡️ TryHackMe: Cyber Kill Chain Room

The **Cyber Kill Chain framework** is designed to identify and prevent network intrusions. Learn the steps adversaries take and how to detect & prevent attacks.

---

## 🔹 Task 1: Introduction

![Cyber Kill Chain Intro](https://github.com/user-attachments/assets/cdbe29b7-abd4-4274-a25f-bf4535211350)

The term **kill chain** originates from the military and describes the structure of an attack:

1. Target identification
2. Decision and order to attack the target
3. Target destruction

**Lockheed Martin (2011)** adapted this for cybersecurity.

**Purpose:** Helps **SOC Analysts, Threat Hunters, Incident Responders** detect intrusion attempts and understand attacker objectives.

**Phases of the Kill Chain:**

| Phase                | Description                                           |
| -------------------- | ----------------------------------------------------- |
| Reconnaissance       | Information gathering on target                      |
| Weaponization        | Create payload using malware + exploit               |
| Delivery             | Transmit payload to target                            |
| Exploitation         | Exploit vulnerability                                |
| Installation         | Establish persistence                                |
| Command & Control    | Remote control via C2 channels                        |
| Actions on Objectives| Achieve goals (exfiltrate data, sabotage, etc.)      |

---

## 🔹 Task 2: Reconnaissance

![Reconnaissance](https://github.com/user-attachments/assets/69d20151-2026-4b0a-905b-4a9e4fe8a626)

**Definition:** Gathering information on a target (planning phase).

**Tools & Techniques:**

| Tool/Method          | Purpose                                               |
| -------------------- | ----------------------------------------------------- |
| theHarvester          | Emails, names, subdomains, IPs, URLs                 |
| Hunter.io             | Email hunting                                        |
| OSINT Framework       | Web interface to OSINT tools                          |
| Social media          | LinkedIn, Facebook, Twitter, Instagram for OSINT     |

<details>
<summary>💡 Answers / Notes</summary>

* **Web-based OSINT interface:** `OSINT Framework`  
* **Email gathering process:** `Email harvesting`

</details>

---

## 🔹 Task 3: Weaponization

![Weaponization](https://github.com/user-attachments/assets/c22c9516-5bec-4258-a910-3d8964a1c8ef)

**Definition:** Combine malware + exploit into a payload.

**Examples:**

- Malicious Office macros/VBA scripts  
- Malicious USB drives  
- Command & Control channels  
- Backdoor implants

<details>
<summary>💡 Answers / Notes</summary>

* **Group of commands in Office documents for malicious purposes:** `Macro`

</details>

---

## 🔹 Task 4: Delivery

![Delivery](https://github.com/user-attachments/assets/e9bc7e1e-30b4-4a25-93c5-354f1cada295)

**Definition:** Transmitting the payload to the victim.

| Method               | Description                                          |
| -------------------- | ---------------------------------------------------- |
| Phishing Emails       | Spearphishing for targeted victims                  |
| USB Drop Attacks      | Malicious USB left for victim to pick up            |
| Watering Hole Attack  | Compromise popular sites; victims download malware  |

<details>
<summary>💡 Answer</summary>

* **Attack via compromised websites targeting specific group:** `Watering hole attack`

</details>

---

## 🔹 Task 5: Exploitation

**Definition:** Attacker takes advantage of a vulnerability.

- Triggered by phishing links/attachments  
- Zero-day exploits (unknown vulnerabilities)  
- Lateral movement post-initial access

<details>
<summary>💡 Answer</summary>

* **Cyberattack exploiting an unknown vulnerability:** `Zero-day exploit`

</details>

---

## 🔹 Task 6: Installation

![Installation](https://github.com/user-attachments/assets/c86f70fd-0429-430a-a270-165f560f4587)

**Definition:** Establish persistence on victim system.

| Technique             | Description                                           |
| --------------------- | ----------------------------------------------------- |
| Web Shell             | `.php`/`.asp`/`.jsp` scripts for remote access      |
| Meterpreter           | Backdoor implant for post-exploitation              |
| Registry Run Keys     | Auto-start malware via Windows Registry             |
| Timestomping          | Modify file timestamps to evade detection           |

<details>
<summary>💡 Answers</summary>

1. **Modify file timestamps:** `Timestomping`  
2. **Malicious script on webserver:** `Web shell`

</details>

---

## 🔹 Task 7: Command & Control (C2)

![Command & Control](https://github.com/user-attachments/assets/2d02c9a5-c5f4-4784-8822-04cb8c8d4421)

**Definition:** Remote control of victim system via C2 channels.

| Technique             | Description                                           |
| --------------------- | ----------------------------------------------------- |
| HTTP/HTTPS Beaconing   | Regular signals to C2 server                         |
| DNS Tunneling          | Using DNS queries to communicate with C2 server      |

<details>
<summary>💡 Answer</summary>

* **C2 communication via DNS:** `DNS Tunneling`

</details>

---

## 🔹 Task 8: Actions on Objectives (Exfiltration)

**Definition:** Attacker achieves final goals.

| Action                  | Description                                        |
| ----------------------- | -------------------------------------------------- |
| Credential Harvesting    | Collect user credentials                            |
| Privilege Escalation     | Gain higher system permissions                      |
| Lateral Movement         | Move through network                                |
| Data Exfiltration         | Steal sensitive data                                 |
| Shadow Copy Deletion      | Delete backups or snapshots                          |

<details>
<summary>💡 Answer</summary>

* **Windows technology for snapshots/backups:** `Shadow Copy`

</details>

---

## 🔹 Task 9: Practice Analysis – Target Breach 2013

**Scenario:** Target breach (Nov 27, 2013) affected ~40 million accounts.

| Kill Chain Phase  | Event                             |
| ----------------- | --------------------------------- |
| Weaponization     | powershell                        |
| Delivery          | spearphishing attachment          |
| Exploitation      | exploit public-facing application |
| Installation      | dynamic linker hijacking          |
| Command & Control | fallback channels                 |
| Exfiltration      | data from local system            |

<details>
<summary>💡 Flag / Notes</summary>

Provided by the static site upon completion.

</details>

---

## 🔹 Task 10: Conclusion

![Conclusion](https://github.com/user-attachments/assets/d45c1025-509c-4167-8318-33cf16579ecc)

**Key Takeaways:**

- Cyber Kill Chain is useful for network defense.  
- Limitations: Last updated 2011, malware & perimeter focus, weak against insider threats.  
- Modern attacks combine multiple TTPs.  
- Recommendation: Combine with **MITRE ATT&CK** or **Unified Kill Chain** for full coverage.

---

> ⚡ This `README.md` is optimized for **GitHub**: clear tables, collapsible answers, and visual structure for easy reference.

