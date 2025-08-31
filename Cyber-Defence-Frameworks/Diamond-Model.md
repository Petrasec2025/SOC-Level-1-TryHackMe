TryHackMe Diamond Model Room
Learn about the four core features of the Diamond Model of Intrusion Analysis: adversary, infrastructure, capability, and victim.

Task 1 Introduction
What is The Diamond Model?

The Diamond Model of Intrusion Analysis was developed by cybersecurity professionals — Sergio Caltagirone, Andrew Pendergast, and Christopher Betz in 2013.

As described by its creators, the Diamond Model is composed of four core features: adversary, infrastructure, capability, and victim, and establishes the fundamental atomic element of any intrusion activity. You might have also noticed two additional components or axes of the Diamond Model — Social, Political and Technology; we will go into a little bit more detail about them later in this room. Why is it called a “Diamond Model”? The four core features are edge-connected, representing their underlying relationships and arranged in the shape of a diamond.

The Diamond Model carries the essential concepts of intrusion analysis and adversary operations while allowing the flexibility to expand and encompass new ideas and concepts. The model provides various opportunities to integrate intelligence in real-time for network defence, automating correlation across events, classifying events with confidence into adversary campaigns, and forecasting adversary operations while planning and gaming mitigation strategies.
<img width="897" height="521" alt="Screenshot 2025-08-31 at 9 14 55 PM" src="https://github.com/user-attachments/assets/916b4f2d-7915-46db-af31-465033364f21" />
Why should you learn about The Diamond Model?

The Diamond Model can help you identify the elements of an intrusion. At the end of this room, you will create a Diamond Model for events such as a breach, intrusion, attack, or incident. You will also be able to analyze an Advanced Persistent Threat (APT).

The Diamond Model can also help explain to other people who are non-technical about what happened during an event or any valuable information on the malicious threat actor.

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
Since the answers can be found above, I won’t be sharing them here. You can follow along so that you can find them.

What is the term for a person/group that has the intention to perform malicious actions against cyber resources?
At the end of this task is two terms, the answer is the top term. Once you find it, highlight & copy (ctrl +c ) or type the answer into the TryHackMe answer field, then click submit.
<img width="700" height="78" alt="Screenshot 2025-08-31 at 9 18 09 PM" src="https://github.com/user-attachments/assets/7e5f74b5-e6e6-4766-a170-c71e9aa3c2f0" />
What is the term of the person or a group that will receive the benefits from the cyberattacks?
At the end of this task is two terms, the answer is the second term. Once you find it, highlight & copy (ctrl +c ) or type the answer into the TryHackMe answer field, then click submit.
<img width="706" height="63" alt="Screenshot 2025-08-31 at 9 18 21 PM" src="https://github.com/user-attachments/assets/d3808a27-3cb5-468a-812f-367757266dab" />
Task 3 Victim
Victim — is a target of the adversary. A victim can be an organization, person, target email address, IP address, domain, etc. It’s essential to understand the difference between the victim persona and the victim assets because they serve different analytic functions.

A victim can be an opportunity for the attackers to get a foothold on the organization they are trying to attack. There is always a victim in every cyberattack. For example, the spear-phishing email (a well-crafted email targeting a specific person of interest) was sent to the company, and someone (victim) clicked on the link. In this case, the victim is the selected target of interest for an adversary.

Victim Personae are the people and organizations being targeted and whose assets are being attacked and exploited. These can be organization names, people’s names, industries, job roles, interests, etc.

Victim Assets are the attack surface and include the set of systems, networks, email addresses, hosts, IP addresses, social networking accounts, etc., to which the adversary will direct their capabilities.

You have finished up this task, you can now move onto

Answer the questions below
Since the answer can be found above, I won’t be sharing them here. You can follow along so that you can find them.

What is the term that applies to the Diamond Model for organizations or people that are being targeted?
At the end of this task is two terms, the answer is the top term. Once you find it, highlight & copy (ctrl +c ) or type the answer into the TryHackMe answer field, then click submit.
<img width="690" height="48" alt="Screenshot 2025-08-31 at 9 19 32 PM" src="https://github.com/user-attachments/assets/901f11cb-3872-4c73-81ee-9a323d4160a4" />
Task 4 Capability
Capability — is also known as the skill, tools, and techniques used by the adversary in the event. The capability highlights the adversary’s tactics, techniques, and procedures (TTPs).

