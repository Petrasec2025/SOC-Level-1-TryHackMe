TryHackMe Unified Kill Chain Room
---
The Unified Kill Chain is a framework which establishes the phases of an attack, and a means of identifying and mitigating risk to IT assets.

Task 1 Introduction
<img width="659" height="398" alt="Screenshot 2025-08-26 at 8 40 21 PM" src="https://github.com/user-attachments/assets/5c9c9d13-e95f-4c90-aea5-a3e75a66a709" />
Understanding the behaviours, objectives and methodologies of a cyber threat is a vital step to establishing a strong cybersecurity defence (known as a cybersecurity posture).

In this room, you will be introduced to the UKC (Unified Kill Chain) framework that is used to help understand how cyber attacks occur.

Learning Objectives:

Understanding why frameworks such as the UKC are important and helpful in establishing a good cybersecurity posture
Using the UKC to understand an attacker’s motivation, methodologies and tactics
Understanding the various phases of the UKC
Discover that the UKC is a framework that is used to complement other frameworks such as MITRE.
Task 2 What is a “Kill Chain”
<img width="402" height="350" alt="Screenshot 2025-08-26 at 8 41 36 PM" src="https://github.com/user-attachments/assets/32bf04a7-7324-472b-a5b4-0f9f4b69c013" />
Originating from the military, a “Kill Chain” is a term used to explain the various stages of an attack. In the realm of cybersecurity, a “Kill Chain” is used to describe the methodology/path attackers such as hackers or APTs use to approach and intrude a target.

For example, an attacker scanning, exploiting a web vulnerability, and escalating privileges will be a “Kill Chain”. We will come to explain these stages in much further detail later in this room.

The objective is to understand an attacker’s “Kill Chain” so that defensive measures can be put in place to either pre-emptively protect a system or disrupt an attacker’s attempt.

Answer the questions below
Where does the term “Kill Chain” originate from?
For this answer, you must fill in the blank!: The ********

Since the answers can be found above, I won’t be posting it. You can follow along to learn and discover where they are located.

The answer can be found in the first sentence of this task. Once you find it, highlight & copy (ctrl +c ) or type the answer into the TryHackMe answer field, then click submit.
<img width="710" height="88" alt="Screenshot 2025-08-26 at 8 42 10 PM" src="https://github.com/user-attachments/assets/96b78b4f-93c7-4474-b219-3267b8d3b8ce" />
Task 3 What is “Threat Modelling”
Threat modelling, in a cybersecurity context, is a series of steps to ultimately improve the security of a system. Threat modelling is about identifying risk and essentially boils down to:

Identifying what systems and applications need to be secured and what function they serve in the environment. For example, is the system critical to normal operations, and is a system holding sensitive information like payment info or addresses?
Assessing what vulnerabilities and weaknesses these systems and applications may have and how they could be potentially exploited
Creating a plan of action to secure these systems and applications from the vulnerabilities highlighted
Putting in policies to prevent these vulnerabilities from occurring again where possible (for example, implementing a software development life cycle (SDLC) for an application or training employees on phishing awareness).
<img width="357" height="439" alt="Screenshot 2025-08-26 at 8 42 50 PM" src="https://github.com/user-attachments/assets/b3967eed-302b-4a08-b38e-ab2092071256" />
Threat modelling is an important procedure in reducing the risk within a system or application, as it creates a high-level overview of an organisation’s IT assets (an asset in IT is a piece of software or hardware) and the procedures to resolve vulnerabilities.

The UKC can encourage threat modelling as the UKC framework helps identify potential attack surfaces and how these systems may be exploited.

STRIDE, DREAD and CVSS (to name a few) are all frameworks specifically used in threat modelling. If you are interested to learn more, check out the “Principles of Security” room on TryHackMe.

Answer the questions below
What is the technical term for a piece of software or hardware in IT (Information Technology?)

Since the answers can be found above, I won’t be posting it. You can follow along to learn and discover where they are located.

