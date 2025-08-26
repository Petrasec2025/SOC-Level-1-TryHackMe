Diamond Model — SOC Level 1 -Cyber Defence Frameworks — TryHackMe Walkthrough
---
Learn about the four core features of the Diamond Model of Intrusion Analysis: adversary, infrastructure, capability, and victim.
<img width="664" height="305" alt="Screenshot 2025-08-26 at 9 36 09 PM" src="https://github.com/user-attachments/assets/0f82eda4-3ee6-4094-8c13-2e123f87da38" />
Site Link: https://tryhackme.com/r/room/p/Petras20

---
<img width="594" height="93" alt="Screenshot 2025-08-26 at 9 36 19 PM" src="https://github.com/user-attachments/assets/660f258b-8c52-4e60-b3d4-1e4c7f2e15b0" />
Task 1 Introduction
What is The Diamond Model?

The Diamond Model of Intrusion Analysis was developed by cybersecurity professionals — Sergio Caltagirone, Andrew Pendergast, and Christopher Betz in 2013.

As described by its creators, the Diamond Model is composed of four core features: adversary, infrastructure, capability, and victim, and establishes the fundamental atomic element of any intrusion activity. You might have also noticed two additional components or axes of the Diamond Model — Social, Political and Technology; we will go into a little bit more detail about them later in this room. Why is it called a “Diamond Model”? The four core features are edge-connected, representing their underlying relationships and arranged in the shape of a diamond.

The Diamond Model carries the essential concepts of intrusion analysis and adversary operations while allowing the flexibility to expand and encompass new ideas and concepts. The model provides various opportunities to integrate intelligence in real-time for network defence, automating correlation across events, classifying events with confidence into adversary campaigns, and forecasting adversary operations while planning and gaming mitigation strategies.

<img width="208" height="117" alt="Screenshot 2025-08-26 at 9 36 24 PM" src="https://github.com/user-attachments/assets/69b98f64-adfb-4611-81a1-0c0919d698d2" />
Why should you learn about The Diamond Model?

The Diamond Model can help you identify the elements of an intrusion. At the end of this room, you will create a Diamond Model for events such as a breach, intrusion, attack, or incident. You will also be able to analyze an Advanced Persistent Threat (APT).

The Diamond Model can also help explain to other people who are non-technical about what happened during an event or any valuable information on the malicious threat actor.

Answer the questions below

Read the above.

Task 2 Adversary
Who is an Adversary?

An adversary is also known as an attacker, enemy, cyber threat actor, or hacker. The adversary is the person who stands behind the cyberattack. Cyberattacks can be an instruction or a breach.

According to the creators of the Diamond Model, an adversary is an actor or organization responsible for utilizing a capability against the victim to achieve their intent. Adversary knowledge can generally be mysterious, and this core feature is likely to be empty for most events — at least at the time of discovery.

It is essential to know the distinction between adversary operator and adversary customer because it will help you understand intent, attribution, adaptability, and persistence by helping to frame the relationship between an adversary and victim pair.

It is difficult to identify an adversary during the first stages of a cyberattack. Utilizing data collected from an incident or breach, signatures, and other relevant information can help you determine who the adversary might be.

Adversary Operator is the “hacker” or person(s) conducting the intrusion activity.

Adversary Customer is the entity that stands to benefit from the activity conducted in the intrusion. It may be the same person who stands behind the adversary operator, or it may be a separate person or group.

As an example, an adversary customer could control different operators simultaneously. Each operator might have its capabilities and infrastructure.

Answer the questions below

2.1 What is the term for a person/group that has the intention to perform malicious actions against cyber resources?

Answer: Adversary Operator

2.2 What is the term of the person or a group that will receive the benefits from the cyberattacks?

Answer: Adversary Customer

Task 3 Victim
Victim — is a target of the adversary. A victim can be an organization, person, target email address, IP address, domain, etc. It’s essential to understand the difference between the victim persona and the victim assets because they serve different analytic functions.

A victim can be an opportunity for the attackers to get a foothold on the organization they are trying to attack. There is always a victim in every cyberattack. For example, the spear-phishing email (a well-crafted email targeting a specific person of interest) was sent to the company, and someone (victim) clicked on the link. In this case, the victim is the selected target of interest for an adversary.

Victim Personae are the people and organizations being targeted and whose assets are being attacked and exploited. These can be organization names, people’s names, industries, job roles, interests, etc.

Victim Assets are the attack surface and include the set of systems, networks, email addresses, hosts, IP addresses, social networking accounts, etc., to which the adversary will direct their capabilities.

Answer the questions below

3.1 What is the term that applies to the Diamond Model for organizations or people that are being targeted?

Answer: Victim Personae

Task 4 Capability
Capability — is also known as the skill, tools, and techniques used by the adversary in the event. The capability highlights the adversary’s tactics, techniques, and procedures (TTPs).

