
<img width="1338" height="265" alt="Screenshot 2025-09-06 at 5 48 43 PM" src="https://github.com/user-attachments/assets/fcb9d406-f042-4c65-83a0-7242e7abb86c" />

Task 1 Introduction
Introduction

This room will introduce you to cyber threat intelligence (CTI) and various frameworks used to share intelligence. As security analysts, CTI is vital for investigating and reporting against adversary attacks with organisational stakeholders and external communities.

Learning Objectives

The basics of CTI and its various classifications.
The lifecycle followed to deploy and use intelligence during threat investigations.
Frameworks and standards used in distributing intelligence.
Cyber Threat Intelligence Module

This is the first room in a new Cyber Threat Intelligence module. The module will also contain:

Threat Intelligence Tools
YARA
OpenCTI
MISP
---
Task 2 Cyber Threat Intelligence
Cyber Threat Intelligence (CTI) can be defined as evidence-based knowledge about adversaries, including their indicators, tactics, motivations, and actionable advice against them. These can be utilised to protect critical assets and inform cybersecurity teams and management business decisions.

It would be typical to use the terms “data”, “information”, and “intelligence” interchangeably. However, let us distinguish between them to understand better how CTI comes into play.

Press enter or click to view image in full size

<img width="490" height="454" alt="Screenshot 2025-09-06 at 5 46 59 PM" src="https://github.com/user-attachments/assets/f77d36fb-cc6c-4a44-a0c8-fc7237cdfd75" />
---
Data: Discrete indicators associated with an adversary such as IP addresses, URLs or hashes.

Information: A combination of multiple data points that answer questions such as “How many times have employees accessed tryhackme.com within the month?”

Intelligence: The correlation of data and information to extract patterns of actions based on contextual analysis.

The primary goal of CTI is to understand the relationship between your operational environment and your adversary and how to defend your environment against any attacks. You would seek this goal by developing your cyber threat context by trying to answer the following questions:

Who’s attacking you?
What are their motivations?
What are their capabilities?
What artefacts and indicators of compromise (IOCs) should you look out for?
With these questions, threat intelligence would be gathered from different sources under the following categories:

Internal:

Corporate security events such as vulnerability assessments and incident response reports.
Cyber awareness training reports.
System logs and events.
Community:

Open web forums.
Dark web communities for cybercriminals.
External

Threat intel feeds (Commercial & Open-source)
Online marketplaces.
Public sources include government data, publications, social media, financial and industrial assessments.
Threat Intelligence Classifications:
Threat Intel is geared towards understanding the relationship between your operational environment and your adversary. With this in mind, we can break down threat intel into the following classifications:
<img width="595" height="588" alt="Screenshot 2025-09-06 at 5 49 58 PM" src="https://github.com/user-attachments/assets/19d22193-5681-4d20-9784-ba644ba1c501" />

Strategic Intel: High-level intel that looks into the organisation’s threat landscape and maps out the risk areas based on trends, patterns and emerging threats that may impact business decisions.
Technical Intel: Looks into evidence and artefacts of attack used by an adversary. Incident Response teams can use this intel to create a baseline attack surface to analyse and develop defence mechanisms.
Tactical Intel: Assesses adversaries’ tactics, techniques, and procedures (TTPs). This intel can strengthen security controls and address vulnerabilities through real-time investigations.
Operational Intel: Looks into an adversary’s specific motives and intent to perform an attack. Security teams may use this intel to understand the critical assets available in the organisation (people, processes and technologies) that may be targeted.
Answer the questions below
Since the answer can be found about, it won’t be posted here. Follow along so that if you aren’t sure of the answer you know where to find it.

What does CTI stand for?
The answer can be found in the first sentence of this task. Once you find it, highlight then copy (ctrl + c ) and paste (ctrl +v ) or type, the answer into TryHackMe Answer field, then click submit.