The answer can be found at the end of the sentence after the boiled down section. Once you find it, highlight & copy (ctrl +c ) or type the answer into the TryHackMe answer field, then click submit.
<img width="684" height="68" alt="Screenshot 2025-08-26 at 8 44 17 PM" src="https://github.com/user-attachments/assets/7f18bce3-715f-4359-bbf7-11a81215e133" />
Task 4 Introducing the Unified Kill Chain
<img width="684" height="377" alt="Screenshot 2025-08-26 at 8 44 24 PM" src="https://github.com/user-attachments/assets/12e775bf-1412-4be6-8383-72d311c8bf48" />
To continue from the previous task, the Unified Kill Chain published in 2017, aims to complement (not compete) with other cybersecurity kill chain frameworks such as Lockheed Martin’s and MITRE’s ATT&CK.

The UKC states that there are 18 phases to an attack: Everything from reconnaissance to data exfiltration and understanding an attacker’s motive. These phases have been grouped together in this room into a few areas of focus for brevity, which will be detailed in the remaining tasks.

Some large benefits of the UKC over traditional cybersecurity kill chain frameworks include the fact that it is modern and extremely detailed (reminder: it has 18 phases officially, whereas other frameworks may have a small handful)
<img width="690" height="451" alt="Screenshot 2025-08-26 at 8 44 34 PM" src="https://github.com/user-attachments/assets/a3463b7c-5e5d-41cf-a6d6-3813b6a57389" />
Benefits of the Unified Kill Chain (UKC) FrameworkHow do Other Frameworks Compare?Modern (released in 2017, updated in 2022).
Some frameworks, such as MITRE’s were released in 2013, when the cybersecurity landscape was very different.
The UKC is extremely detailed (18 phases).
Other frameworks often have a small handful of phases.
The UKC covers an entire attack — from reconnaissance, exploitation, post-exploitation and includes identifying an attacker’s motivation.
Other frameworks cover a limited amount of phases.
The UKC highlights a much more realistic attack scenario. Various stages will often re-occur. For example, after exploiting a machine, an attacker will begin reconnaissance to pivot another system.
Other frameworks do not account for the fact that an attacker will go back and forth between the various phases during an attack.

Answer the questions below
Since the answers can be found above, I won’t be posting it. You can follow along to learn and discover where they are located.

In what year was the Unified Kill Chain framework released?
The answer can be found in the first sentence of this task. Once you find it, highlight & copy (ctrl +c ) or type the answer into the TryHackMe answer field, then click submit.
<img width="713" height="61" alt="Screenshot 2025-08-26 at 8 46 40 PM" src="https://github.com/user-attachments/assets/38da0ba5-7c68-40c8-af4d-bf02b9c53cf7" />

According to the Unified Kill Chain, how many phases are there to an attack?
Count the number of “links” to the Unified kill chain, or see what at the bottom of the chart and see what the number is. Once you find it, highlight & copy (ctrl +c ) or type the answer into the TryHackMe answer field, then click submit.
<img width="667" height="423" alt="Screenshot 2025-08-26 at 8 46 50 PM" src="https://github.com/user-attachments/assets/344824a0-5499-469c-a285-ebf437189c90" />
What is the name of the attack phase where an attacker employs techniques to evade detection?
Going back up to the chart, the answer can be found at number 7. Once you find it, highlight & copy (ctrl +c ) or type the answer into the TryHackMe answer field, then click submit.
<img width="819" height="75" alt="Screenshot 2025-08-26 at 8 47 47 PM" src="https://github.com/user-attachments/assets/3c32a5ea-b3b8-467f-8571-47e8ad31de8a" />
What is the name of the attack phase where an attacker employs techniques to remove data from a network?
Going back up to the chart, the answer can be found at number 16. Once you find it, highlight & copy (ctrl +c ) or type the answer into the TryHackMe answer field, then click submit.
<img width="673" height="72" alt="Screenshot 2025-08-26 at 8 47 53 PM" src="https://github.com/user-attachments/assets/a66c704a-9a61-40bf-8518-4e7e651a6a54" />
What is the name of the attack phase where an attacker achieves their objectives?
Going back up to the chart, the answer can be found at number 18. Once you find it, highlight & copy (ctrl +c ) or type the answer into the TryHackMe answer field, then click submit.
<img width="795" height="92" alt="Screenshot 2025-08-26 at 8 50 11 PM" src="https://github.com/user-attachments/assets/70f815cc-13cc-437f-a98f-4c8a93f2889e" />