The capability can include all techniques used to attack the victims, from the less sophisticated methods, such as manual password guessing, to the most sophisticated techniques, like developing malware or a malicious tool.

Capability Capacity is all of the vulnerabilities and exposures that the individual capability can use.

An Adversary Arsenal is a set of capabilities that belong to an adversary. The combined capacities of an adversary’s capabilities make it the adversary’s arsenal.

An adversary must have the required capabilities. The capabilities can be malware and phishing email development skills or, at least, access to capabilities, such as acquiring malware or ransomware as a service.

Answer the questions below

Provide the term for the set of tools or capabilities that belong to an adversary.

Answer: Adversary Arsenal

Task 5 Infrastructure
Infrastructure — is also known as software or hardware. Infrastructure is the physical or logical interconnections that the adversary uses to deliver a capability or maintain control of capabilities. For example, a command and control centre (C2) and the results from the victim (data exfiltration).

The infrastructure can also be IP addresses, domain names, email addresses, or even a malicious USB device found in the street that is being plugged into a workstation.

Type 1 Infrastructure is the infrastructure controlled or owned by the adversary.

Type 2 Infrastructure is the infrastructure controlled by an intermediary. Sometimes the intermediary might or might not be aware of it. This is the infrastructure that a victim will see as the adversary. Type 2 Infrastructure has the purpose of obfuscating the source and attribution of the activity. Type 2 Infrastructure includes malware staging servers, malicious domain names, compromised email accounts, etc.

Service Providers are organizations that provide services considered critical for the adversary availability of Type 1 and Type 2 Infrastructures, for example, Internet Service Providers, domain registrars, and webmail providers.

Answer the questions below

5.1 To which type of infrastructure do malicious domains and compromised email accounts belong?

Answer: Type 2 Infrastructure

5.2 What type of infrastructure is most likely owned by an adversary?

Answer: Type 1 Infrastructure

Task 6 Event Meta Features
<img width="801" height="508" alt="Screenshot 2025-08-26 at 9 36 42 PM" src="https://github.com/user-attachments/assets/fe95e109-55da-4d91-965d-6bff23b3f89a" />
Six possible meta-features can be added to the Diamond Model. Meta-features are not required, but they can add some valuable information or intelligence to the Diamond Model.

Timestamp — is the date and time of the event. Each event can be recorded with a date and time that it occurred, such as 2021–09–12 02:10:12.136. The timestamp can include when the event started and stopped. Timestamps are essential to help determine the patterns and group the malicious activity. For example, if the intrusion or breach happened at 3 am in the United States, it might be possible that the attack was carried out from a specific country with a different time zone and standard business hours.
Phase — these are the phases of an intrusion, attack, or breach. According to the Diamond Model creators and the Axiom 4, “Every malicious activity contains two or more phases which must be successfully executed in succession to achieve the desired result.” Malicious activities do not occur as single events, but rather as a sequence of events. A great example can be the Cyber Kill Chain developed by Lockheed Martin. You can find out more about the Cyber Kill Chain by visiting the Cyber Kill Chain room on TryHackMe
The phases can be:
1. Reconnaissance
2. Weaponization
3. Delivery
4. Exploitation
5. Installation
6. Command & Control
7. Actions on Objective
For example, an attacker needs to do some research to discover the target or a victim. Then they would try to exploit the target, establish a command-and-control centre and, lastly, exfiltrate the sensitive information.
Result — While the results and post-conditions of an adversary’s operations will not always be known or have a high confidence value when they are known, they are helpful to capture. It is crucial to capture the results and post-conditions of an adversary’s operations, but sometimes they might not always be known. The event results can be labelled as “success,” “failure,” or “unknown.” The event results can also be related to the CIA (confidentiality, integrity, and availability) triad, such as Confidentiality Compromised, Integrity Compromised, and Availability Compromised. Another approach can also be documenting all of the post-conditions resulting from the event, for example, information gathered in the reconnaissance stage or successful passwords/sensitive data exfiltration.
Direction — This meta-feature helps describe host-based and network-based events and represents the direction of the intrusion attack. The Diamond Model of Intrusion Analysis defines seven potential values for this meta-feature: Victim-to-Infrastructure, Infrastructure-to-Victim, Infrastructure-to-Infrastructure, Adversary-to-Infrastructure, Infrastructure-to-Adversary, Bidirectional or Unknown.
Methodology — This meta-feature will allow an analyst to describe the general classification of intrusion, for example, phishing, DDoS, breach, port scan, etc.
Resources — According to the Diamond Model, every intrusion event needs one or more external resources to be satisfied to succeed. Examples of the resources can include the following: software (e.g., operating systems, virtualization software, or Metasploit framework), knowledge (e.g., how to use Metasploit to execute the attack and run the exploit), information (e.g., a username/password to masquerade), hardware (e.g., servers, workstations, routers), funds (e.g., money to purchase domains), facilities (e.g., electricity or shelter), access (e.g., a network path from the source host to the victim and vice versa, network access from an Internet Service Provider (ISP)).
Answer the questions below