The capability can include all techniques used to attack the victims, from the less sophisticated methods, such as manual password guessing, to the most sophisticated techniques, like developing malware or a malicious tool.

Capability Capacity is all of the vulnerabilities and exposures that the individual capability can use.

An Adversary Arsenal is a set of capabilities that belong to an adversary. The combined capacities of an adversary’s capabilities make it the adversary’s arsenal.

An adversary must have the required capabilities. The capabilities can be malware and phishing email development skills or, at least, access to capabilities, such as acquiring malware or ransomware as a service.

Answer the questions below
Since the answer can be found above, I won’t be sharing them here. You can follow along so that you can find them.

Provide the term for the set of tools or capabilities that belong to an adversary.
At the end of this task is two terms, the answer is the second term. Once you find it, highlight & copy (ctrl +c ) or type the answer into the TryHackMe answer field, then click submit.
<img width="705" height="43" alt="Screenshot 2025-08-31 at 9 19 40 PM" src="https://github.com/user-attachments/assets/2ea36298-37f0-46ef-991b-2d38b9b7bfc6" />
Task 5 Infrastructure
Infrastructure — is also known as software or hardware. Infrastructure is the physical or logical interconnections that the adversary uses to deliver a capability or maintain control of capabilities. For example, a command and control centre (C2) and the results from the victim (data exfiltration).

The infrastructure can also be IP addresses, domain names, email addresses, or even a malicious USB device found in the street that is being plugged into a workstation.

Type 1 Infrastructure is the infrastructure controlled or owned by the adversary.

Type 2 Infrastructure is the infrastructure controlled by an intermediary. Sometimes the intermediary might or might not be aware of it. This is the infrastructure that a victim will see as the adversary. Type 2 Infrastructure has the purpose of obfuscating the source and attribution of the activity. Type 2 Infrastructure includes malware staging servers, malicious domain names, compromised email accounts, etc.

Service Providers are organizations that provide services considered critical for the adversary availability of Type 1 and Type 2 Infrastructures, for example, Internet Service Providers, domain registrars, and webmail providers.

Answer the questions below
Since the answers can be found above, I won’t be sharing them here. You can follow along so that you can find them.

To which type of infrastructure do malicious domains and compromised email accounts belong?
At the end of this task is three terms, the answer is the second term. Once you find it, highlight & copy (ctrl +c ) or type the answer into the TryHackMe answer field, then click submit.

<img width="713" height="75" alt="Screenshot 2025-08-31 at 9 21 06 PM" src="https://github.com/user-attachments/assets/165ebe4a-b859-4961-a862-1c4a4ee48229" />
What type of infrastructure is most likely owned by an adversary?
At the end of this task is three terms, the answer is the first term. Once you find it, highlight & copy (ctrl +c ) or type the answer into the TryHackMe answer field, then click submit.

Press enter or click to view image in full size
<img width="670" height="58" alt="Screenshot 2025-08-31 at 9 21 13 PM" src="https://github.com/user-attachments/assets/9def6479-b637-449c-978b-e9326931ab63" />
Task 6 Event Meta Features
Six possible meta-features can be added to the Diamond Model. Meta-features are not required, but they can add some valuable information or intelligence to the Diamond Model.

Timestamp — is the date and time of the event. Each event can be recorded with a date and time that it occurred, such as 2021–09–12 02:10:12.136. The timestamp can include when the event started and stopped. Timestamps are essential to help determine the patterns and group the malicious activity. For example, if the intrusion or breach happened at 3 am in the United States, it might be possible that the attack was carried out from a specific country with a different time zone and standard business hours.
Phase — these are the phases of an intrusion, attack, or breach. According to the Diamond Model creators and the Axiom 4, “Every malicious activity contains two or more phases which must be successfully executed in succession to achieve the desired result.” Malicious activities don’t occur in two or more events rather than just one. A great example can be the Cyber Kill Chain developed by Lockheed Martin. You can find out more about the Cyber Kill Chain by visiting the Cyber Kill Chain room on TryHackMe
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
Since the answers can be found above, I won’t be sharing them here. You can follow along so that you can find them.

What meta-feature does the axiom “Every malicious activity contains two or more phases which must be successfully executed in succession to achieve the desired result” belong to?
This answer can be found at the second bullet point above. Once you find it, highlight & copy (ctrl +c ) or type the answer into the TryHackMe answer field, then click submit.