Task 5 Phase: In (Initial Foothold)
<img width="494" height="346" alt="Screenshot 2025-08-26 at 8 50 17 PM" src="https://github.com/user-attachments/assets/6015d836-09d3-4572-bcf4-23c19b95e626" />
The main focus of this series of phases is for an attacker to gain access to a system or networked environment.

An attacker will employ numerous tactics to investigate the system for potential vulnerabilities that can be exploited to gain a foothold in the system. For example, a common tactic is the use of reconnaissance against a system to discover potential attack vectors (such as applications and services).
<img width="836" height="538" alt="Screenshot 2025-08-26 at 8 51 53 PM" src="https://github.com/user-attachments/assets/b131f08e-bd12-4220-93fc-dfcd23599503" />
This series of phases also accommodates for an attacker creating a form of persistence (such as files or a process that allows the attacker to connect to the machine at any time). Finally, the UKC accounts for the fact that attackers will often use a combination of the tactics listed above.

We will explore the different phases of this section of the UKC in the headings below:

Reconnaissance (MITRE Tactic TA0043)

This phase of the UKC describes techniques that an adversary employs to gather information relating to their target. This can be achieved through means of passive and active reconnaissance. The information gathered during this phase is used all throughout the later stages of the UKC (such as the initial foothold).

Information gathered from this phase can include:

Discovering what systems and services are running on the target, this is beneficial information in the weaponisation and exploitation phases of this section.
Finding contact lists or lists of employees that can be impersonated or used in either a social-engineering or phishing attack.
Looking for potential credentials that may be of use in later stages, such as pivoting or initial access.
Understanding the network topology and other networked systems can be used to pivot too.
Weaponization (MITRE Tactic TA0001)

This phase of the UKC describes the adversary setting up the necessary infrastructure to perform the attack. For example, this could be setting up a command and control server, or a system capable of catching reverse shells and delivering payloads to the system.

Social Engineering (MITRE Tactic TA0001)

This phase of the UKC describes techniques that an adversary can employ to manipulate employees to perform actions that will aid in the adversaries attack. For example, a social engineering attack could include:

Getting a user to open a malicious attachment.
Impersonating a web page and having the user enter their credentials.
Calling or visiting the target and impersonating a user (for example, requesting a password reset) or being able to gain access to areas of a site that the attacker would not previously be capable of (for example, impersonating a utility engineer).
Exploitation (MITRE Tactic TA0002)

This phase of the UKC describes how an attacker takes advantage of weaknesses or vulnerabilities present in a system. The UKC defines “Exploitation” as abuse of vulnerabilities to perform code execution. For example:

Uploading and executing a reverse shell to a web application.
Interfering with an automated script on the system to execute code.
Abusing a web application vulnerability to execute code on the system it is running on.
Persistence (MITRE Tactic TA0003)

This phase of the UKC is rather short and simple. Specifically, this phase of the UKC describes the techniques an adversary uses to maintain access to a system they have gained an initial foothold on. For example:

Creating a service on the target system that will allow the attacker to regain access.
Adding the target system to a Command & Control server where commands can be executed remotely at any time.
Leaving other forms of backdoors that execute when a certain action occurs on the system (i.e. a reverse shell will execute when a system administrator logs in).
Defence Evasion (MITRE Tactic TA0005)