6.1 What meta-feature does the axiom “Every malicious activity contains two or more phases which must be successfully executed in succession to achieve the desired result” belong to?

Answer: Phase

6.2 You can label the event results as “success”, “failure”, and “unknown”. What meta-feature is this related to?

Answer: Result

6.3 To what meta-feature is this phrase applicable “Every intrusion event requires one or more external resources to be satisfied prior to success”?

Answer: Resources

Task 7 Social-Political Component
The social-political component describes the needs and intent of the adversary, for example, financial gain, gaining acceptance in the hacker community, hacktivism, or espionage.

The scenario can be that the victim provides a “product”, for example, computing resources & bandwidth as a zombie in a botnet for crypto mining (producing new cryptocurrencies by solving cryptographic equations through the use of computers) purposes, while the adversary consumes their product or gets financial gain.

Answer the questions below

Read the above.

Task 8 Technology Component
Technology — the technology meta-feature or component highlights the relationship between the core features: capability and infrastructure. The capability and infrastructure describe how the adversary operates and communicates. A scenario can be a watering-hole attack which is a methodology where the adversary compromises legitimate websites that they believe their targeted victims will visit.

Answer the questions below

Read the above.

Task 9 Practice Analysis
Are you ready to construct the Diamond Model? Please, deploy the static site attached to this task and dive into the case study and extract the information needed to populate our Diamond Model.

(Please note: The case study for this room occurred in 2015, and is not in light of recent developments in Ukraine).

Answer the questions below

9.1 Ensure you have deployed the static site attached to this task. To complete the static site, you will need to click on each triangular section of the diamond until you have completed all eight areas of the diamond

Complete all eight areas of the diamond. What is the flag that is displayed to you?
<img width="585" height="534" alt="Screenshot 2025-08-26 at 9 36 54 PM" src="https://github.com/user-attachments/assets/dca83328-5ea7-43a1-88af-43dd27daa9d8" />
<img width="466" height="385" alt="Screenshot 2025-08-26 at 9 37 01 PM" src="https://github.com/user-attachments/assets/f2707f30-78f9-4cce-a80f-8cc643a17a22" />
<img width="957" height="738" alt="Screenshot 2025-08-26 at 9 37 11 PM" src="https://github.com/user-attachments/assets/94b02d26-44f4-4893-9be4-5ca6d59db2e5" />
<img width="1052" height="566" alt="Screenshot 2025-08-26 at 9 37 20 PM" src="https://github.com/user-attachments/assets/3b2984fc-ab27-44ca-8087-f31f40401740" />
<img width="607" height="634" alt="Screenshot 2025-08-26 at 9 37 27 PM" src="https://github.com/user-attachments/assets/6c0fd640-178f-472c-ba9e-7e119a9696b1" />
<img width="780" height="621" alt="Screenshot 2025-08-26 at 9 37 35 PM" src="https://github.com/user-attachments/assets/43e78182-07b1-4891-bcc0-85dba62ac105" />
<img width="660" height="633" alt="Screenshot 2025-08-26 at 9 37 43 PM" src="https://github.com/user-attachments/assets/d475aa47-d2d3-4d0d-a580-6d9991dfda0f" />
<img width="899" height="636" alt="Screenshot 2025-08-26 at 9 55 41 PM" src="https://github.com/user-attachments/assets/b7703a1f-ea2a-4b2a-adbc-f9f0063d74a2" />
<img width="887" height="651" alt="Screenshot 2025-08-26 at 9 55 49 PM" src="https://github.com/user-attachments/assets/b3583728-d947-459b-b701-683eb0ac93af" />
<img width="774" height="321" alt="Screenshot 2025-08-26 at 9 55 55 PM" src="https://github.com/user-attachments/assets/88332482-2dba-4e4a-9e7c-32cc6d00ab8c" />
Answer: THM{DIAMOND_MODEL_ATTACK_CHAIN}

---
Conclusion

I found the Diamond Model room extremely informative and practical for understanding cyber intrusion analysis. The structured approach of the model—breaking down an attack into Adversary, Victim, Capability, and Infrastructure, along with meta-features like Phase, Result, and Resources—makes it easier to analyze attacks systematically.

I particularly appreciated how the model allows you to explain complex cyber incidents to non-technical audiences, which is crucial when communicating with executives or clients. The inclusion of Social-Political and Technology components also helps to understand the motives and methods of adversaries, giving a more complete picture of a threat.

Working through the practice exercise and completing the Diamond Model for the case study helped me apply theory to a real scenario, which reinforced my understanding. Overall, this room improved my ability to think like a threat hunter and strengthened my skills in intrusion analysis, threat intelligence, and incident response.

I would definitely use the Diamond Model in real-world cybersecurity operations, as it provides a clear, methodical way to identify, analyze, and communicate about cyber threats, and it would be a valuable addition to my professional toolkit.