Press enter or click to view image in full size
<img width="717" height="85" alt="Screenshot 2025-08-31 at 9 22 47 PM" src="https://github.com/user-attachments/assets/21964c81-0341-4570-924d-1fe394201491" />
You can label the event results as “success”, “failure”, and “unknown”. What meta-feature is this related to?
This answer can be found at the third bullet point above. Once you find it, highlight & copy (ctrl +c ) or type the answer into the TryHackMe answer field, then click submit.

Press enter or click to view image in full size
<img width="723" height="124" alt="Screenshot 2025-08-31 at 9 22 59 PM" src="https://github.com/user-attachments/assets/ab42ff9b-52de-4e45-be1d-742902f565ed" />
To what meta-feature is this phrase applicable “Every intrusion event requires one or more external resources to be satisfied prior to success”?
This answer can be found at the final bullet point above. Once you find it, highlight & copy (ctrl +c ) or type the answer into the TryHackMe answer field, then click submit.
<img width="726" height="101" alt="Screenshot 2025-08-31 at 9 24 35 PM" src="https://github.com/user-attachments/assets/42750086-1277-4738-8beb-e4fa8eedac5c" />
Task 7 Social-Political Component
The social-political component describes the needs and intent of the adversary, for example, financial gain, gaining acceptance in the hacker community, hacktivism, or espionage.

The scenario can be that the victim provides a “product”, for example, computing resources & bandwidth as a zombie in a botnet for crypto mining (producing new cryptocurrencies by solving cryptographic equations through the use of computers) purposes, while the adversary consumes their product or gets financial gain.

Task 8 Technology Component
Technology — the technology meta-feature or component highlights the relationship between the core features: capability and infrastructure. The capability and infrastructure describe how the adversary operates and communicates. A scenario can be a watering-hole attack which is a methodology where the adversary compromises legitimate websites that they believe their targeted victims will visit.

Task 9 Practice Analysis
Are you ready to construct the Diamond Model? Please, deploy the static site attached to this task and dive into the case study and extract the information needed to populate our Diamond Model.

(Please note: The case study for this room occurred in 2015, and is not in light of recent developments in Ukraine).

Answer the questions below
Ensure you have deployed the static site attached to this task. To complete the static site, you will need to click on each triangular section of the diamond until you have completed all eight areas of the diamond

Getting Started
To get started with this practical you will need to start the static site. Click the green button labeled View site for the static site.
<img width="697" height="138" alt="Screenshot 2025-08-31 at 9 26 30 PM" src="https://github.com/user-attachments/assets/2ca562b0-1354-44b6-843b-e0694ff1f811" />
The screen will split in half and on the right side will be the Diamond Model, you will click on each piece then will be asked a question. Once all questions are answered you will get the flag. I will be starting with the five triangles at the top, then the three at the bottom, in a left to right order. I have labeled each piece with a number to go along with the number question below.


<img width="679" height="664" alt="Screenshot 2025-08-31 at 9 26 37 PM" src="https://github.com/user-attachments/assets/64567284-6fc8-435d-9939-db8e4dd45533" />

1. The incident response team has determined that a group of notorious underground hackers named APT2166 are responsible for the attack.
<img width="586" height="545" alt="Screenshot 2025-08-31 at 9 27 45 PM" src="https://github.com/user-attachments/assets/93d20a1d-775e-4cc6-9dc3-3d8a7f63e55b" />
We learned about this back in Task 2 Adversary.

Press enter or click to view image in full size

Answer: Adversary

2. The attack occurred on 2021–10–23 at 15:45:00:00.000.
   <img width="595" height="492" alt="Screenshot 2025-08-31 at 9 28 33 PM" src="https://github.com/user-attachments/assets/56f652e7-0893-42af-9ccb-3e5748ead73c" />
   We learned about this back in Task 6 Event Meta Features, they use a different word but they both have the same meaning.
   <img width="638" height="176" alt="Screenshot 2025-08-31 at 9 28 42 PM" src="https://github.com/user-attachments/assets/83c16372-4499-4066-b568-65779ae12515" />
   Answer: Timeline