The “Defence Evasion” section of the UKC is one of the more valuable phases of the UKC. This phase specifically is used to understand the techniques an adversary uses to evade defensive measures put in place in the system or network. For example, this could be:

Web application firewalls.
Network firewalls.
Anti-virus systems on the target machine.
Intrusion detection systems.
This phase is valuable when analysing an attack as it helps form a response and better yet — gives the defensive team information on how they can improve their defence systems in the future.

Command & Control (MITRE Tactic TA0011)

The “Command & Control” phase of the UKC combines the efforts an adversary made during the “Weaponization” stage of the UKC to establish communications between the adversary and target system.

An adversary can establish command and control of a target system to achieve its action on objectives. For example, the adversary can:

Execute commands.
Steal data, credentials and other information.
Use the controlled server to pivot to other systems on the network.
Pivoting (MITRE Tactic TA0008)

“Pivoting” is the technique an adversary uses to reach other systems within a network that are not otherwise accessible (for example, they are not exposed to the internet). There are often many systems in a network that are not directly reachable and often contain valuable data or have weaker security.

For example, an adversary can gain access to a web server that is publically accessible to attack other systems that are within the same network (but are not accessible via the internet).

Answer the questions below
What is an example of a tactic to gain a foothold using emails?
Above under the Social Engineering section you will find; Getting a user to open a malicious attachment. This is the hint of about the tatic being used in email. Click the blue link next to Social Engineering labeled, MITRE Tactic TA0001.
<img width="748" height="113" alt="Screenshot 2025-08-26 at 8 52 56 PM" src="https://github.com/user-attachments/assets/4ae1e605-e090-4eea-80c5-6b42b543fa07" />
The MITRE ATT&CK page will load, you will see the Techniques table below the scroll down till reach T1566.
<img width="692" height="332" alt="Screenshot 2025-08-26 at 8 53 03 PM" src="https://github.com/user-attachments/assets/3b145d89-fa40-4828-a4ad-853897dcc411" />
Once you reach this technique you will have your answer. Once you find it, highlight & copy (ctrl +c ) or type the answer into the TryHackMe answer field, then click submit.
<img width="673" height="93" alt="Screenshot 2025-08-26 at 8 53 10 PM" src="https://github.com/user-attachments/assets/ff03dc11-2345-40a0-a2f2-6888357cea32" />
Answer: Phishing

Impersonating an employee to request a password reset is a form of what?
Since the answer can be found above, I won’t be posting it. You can follow along to learn and discover where they are located.

Scroll up till you find the section about manipulating employees, the name of this section is the answer to this question. Once you find it, highlight & copy (ctrl +c ) or type the answer into the TryHackMe answer field, then click submit.

Press enter or click to view image in full size
<img width="754" height="177" alt="Screenshot 2025-08-26 at 8 54 43 PM" src="https://github.com/user-attachments/assets/06be2465-efc8-4965-86a8-d5221609eda5" />
An adversary setting up the Command & Control server infrastructure is what phase of the Unified Kill Chain?
Since the answer can be found above, I won’t be posting it. You can follow along to learn and discover where they are located.

Scroll up to the Command & Control Section, in the first sentence you will find the answer. Once you find it, highlight & copy (ctrl +c ) or type the answer into the TryHackMe answer field, then click submit.
<img width="740" height="171" alt="Screenshot 2025-08-26 at 8 54 49 PM" src="https://github.com/user-attachments/assets/2251ca8d-a469-464e-ac97-abbf616dda30" />

Exploiting a vulnerability present on a system is what phase of the Unified Kill Chain?
Since the answer can be found above, I won’t be posting it. You can follow along to learn and discover where they are located.