<img width="710" height="66" alt="Screenshot 2025-09-06 at 5 50 55 PM" src="https://github.com/user-attachments/assets/7331e291-f3dd-4fa5-a040-4b9da5b95901" />
IP addresses, Hashes and other threat artefacts would be found under which Threat Intelligence classification?
The answer can be found in the Threat Intelligence Classification section, it is the second bullet point. Once you find it, highlight then copy (ctrl + c ) and paste (ctrl +v ) or type, the answer into TryHackMe Answer field, then click submit.
<img width="666" height="119" alt="Screenshot 2025-09-06 at 5 51 14 PM" src="https://github.com/user-attachments/assets/1c5b4606-aaa5-4411-83fa-e3b8791d04d5" />
Task 3 CTI Lifecycle
Threat intel is obtained from a data-churning process that transforms raw data into contextualised and action-oriented insights geared towards triaging security incidents. The transformational process follows a six-phase cycle:
<img width="980" height="621" alt="Screenshot 2025-09-06 at 5 52 34 PM" src="https://github.com/user-attachments/assets/09ec21e6-abb0-47f9-ba35-a404e270a5c0" />
Direction
Every threat intel program requires to have objectives and goals defined, involving identifying the following parameters:

Information assets and business processes that require defending.
Potential impact to be experienced on losing the assets or through process interruptions.
Sources of data and intel to be used towards protection.
Tools and resources that are required to defend the assets.
This phase also allows security analysts to pose questions related to investigating incidents.

Collection
Once objectives have been defined, security analysts will gather the required data to address them. Analysts will do this by using commercial, private and open-source resources available. Due to the volume of data analysts usually face, it is recommended to automate this phase to provide time for triaging incidents.

Processing
Raw logs, vulnerability information, malware and network traffic usually come in different formats and may be disconnected when used to investigate an incident. This phase ensures that the data is extracted, sorted, organised, correlated with appropriate tags and presented visually in a usable and understandable format to the analysts. SIEMs are valuable tools for achieving this and allow quick parsing of data.

Analysis
Once the information aggregation is complete, security analysts must derive insights. Decisions to be made may involve:

Investigating a potential threat through uncovering indicators and attack patterns.
Defining an action plan to avert an attack and defend the infrastructure.
Strengthening security controls or justifying investment for additional resources.
Dissemination
Different organisational stakeholders will consume the intelligence in varying languages and formats. For example, C-suite members will require a concise report covering trends in adversary activities, financial implications and strategic recommendations. At the same time, analysts will more likely inform the technical team about the threat IOCs, adversary TTPs and tactical action plans.

Feedback
The final phase covers the most crucial part, as analysts rely on the responses provided by stakeholders to improve the threat intelligence process and implementation of security controls. Feedback should be regular interaction between teams to keep the lifecycle working.

Answer the questions below
Since the answer can be found about, it won’t be posted here. Follow along so that if you aren’t sure of the answer you know where to find it.

At which phase of the lifecycle is data made usable through sorting, organising, correlation and presentation?
This is the third step of the CTI Process Feedback Loop. Once you find it, highlight then copy (ctrl + c ) and paste (ctrl +v ) or type, the answer into TryHackMe Answer field, then click submit.
<img width="720" height="113" alt="Screenshot 2025-09-06 at 5 53 16 PM" src="https://github.com/user-attachments/assets/a59789e8-6689-429c-8658-944a214b8555" />
During which phase do security analysts get the chance to define the questions to investigate incidents?
This is the first step of the CTI Process Feedback Loop. Once you find it, highlight then copy (ctrl + c ) and paste (ctrl +v ) or type, the answer into TryHackMe Answer field, then click submit.
<img width="652" height="305" alt="Screenshot 2025-09-06 at 5 53 22 PM" src="https://github.com/user-attachments/assets/4298fa06-74b9-4f08-ac91-fd539c657349" />
Task 4 CTI Standards & Frameworks
Standards and frameworks provide structures to rationalise the distribution and use of threat intel across industries. They also allow for common terminology, which helps in collaboration and communication. Here, we briefly look at some essential standards and frameworks commonly used.

