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