Scroll up to the Section with MITRE Tactic TA0002, in the first sentence you will find the answer, the highlighted part describes what the question is asking. Once you find it, highlight & copy (ctrl +c ) or type the answer into the TryHackMe answer field, then click submit.
<img width="761" height="147" alt="Screenshot 2025-08-26 at 8 54 56 PM" src="https://github.com/user-attachments/assets/0e48baf7-78c3-44fa-bdfb-7d678e467095" />
Moving from one system to another is an example of?
Since the answer can be found above, I won’t be posting it. You can follow along to learn and discover where they are located.

Scroll up to the Section with MITRE Tactic TA0008, in the first sentence you will find the answer, the highlighted part describes what the question is asking. Once you find it, highlight & copy (ctrl +c ) or type the answer into the TryHackMe answer field, then click submit.

Press enter or click to view image in full size
<img width="699" height="142" alt="Screenshot 2025-08-26 at 8 59 21 PM" src="https://github.com/user-attachments/assets/5001f4ff-3d5d-4625-9dc5-68ba802718f8" />
Leaving behind a malicious service that allows the adversary to log back into the target is what?
Since the answer can be found above, I won’t be posting it. You can follow along to learn and discover where they are located.

Scroll up to the Section with MITRE Tactic TA0003, the last bullet point is where you can find the answer, the highlighted part describes what the question is asking. Once you find it, highlight & copy (ctrl +c ) or type the answer into the TryHackMe answer field, then click submit.
<img width="715" height="110" alt="Screenshot 2025-08-26 at 8 59 28 PM" src="https://github.com/user-attachments/assets/6cd6ab07-7285-4284-8d15-6c70d646749d" />
Task 6 Phase: Through (Network Propagation)
This phase follows a successful foothold being established on the target network. An attacker would seek to gain additional access and privileges to systems and data to fulfil their goals. The attacker would set up a base on one of the systems to act as their pivot point and use it to gather information about the internal network.

Press enter or click to view image in full size
<img width="763" height="466" alt="Screenshot 2025-08-26 at 8 59 42 PM" src="https://github.com/user-attachments/assets/f078c05c-ea6d-4fb6-af30-8409d4fcf8e0" />
Pivoting (MITRE Tactic TA0008)

Once the attacker has access to the system, they would use it as their staging site and a tunnel between their command operations and the victim’s network. The system would also be used as the distribution point for all malware and backdoors at later stages.

Discovery (MITRE Tactic TA0007)
The adversary would uncover information about the system and the network it is connected to. Within this stage, the knowledge base would be built from the active user accounts, the permissions granted, applications and software in use, web browser activity, files, directories and network shares, and system configurations.

Privilege Escalation (MITRE Tactic TA0004)
Following their knowledge-gathering, the adversary would try to gain more prominent permissions within the pivot system. They would leverage the information on the accounts present with vulnerabilities and misconfigurations found to elevate their access to one of the following superior levels:

SYSTEM/ ROOT.
Local Administrator.
A user account with Admin-like access.
A user account with specific access or functions.
Execution (MITRE Tactic TA0002)
Recall when the adversary set up their attack infrastructure. Once the attacker has access to the system, they would use it as their staging site and a tunnel between their command operations and the victim’s network. The system would also be used as the distribution point for all malware and backdoors at later stages. and weaponised payloads? This is where they deploy their malicious code using the pivot system as their host. Remote trojans, C2 scripts, malicious links and scheduled tasks are deployed and created to facilitate a recurring presence on the system and uphold their persistence.

Credential Access (MITRE Tactic TA0006)
Working hand in hand with the Privilege Escalation stage, the adversary would attempt to steal account names and passwords through various methods, including keylogging and credential dumping. This makes them harder to detect during their attack as they would be using legitimate credentials.

Lateral Movement (MITRE Tactic TA0008)

With the credentials and elevated privileges, the adversary would seek to move through the network and jump onto other targeted systems to achieve their primary objective. The stealthier the technique used, the better.

Answer the questions below
As a SOC analyst, you pick up numerous alerts pointing to failed login attempts from an administrator account. What stage of the kill chain would an attacker be seeking to achieve?
Since the answer can be found above, I won’t be posting it. You can follow along to learn and discover where they are located.