MITRE ATT&CK
The ATT&CK framework is a knowledge base of adversary behaviour, focusing on the indicators and tactics. Security analysts can use the information to be thorough while investigating and tracking adversarial behaviour.
<img width="690" height="379" alt="Screenshot 2025-09-06 at 5 53 30 PM" src="https://github.com/user-attachments/assets/b5722d57-4e4f-4805-8a22-499462b8c4a5" />
TAXII
The Trusted Automated eXchange of Indicator Information (TAXII) defines protocols for securely exchanging threat intel to have near real-time detection, prevention and mitigation of threats. The protocol supports two sharing models:

Collection: Threat intel is collected and hosted by a producer upon request by users using a request-response model.
Channel: Threat intel is pushed to users from a central server through a publish-subscribe model.
STIX
Structured Threat Information Expression (STIX) is a language developed for the “specification, capture, characterisation and communication of standardised cyber threat information”. It provides defined relationships between sets of threat info such as observables, indicators, adversary TTPs, attack campaigns, and more.

Cyber Kill Chain
Developed by Lockheed Martin, the Cyber Kill Chain breaks down adversary actions into steps. This breakdown helps analysts and defenders identify which stage-specific activities occurred when investigating an attack. The phases defined are shown in the image below.
<img width="990" height="381" alt="Screenshot 2025-09-06 at 5 55 02 PM" src="https://github.com/user-attachments/assets/2669c15e-323d-4346-baed-5770b5daab6b" />

TechniquePurposeExamplesReconnaissanceObtain information about the victim and the tactics used for the attack.Harvesting emails, OSINT, and social media, network scansWeaponisationMalware is engineered based on the needs and intentions of the attack.Exploit with backdoor, malicious office documentDeliveryCovers how the malware would be delivered to the victim’s system.Email, weblinks, USBExploitationBreach the victim’s system vulnerabilities to execute code and create scheduled jobs to establish persistence.
EternalBlue, Zero-Logon, etc.InstallationInstall malware and other tools to gain access to the victim’s system.Password dumping, backdoors, remote access trojansCommand & ControlRemotely control the compromised system, deliver additional malware, move across valuable assets and elevate privileges.Empire, Cobalt Strike, etc.Actions on ObjectivesFulfil the intended goals for the attack: financial gain, corporate espionage, and data exfiltration.Data encryption, ransomware, public defacement

Over time, the kill chain has been expanded using other frameworks such as ATT&CK and formulated a new Unified Kill Chain.

The Diamond Model
The diamond model looks at intrusion analysis and tracking attack groups over time. It focuses on four key areas, each representing a different point on the diamond. These are:

<img width="823" height="501" alt="Screenshot 2025-09-06 at 5 56 14 PM" src="https://github.com/user-attachments/assets/fca5808d-ca12-4bcf-880c-0bc8ed3d6e2f" />

Adversary: The focus here is on the threat actor behind an attack and allows analysts to identify the motive behind the attack.
Victim: The opposite end of adversary looks at an individual, group or organisation affected by an attack.
Infrastructure: The adversaries’ tools, systems, and software to conduct their attack are the main focus. Additionally, the victim’s systems would be crucial to providing information about the compromise.
Capabilities: The focus here is on the adversary’s approach to reaching its goal. This looks at the means of exploitation and the TTPs implemented across the attack timeline.
An example of the diamond model in play would involve an adversary targeting a victim using phishing attacks to obtain sensitive information and compromise their system, as displayed on the diagram. As a threat intelligence analyst, the model allows you to pivot along its properties to produce a complete picture of an attack and correlate indicators.

Answer the questions below
Since the answer can be found about, it won’t be posted here. Follow along so that if you aren’t sure of the answer you know where to find it.