3. The attackers targeted the Information Technology (IT) systems of the corporation.
<img width="571" height="551" alt="Screenshot 2025-08-31 at 9 29 57 PM" src="https://github.com/user-attachments/assets/9bb8d0cc-acd9-4a44-90bf-840115bef02c" />
We learn about this back at Task 3 Victim.
<img width="669" height="78" alt="Screenshot 2025-08-31 at 9 30 04 PM" src="https://github.com/user-attachments/assets/9515dd46-df66-4f38-a769-a09c2b05194e" />
Answer: Victim

4. The attackers used a recent malware campaign known as OneTrick to ransomware the corporation’s servers.
<img width="591" height="525" alt="Screenshot 2025-08-31 at 9 31 28 PM" src="https://github.com/user-attachments/assets/8ec5c88b-a1c8-45bd-8c50-3b9cb32ab242" />
We learn about this back at Task 6 Event Meta Features.
<img width="651" height="239" alt="Screenshot 2025-08-31 at 9 31 34 PM" src="https://github.com/user-attachments/assets/9573cb58-0213-4c4c-b0b8-aa4f4542e5e2" />
Answer: Resources
5. The attackers stole data from the corporation and sold it on an underground hacking forum.

<img width="585" height="527" alt="Screenshot 2025-08-31 at 9 32 51 PM" src="https://github.com/user-attachments/assets/65298afb-6b36-4ce1-982b-be88c8c24cf7" />

We learn about this back at Task 6 Event Meta Features.


<img width="606" height="227" alt="Screenshot 2025-08-31 at 9 32 58 PM" src="https://github.com/user-attachments/assets/304a3a93-849b-4d92-92e0-9e482f9b0c3d" />

Answer: Result

6. The attackers gained access using legitimate credentials that were gained as a result of a phishing attack.
<img width="598" height="529" alt="Screenshot 2025-08-31 at 9 36 50 PM" src="https://github.com/user-attachments/assets/b70759a8-b808-4e1b-8f22-17f19295c06e" />
We learn about this back at Task 4 Capability.
<img width="679" height="63" alt="Screenshot 2025-08-31 at 9 36 59 PM" src="https://github.com/user-attachments/assets/324ab80d-379f-46f2-b6ba-fca3b27e84b5" />
Answer: Capability

7. Once the attackers gained access to the network, they pivoted to the internal databases and file shares.

<img width="609" height="532" alt="Screenshot 2025-08-31 at 9 38 02 PM" src="https://github.com/user-attachments/assets/d69d7a7d-966d-43e8-bfa7-6bae59cc0804" />


We learn about this back at Task 6 Event Meta Features.
<img width="706" height="88" alt="Screenshot 2025-08-31 at 9 38 10 PM" src="https://github.com/user-attachments/assets/4b00c1b5-7051-485e-b610-561dee4618a4" />
Answer: Methodology

8. The attacker’s steps can be followed using the phases of what Cyber Kill Chain model?
   <img width="596" height="499" alt="Screenshot 2025-08-31 at 9 39 38 PM" src="https://github.com/user-attachments/assets/d5769e3c-0092-4d68-ab57-485dee625583" />
   We learn about this back at Task 6 Event Meta Features.
   <img width="698" height="379" alt="Screenshot 2025-08-31 at 9 39 51 PM" src="https://github.com/user-attachments/assets/0769f8b2-1ab4-483b-bae2-4709e5d4089e" />
   Answer: Lockheed Martin’s Cyber Kill Chain

Complete all eight areas of the diamond. What is the flag that is displayed to you?
Once you have answered all the questions you will be presented with the flag.
<img width="560" height="116" alt="Screenshot 2025-08-31 at 9 41 03 PM" src="https://github.com/user-attachments/assets/b114fd6f-8d9d-47eb-a47b-929e1b42a12c" />
highlight & copy (ctrl + c ) then paste (ctrl + v ) into the TryHackMe answer field, then click submit.
Task 10 Conclusion
I successfully completed the Diamond Model Room, where I learned how to apply the Diamond Model concepts in disrupting threat activity and communicating valuable insights to both technical teams and non-technical audiences, including business executives (C-Suite) and clients. The Diamond Model has strengthened my ability to conduct intrusion analysis with improved efficiency and accuracy, while also enabling me to leverage real-time intelligence for network defense and anticipate adversary operations.

🎉 I’m proud to have completed this milestone and added the Diamond Model methodology to my cybersecurity toolkit.