From the question, I am assuming that they already had access to the system, and were trying to gain higher privledged access. Scroll up to the Section with MITRE Tactic TA0004, in the first sentence you will find the highlighted part that describes what the question is asking. Once you find it, highlight & copy (ctrl +c ) or type the answer into the TryHackMe answer field, then click submit.
<img width="730" height="152" alt="Screenshot 2025-08-26 at 9 02 55 PM" src="https://github.com/user-attachments/assets/14035e83-fedd-4421-aebd-16337bd81aa2" />
Mimikatz, a known attack tool, was detected running on the IT Manager’s computer. What is the mission of the tool?
So let’s first go find out what Mimikatz is, go up to one of the links to a MITRE Tactic and click on it to open a new tab.
<img width="830" height="98" alt="Screenshot 2025-08-26 at 9 02 59 PM" src="https://github.com/user-attachments/assets/68cdcb33-aae4-4394-b6e3-55086d07bbdb" />
Once the MITRE ATT&CK page loads, click the Software link along the top.
<img width="778" height="154" alt="Screenshot 2025-08-26 at 9 03 05 PM" src="https://github.com/user-attachments/assets/03538c73-70ec-405c-9271-bb13662f5591" />

On the next page that loads, you will see on the left side of the screen a list of software, scroll down till you reach Mimikatz and click on it.
<img width="369" height="552" alt="Screenshot 2025-08-26 at 9 03 12 PM" src="https://github.com/user-attachments/assets/745b4d8b-cbc7-4c11-b38b-141f8ec1d40d" />
On the right side of the webpage you will see a description of Mimikatz, this is what we were looking for. Now lets head back to the TryHackMe task to find what term we are looking for.
<img width="686" height="216" alt="Screenshot 2025-08-26 at 9 03 18 PM" src="https://github.com/user-attachments/assets/f55c0d65-c7ea-4aa0-8fb9-2182e3094a47" />

Looking through the different Tactics we see the answer can be found in the Credential Access Section, the answer is at the end of the first sentence. Once you find it, highlight & copy (ctrl +c ) or type the answer into the TryHackMe answer field, then click submit.
<img width="750" height="83" alt="Screenshot 2025-08-26 at 9 03 23 PM" src="https://github.com/user-attachments/assets/7d5da476-7528-4ba1-a71c-4d7f8629532f" />
Task 7 Phase: Out (Action on Objectives)
<img width="425" height="232" alt="Screenshot 2025-08-26 at 9 03 27 PM" src="https://github.com/user-attachments/assets/5d678fd2-e97b-4dc2-9f06-ff83d5eb46c7" />
This phase wraps up the journey of an adversary’s attack on an environment, where they have critical asset access and can fulfil their attack goals. These goals are usually geared toward compromising the confidentiality, integrity and availability (CIA) triad.
<img width="772" height="492" alt="Screenshot 2025-08-26 at 9 03 34 PM" src="https://github.com/user-attachments/assets/6d85dc96-4d8b-4dc9-a9dd-38ccd0afe68f" />
The tactics to be deployed by an attacker would include:

Collection MITRE Tactic (TA0009)
After all the hunting for access and assets, the adversary will be seeking to gather all the valuable data of interest. This, in turn, compromises the confidentiality of the data and would lead to the next attack stage — Exfiltration. The main target sources include drives, browsers, audio, video and email.

Exfiltration (MITRE Tactic TA0010)
To elevate their compromise, the adversary would seek to steal data, which would be packaged using encryption measures and compression to avoid any detection. The C2 channel and tunnel deployed in the earlier phases will come in handy during this process.

Impact (MITRE Tactic TA0040)
If the adversary seeks to compromise the integrity and availability of the data assets, they would manipulate, interrupt or destroy these assets. The goal would be to disrupt business and operational processes and may involve removing account access, disk wipes, and data encryption such as ransomware, defacement and denial of service (DoS) attacks.