What sharing models are supported by TAXII?
The answer is under the TAXII section, the answer is both bullet point with a and inbetween. Once you find it, highlight then copy (ctrl + c ) and paste (ctrl +v ) or type, the answer into TryHackMe Answer field, then click submit.

Press enter or click to view image in full size
<img width="700" height="127" alt="Screenshot 2025-09-06 at 5 57 53 PM" src="https://github.com/user-attachments/assets/c9933019-f6d8-4321-a71e-91ebf39977f7" />
When an adversary has obtained access to a network and is extracting data, what phase of the kill chain are they on?
This can be found under the Lockheed Martin Kill Chain section, it is the final link on the chain. Once you find it, highlight then copy (ctrl + c ) and paste (ctrl +v ) or type, the answer into TryHackMe Answer field, then click submit.

<img width="679" height="316" alt="Screenshot 2025-09-06 at 5 56 26 PM" src="https://github.com/user-attachments/assets/7312ee7c-8366-4b44-8c71-cc4a49c74349" />

Task 5 Practical Analysis
As part of the dissemination phase of the lifecycle, CTI is also distributed to organisations using published threat reports. These reports come from technology and security companies that research emerging and actively used threat vectors. They are valuable for consolidating information presented to all suitable stakeholders. Some notable threat reports come from Mandiant, Recorded Future and AT&TCybersecurity.

All the things we have discussed come together when mapping out an adversary based on threat intel. To better understand this, we will analyse a simplified engagement example. Click on the green “View Site” button in this task to open the Static Site Lab and navigate through the security monitoring tool on the right panel and fill in the threat details.

Answer the questions below
Start off by opening the static site by clicking the green View Site Button. This will split the screen in half and on the right side of the screen will be the practical side with the information needed to answer the question.

Press enter or click to view image in full size
<img width="708" height="321" alt="Screenshot 2025-09-06 at 5 56 47 PM" src="https://github.com/user-attachments/assets/2e4c88e3-0357-463e-8af4-6e4e0afb1be2" />
What was the source email address?
Looking down through Alert logs we can see that an email was received by John Doe. The email address that is at the end of this alert is the email address that question is asking for. Once you find it, highlight then copy (ctrl + c ) and paste (ctrl +v ) or type, the answer into TryHackMe Answer field, then click submit.
<img width="671" height="689" alt="Screenshot 2025-09-06 at 5 59 58 PM" src="https://github.com/user-attachments/assets/d5055128-cd33-4284-b3d5-ba1ae5698595" />
Answer: vipivillain@badbank.com

What was the name of the file downloaded?
Look at the Alert above the one from the previous question, it will say File download inititiated. At the end of this alert is the name of the file, this is the answer to this quesiton. Once you find it, highlight then copy (ctrl + c ) and paste (ctrl +v ) or type, the answer into TryHackMe Answer field, then click submit.
<img width="674" height="669" alt="Screenshot 2025-09-06 at 6 00 07 PM" src="https://github.com/user-attachments/assets/d42e3cb9-b52c-4962-a871-7035b8838530" />
Answer: flbpfuh.exe

After building the threat profile, what message do you receive?
For this section you will scroll down, and have five different questions to answer. The answers to these questions can be found in the Alert Logs above. The way I am going to go through these is, the three at the top then the two at the bottom. I have them numbered to better find them below.
<img width="674" height="566" alt="Screenshot 2025-09-06 at 6 00 16 PM" src="https://github.com/user-attachments/assets/9cff03f7-8dca-4c8e-88f2-86279b7b6106" />
1. What was the threat actor’s extraction IP address?
   <img width="386" height="119" alt="Screenshot 2025-09-06 at 6 00 22 PM" src="https://github.com/user-attachments/assets/828b79a4-f88c-4635-b87f-dfcda7e9ca53" />
   Looking at the Alert Logs we can see that we have Outbound and Internal traffic from a certain IP address that seem sus, this is the attackers IP address. Once you find it, highlight then copy (ctrl + c ) and paste (ctrl +v ) or type, the answer into answer field and click the blue Check Answer button.
   <img width="679" height="699" alt="Screenshot 2025-09-06 at 6 00 33 PM" src="https://github.com/user-attachments/assets/413f8a76-0276-4024-b1a3-ec110020f3ea" />
   Answer:

2. What was the threat actor’s email address?
<img width="387" height="121" alt="Screenshot 2025-09-06 at 6 00 41 PM" src="https://github.com/user-attachments/assets/30f55bb8-1589-43fe-a813-5033430ddf6c" />

We answer this question already with the first question of this task. Looking down through Alert logs we can see that an email was received by John Doe. The email address that is at the end of this alert is the email address that question is asking for. Once you find it, highlight then copy (ctrl + c ) and paste (ctrl +v ) or type, the answer into answer field and click the blue Check Answer button.

<img width="655" height="686" alt="Screenshot 2025-09-06 at 6 00 50 PM" src="https://github.com/user-attachments/assets/4bd5118f-ca9b-4bdb-a075-a986c9089af7" />

Answer: vipivillain@badbank.com

3. What software tool was used in the extraction?
<img width="383" height="112" alt="Screenshot 2025-09-06 at 6 00 57 PM" src="https://github.com/user-attachments/assets/37972dd1-c05f-4f16-8d85-fd298f3c4f1b" />
We answer this question already with the second question of this task. Look at the Alert above the one from the previous question, it will say File download inititiated. At the end of this alert is the name of the file, this is the answer to this quesiton. Once you find it, highlight then copy (ctrl + c ) and paste (ctrl +v ) or type, the answer into answer field and click the blue Check Answer button.
<img width="654" height="694" alt="Screenshot 2025-09-06 at 6 01 04 PM" src="https://github.com/user-attachments/assets/341e5889-9e9f-4dad-814b-62afdde8c4a5" />
Answer: flbpfuh.exe

4. What user account was logged in by the threat actor?
   <img width="384" height="125" alt="Screenshot 2025-09-06 at 6 01 11 PM" src="https://github.com/user-attachments/assets/877ec675-f6c3-4008-8e9b-5178b925de84" />

The Alert that this question is talking about is at the top of the Alert list. It states that an account was Logged on successfully. The account at the end of this Alert is the answer to this question. Once you find it, highlight then copy (ctrl + c ) and paste (ctrl +v ) or type, the answer into answer field and click the blue Check Answer button.
<img width="651" height="701" alt="Screenshot 2025-09-06 at 6 01 21 PM" src="https://github.com/user-attachments/assets/b1c8c95f-3b6c-4d88-a408-27f719c59d17" />

Answer: Administrator

5. Who was the targeted victim?
   <img width="402" height="128" alt="Screenshot 2025-09-06 at 6 01 26 PM" src="https://github.com/user-attachments/assets/b16a9d59-67c1-401c-b49e-ec5142e8929c" />
   On the Alert log we see a name come up a couple times, this person is the victim to the initite attack and the answer to this question. Once you find it, highlight then copy (ctrl + c ) and paste (ctrl +v ) or type, the answer into answer field and click the blue Check Answer button.
   <img width="676" height="702" alt="Screenshot 2025-09-06 at 6 01 34 PM" src="https://github.com/user-attachments/assets/12b074c9-2d4d-47bf-a76f-9fbba454868f" />
   Answer: John Doe

The Flag!!!!!!
Once you answer that last question, TryHackMe will give you the Flag.
<img width="322" height="86" alt="Screenshot 2025-09-06 at 6 01 41 PM" src="https://github.com/user-attachments/assets/67a457ad-5923-4307-ac73-13c5b526dfc2" />


Once you find it, highlight then copy (ctrl + c ) and paste (ctrl +v ) or type, the answer into TryHackMe Answer field, then click submit.

Answer: THM{NOW_I_CAN_CTI}

🎉🎉Congrats!!! You have completed the Intro to Cyber Threat Intel🎉🎉

