TryHackMe: Cyber Kill Chain Room

The Cyber Kill Chain framework is designed for identification and prevention of network intrusions. In this room, you will learn the steps adversaries take to achieve their goals and how to detect and prevent attacks.

Task 1: Introduction

The term kill chain originates from the military and describes the structure of an attack:

Target identification

Decision and order to attack the target

Target destruction

Lockheed Martin adapted this concept for cybersecurity in 2011, defining steps used by malicious actors in cyberspace. To succeed, an adversary must pass through all phases of the Kill Chain.

Importance

Understanding the Cyber Kill Chain helps defend against:

Ransomware attacks

Security breaches

Advanced Persistent Threats (APTs)

It allows SOC Analysts, Threat Hunters, and Incident Responders to recognize intrusion attempts and understand attacker objectives.

Attack Phases

Reconnaissance

Weaponization

Delivery

Exploitation

Installation

Command & Control

Actions on Objectives

Learning Objectives: Learn the phases of the Cyber Kill Chain, and understand the pros and cons of the traditional model.

Outcome: Recognize attack phases and break the kill chain.

Task 2: Reconnaissance

Definition: Reconnaissance is the process of discovering and collecting information on a target system or victim. It is the planning phase of an attack.

OSINT (Open-Source Intelligence) is part of reconnaissance.

Attackers gather information such as email addresses, phone numbers, and company size.

Tools used for reconnaissance:

theHarvester – gathers emails, names, subdomains, IPs, URLs

Hunter.io – email hunting tool

OSINT Framework – web-based interface to OSINT tools

Social media (LinkedIn, Facebook, Twitter, Instagram) can provide valuable information for phishing attacks.

Scenario: A malicious attacker, “Megatron,” begins his attack planning with OSINT to study the target.

Questions:

Web-based OSINT interface: OSINT Framework

Email gathering process: Email harvesting

Task 3: Weaponization

Definition: Weaponization combines malware and exploit into a deliverable payload.

Malware: Software designed to damage, disrupt, or gain unauthorized access

Exploit: Code that leverages a vulnerability

Payload: Malicious code executed on the target system

Example Techniques:

Infected Microsoft Office documents with malicious macros/VBA scripts

Malicious USB drives or worms

Command and Control (C2) channels

Backdoor implants

Question:

Group of commands in Office documents for malicious purposes: Macro

Task 4: Delivery

Definition: The attacker transmits the payload to the victim.

Methods:

Phishing emails (spearphishing for specific targets)

USB Drop Attacks

Watering hole attacks: compromise websites frequented by the target group; victims download malware unintentionally

Question:

Attack targeting specific group via compromised websites: Watering hole attack

Task 5: Exploitation

Definition: Exploitation occurs when the attacker takes advantage of a vulnerability.

Triggered by phishing links or attachments

Zero-day exploits: vulnerabilities unknown to vendors, leaving no opportunity for detection

Lateral movement: spreading through the network after initial access

Question:

Cyberattack exploiting an unknown vulnerability: Zero-day exploit

Task 6: Installation

Definition: The attacker installs persistent backdoors to maintain access.

Techniques:

Web shells (.php, .asp, .jsp)

Backdoors (e.g., Meterpreter)

Modifying Windows services (MITRE ATT&CK T1543.003)

Registry Run Keys / Startup Folder

Timestomping – modifies file timestamps to evade detection

Questions:

Technique to modify file timestamps: Timestomping

Malicious script on webserver: Web shell

Task 7: Command & Control

Definition: After persistence, the attacker remotely controls the victim’s system via C2 channels.

Examples:

HTTP/HTTPS beaconing

DNS tunneling – victim makes DNS requests to attacker-controlled server

Question:

C2 communication via DNS: DNS Tunneling

Task 8: Actions on Objectives (Exfiltration)

Definition: The attacker achieves their goals.

Possible actions:

Collect credentials

Privilege escalation

Internal reconnaissance

Lateral movement

Exfiltrate sensitive data

Delete backups/shadow copies

Overwrite or corrupt data

Question:

Windows technology for snapshots/backups: Shadow Copy

Task 9: Practice Analysis (Target Data Breach 2013)

Scenario: Target data breach on Nov 27, 2013, affected ~40 million credit/debit accounts.

Static Site Lab Answers:

Kill Chain Phase	Event
Weaponization	powershell
Delivery	spearphishing attachment
Exploitation	exploit public-facing application
Installation	dynamic linker hijacking
Command & Control	fallback channels
Exfiltration	data from local system

Flag: Provided by the static site upon completion.

Task 10: Conclusion

The Cyber Kill Chain is a valuable tool for improving network defense.

Limitations: Last updated in 2011, focuses on malware and perimeter defense, cannot detect insider threats effectively.

Modern threats combine multiple tactics, techniques, and procedures (TTPs).

Recommendation: Use MITRE ATT&CK and Unified Kill Chain alongside the traditional framework for a comprehensive defense strategy.