Objectives
With all the power and access to the systems and network, the adversary would seek to achieve their strategic goal for the attack.

For example, if the attack was financially motivated, they may seek to encrypt files and systems with ransomware and ask for payment to release the data. In other instances, the attacker may seek to damage the reputation of the business, and they would release private and confidential information to the public.

Answer the questions below
While monitoring the network as a SOC analyst, you realise that there is a spike in the network activity, and all the traffic is outbound to an unknown IP address. What stage could describe this activity?
Since the answer can be found above, I won’t be posting it. You can follow along to learn and discover where they are located.

Scroll up till you see MIRTE Tactic TA0010, the last sentence in this section gives away what the attacker is using to get the data. Once you find it, highlight & copy (ctrl +c ) or type the answer into the TryHackMe answer field, then click submit.

Press enter or click to view image in full size
<img width="673" height="74" alt="Screenshot 2025-08-26 at 9 07 08 PM" src="https://github.com/user-attachments/assets/d56fdc3c-c20e-4d66-90b0-d558dd1dee3d" />
Personally identifiable information (PII) has been released to the public by an adversary, and your organisation is facing scrutiny for the breach. What part of the CIA triad would be affected by this action?
Let’s start by Googling the CIA triad, to find out exactly what it is and where the PII would fall into it. So head to Google, in the search bar in the middle of the screen type CIA triad, and press enter to search.
<img width="1308" height="627" alt="Screenshot 2025-08-26 at 9 11 10 PM" src="https://github.com/user-attachments/assets/41190f70-d6bf-45c7-927d-fa35398a820e" />
Once the search loads, on the right side I had a sample load from TechTarget explaining what the CIA triad is, at least a little bit. But it at least gives up the Pillars, which is all we really need.
<img width="844" height="425" alt="Screenshot 2025-08-26 at 9 13 02 PM" src="https://github.com/user-attachments/assets/f7fc8d43-0a11-4071-a65e-20bd9bed6d09" />
So let me define what each Pillar is then we can answer the question.

Confidentiality- The ability to keep data secret.
Integrity- The ability to keep data from being tampered with.
Availability- The ability to readily access to the data.
Knowing that it was Personal Identifable information (PII) that was released to the public, only one of the pillars of the CIA traid seems to be the answer.

Answer: Confidentiality

Task 8 Practical
<img width="534" height="297" alt="Screenshot 2025-08-26 at 9 14 13 PM" src="https://github.com/user-attachments/assets/850d82ca-ae4a-4236-8230-6f262e6c5c23" />
Deploy the static site attached to the task. You will need to match the various actions of an attacker to the correct phase of the Unified Kill Chain framework to reveal the flag.

Answer the questions below
Match the scenario prompt to the correct phase of the Unified Kill Chain to reveal the flag at the end. What is the flag?
To start off you need to click the green View Site button at the top of the Task.
<img width="675" height="163" alt="Screenshot 2025-08-26 at 9 14 23 PM" src="https://github.com/user-attachments/assets/cd09d7de-b2f9-4a0a-ae26-22cd887501ca" />
The screen will split in half and on the right side will be the practical.
The first practical question is; The Attacker uses tools to gather information about a system. What phase of the Unified Kill Chain is this? If you go back to Task 4 you can see the whole Unified Kill Chain, look at all three of these links to see which is the info gathering phase.

<img width="861" height="72" alt="Screenshot 2025-08-26 at 9 17 05 PM" src="https://github.com/user-attachments/assets/a6bd09c3-00fa-413a-940d-abf370735c67" />
Once you figure out the phase, click button to go to the next question.
<img width="669" height="86" alt="Screenshot 2025-08-26 at 9 17 10 PM" src="https://github.com/user-attachments/assets/5325df45-dd6f-48c9-9564-296e5016baaa" />
The next question is; The Attacker installs a malicious script to allow them remote access at a later date. What phase of the Unified Kill Chain is this?
<img width="650" height="641" alt="Screenshot 2025-08-26 at 9 17 19 PM" src="https://github.com/user-attachments/assets/194e0af4-c2be-4e4f-ae2d-70419f4c1a94" />
If you go back to Task 4 you can see the whole Unified Kill Chain, look at all three of these links to see which is the remote access at a later date phase.
<img width="710" height="102" alt="Screenshot 2025-08-26 at 9 18 35 PM" src="https://github.com/user-attachments/assets/755217d2-09a7-47f5-af2f-6fe3c30a1114" />
Once you figure out the phase, click button to go to the next question.
<img width="677" height="86" alt="Screenshot 2025-08-26 at 9 18 40 PM" src="https://github.com/user-attachments/assets/cd11c822-ec8d-4620-b4c4-d41f2212f440" />
The next question is; The hacked machine is being controlled from an Attacker’s own server. What phase of the Unified Kill Chain is this?
<img width="695" height="605" alt="Screenshot 2025-08-26 at 9 18 51 PM" src="https://github.com/user-attachments/assets/cb87faf7-e06f-43df-8cb9-b07660f82562" />
If you go back to Task 4 you can see the whole Unified Kill Chain, look at all three of these links to see which is the controlling a victims machine from an Attacker’s own server.

Press enter or click to view image in full size
<img width="670" height="91" alt="Screenshot 2025-08-26 at 9 20 13 PM" src="https://github.com/user-attachments/assets/bfb30250-1bb0-4bf2-a298-fcfe4b9e7fad" />
The next question is; The Attacker uses the hacked machine to access other servers on the same network. What phase of the Unified Kill Chain is this?
<img width="663" height="664" alt="Screenshot 2025-08-26 at 9 20 22 PM" src="https://github.com/user-attachments/assets/8c705026-83e0-4c9d-943f-5fbe387aeaff" />
If you go back to Task 4 you can see the whole Unified Kill Chain, look at all three of these links to see which is the controlling a victims machine from an Attacker’s own server.
<img width="754" height="55" alt="Screenshot 2025-08-26 at 9 21 32 PM" src="https://github.com/user-attachments/assets/4a268b69-dbf2-4f6d-b9fe-ad1a9e682b5a" />
Once you figure out the phase, click button to go to the next question.
<img width="673" height="80" alt="Screenshot 2025-08-26 at 9 21 39 PM" src="https://github.com/user-attachments/assets/3d7e03ee-015a-49eb-a5f6-d683eabc0b60" />
The next question is; The Attacker steals a database and sells this to a 3rd party. What phase of the Unified Kill Chain is this?
<img width="680" height="657" alt="Screenshot 2025-08-26 at 9 22 50 PM" src="https://github.com/user-attachments/assets/ecfe4c34-d15b-40ea-8a14-1c8a5f719beb" />
If you go back to Task 4 you can see the whole Unified Kill Chain, look at all three of these links to see which is the Attackers intended purpose.

Press enter or click to view image in full size
<img width="720" height="88" alt="Screenshot 2025-08-26 at 9 22 58 PM" src="https://github.com/user-attachments/assets/c72ea587-2ca5-47df-978f-34f7de7060fe" />
Once you figure out the phase, click the button.
<img width="672" height="72" alt="Screenshot 2025-08-26 at 9 23 57 PM" src="https://github.com/user-attachments/assets/ddfbac81-c544-4935-9c98-64216698f3f9" />
This time at the bottom will reveal the flag. Highlight & copy (ctrl +c ) or type the answer into the TryHackMe answer field, then click submit.
<img width="675" height="661" alt="Screenshot 2025-08-26 at 9 24 05 PM" src="https://github.com/user-attachments/assets/67dc7737-79a2-4707-b6c3-01af3abed1bb" />


Answer: THM{UKC_SCENARIO}

Task 9 Conclusion

