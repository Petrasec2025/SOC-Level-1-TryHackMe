<img width="1436" height="325" alt="Screenshot 2025-09-06 at 11 10 19 PM" src="https://github.com/user-attachments/assets/f65119f6-cd76-4b26-8516-ee35f02a32d5" />
Provide an understanding of the OpenCTI Project

Task 1 Room Overview
This room will cover the concepts and usage of OpenCTI, an open-source threat intelligence platform. The room will help you understand and answer the following questions:

What is OpenCTI and how is it used?
How would I navigate through the platform?
What functionalities will be important during a security threat analysis?
Prior to going through this room, we recommend checking out these rooms as prerequisites:

MITRE ATT&CK Framework
TheHive
MISP
Threat Intelligence Tools

<img width="805" height="197" alt="Screenshot 2025-09-06 at 11 12 36 PM" src="https://github.com/user-attachments/assets/f02ad3f5-b549-4ff7-a95b-f529d94417f1" />
Task 2 Introduction to OpenCTI
Cyber Threat Intelligence is typically a managerial mystery to handle, with organisations battling with how to input, digest, analyse and present threat data in a way that will make sense. From the rooms that have been linked on the overview, it is clear that there are numerous platforms that have been developed to tackle the juggernaut that is Threat Intelligence.

OpenCTI
OpenCTI is another open-sourced platform designed to provide organisations with the means to manage CTI through the storage, analysis, visualisation and presentation of threat campaigns, malware and IOCs.

Objective
Developed by the collaboration of the French National cybersecurity agency (ANSSI), the platform’s main objective is to create a comprehensive tool that allows users to capitalise on technical and non-technical information while developing relationships between each piece of information and its primary source. The platform can use the MITRE ATT&CK framework to structure the data. Additionally, it can be integrated with other threat intel tools such as MISP and TheHive. Rooms to these tools have been linked in the overview.
<img width="681" height="383" alt="Screenshot 2025-09-06 at 11 13 28 PM" src="https://github.com/user-attachments/assets/be5e4510-926a-42bd-9130-e2e9cd121661" />
Task 3 OpenCTI Data Model
OpenCTI Data Model
OpenCTI uses a variety of knowledge schemas in structuring data, the main one being the Structured Threat Information Expression (STIX2) standards. STIX is a serialised and standardised language format used in threat intelligence exchange. It allows for the data to be implemented as entities and relationships, effectively tracing the origin of the provided information.

This data model is supported by how the platform’s architecture has been laid out. The image below gives an architectural structure for your know-how.
<img width="665" height="456" alt="Screenshot 2025-09-06 at 11 13 41 PM" src="https://github.com/user-attachments/assets/16234556-246a-4e2f-b274-1dc0d2d5ba95" />
Source: OpenCTI Public Knowledge Base

The highlight services include:

GraphQL API: The API connects clients to the database and the messaging system.
Write workers: Python processes utilised to write queries asynchronously from the RabbitMQ messaging system.
Connectors: Another set of python processes used to ingest, enrich or export data on the platform. These connectors provide the application with a robust network of integrated systems and frameworks to create threat intelligence relations and allow users to improve their defence tactics.
According to OpenCTI, connectors fall under the following classes:
<img width="657" height="291" alt="Screenshot 2025-09-06 at 11 13 55 PM" src="https://github.com/user-attachments/assets/750656f5-e48e-445b-a1b0-039d957af05a" />
Refer to the connectors and data model documentation for more details on configuring connectors and the data schema.

Task 4 OpenCTI Dashboard 1
Follow along with the task by launching the attached machine and using the credentials provided; log in to the OpenCTI Dashboard via the AttackBox on http://MACHINE_IP:8080/. Give the machine 5 minutes to start up and it is advisable to use the AttackBox on fullscreen.

Username: info@tryhack.io

Password: TryHackMe1234

Getting OpenCTI Started
So before we go further let’s get to the OpenCTI Dashboard, to do this first we need to click the green Start Machine button at the top of the task, to get the VM up and running.
<img width="307" height="95" alt="Screenshot 2025-09-06 at 11 14 11 PM" src="https://github.com/user-attachments/assets/98603899-9982-42f0-8c80-7fd01fc63a5b" />
Then go to the top of the Webpage and click the blue Start AttackBox icon, the screen will split and take about a minute and a half for the VM to load.
At the bottom of the VM is two arrows pointing in the oppiosite directions, this is the full screen icon. Click on it.

Press enter or click to view image in full size

A new tab will open with the VM in it, while it loads go back to the TryHackMe tab. Go back to the bar at the bottom of the VM and click the — button to exit splitscreen.

Press enter or click to view image in full size

There is a terminal on the screen, if you have read through this, press enter to close it.

Press enter or click to view image in full size
<img width="675" height="446" alt="Screenshot 2025-09-06 at 11 14 29 PM" src="https://github.com/user-attachments/assets/c8115d5a-a22e-4d43-b737-800603a69eab" />
On the right side of the VM is a quick panel, at the top of this panel is Firefox. Click on the firefox icon.

<img width="107" height="464" alt="Screenshot 2025-09-06 at 11 14 39 PM" src="https://github.com/user-attachments/assets/0a640547-8033-4d73-84e6-23313a2a88ee" />
While Firefox loads, go back to the TryHackMe Task. In the first paragraph you will see a link that will take you to the OpenCTI login page. Highlight and copy (ctrl + c) the link.
<img width="355" height="199" alt="Screenshot 2025-09-06 at 11 14 54 PM" src="https://github.com/user-attachments/assets/1da889fc-11df-4c6e-83ba-86f0a8804659" />
Go back to the VM tab, click on the URL bar. Paste (ctrl + v) the OpenCTI address into the bar and press enter.
<img width="678" height="162" alt="Screenshot 2025-09-06 at 11 14 47 PM" src="https://github.com/user-attachments/assets/aac5c4a7-f679-4bf5-9c17-6b55659cdffc" />
The site will load the login page for OpenCTI. The login credentials are back on the TryHackMe Task, you can either highlight copy (ctrl + c) and paste (ctrl + v) or type, the credentials into the login page. Then click the blue Sign In button.
<img width="677" height="724" alt="Screenshot 2025-09-06 at 11 15 06 PM" src="https://github.com/user-attachments/assets/01eeddd7-2b52-4b6d-843a-12587b81fc6f" />
https://medium.com/@haircutfish/tryhackme-opencti-task-1-thru-task-5-7b9605694249#:~:text=You%20will%20have%20a%20small%20pop%2Dup%20to%20save%20you%20password%20into%20firefox%2C%20just%20click%20Don%E2%80%99t%20Save.
You are now in the OpenCTI dashboard and ready to proceed!!!
<img width="675" height="281" alt="Screenshot 2025-09-06 at 11 21 52 PM" src="https://github.com/user-attachments/assets/884898df-3fa6-4f79-999d-4fe7989da08c" />
OpenCTI Dashboard
Once connected to the platform, the opening dashboard showcases various visual widgets summarising the threat data ingested into OpenCTI. Widgets on the dashboard showcase the current state of entities ingested on the platform via the total number of entities, relationships, reports and observables ingested, and changes to these properties noted within 24 hours.

See Image.
<img width="675" height="388" alt="Screenshot 2025-09-06 at 11 21 59 PM" src="https://github.com/user-attachments/assets/1f935bbe-9d78-4412-9fcb-ceebfe2706fd" />

Activities & Knowledge
The OpenCTI categorises and presents entities under the Activities and Knowledge groups on the left-side panel. The activities section covers security incidents ingested onto the platform in the form of reports. It makes it easy for analysts to investigate these incidents. In contrast, the Knowledge section provides linked data related to the tools adversaries use, targeted victims and the type of threat actors and campaigns used.

Analysis
The Analysis tab contains the input entities in reports analysed and associated external references. Reports are central to OpenCTI as knowledge on threats and events are extracted and processed. They allow for easier identification of the source of information by analysts. Additionally, analysts can add their investigation notes and other external resources for knowledge enrichment. As displayed below, we can look at the Triton Software report published by MITRE ATT&CK and observe or add to the details provided.

See Image.
<img width="661" height="347" alt="Screenshot 2025-09-06 at 11 22 20 PM" src="https://github.com/user-attachments/assets/7031bb40-ac4a-48ad-bfe0-146db66273d4" />
Events
Security analysts investigate and hunt for events involving suspicious and malicious activities across their organisational network. Within the Events tab, analysts can record their findings and enrich their threat intel by creating associations for their incidents.

See Image.
<img width="682" height="351" alt="Screenshot 2025-09-06 at 11 22 31 PM" src="https://github.com/user-attachments/assets/d78a59db-16d8-4746-803c-9a415abd1af9" />
Observations
Technical elements, detection rules and artefacts identified during a cyber attack are listed under this tab: one or several identifiable makeup indicators. These elements assist analysts in mapping out threat events during a hunt and perform correlations between what they observe in their environments against the intel feeds.

See Image.
<img width="657" height="408" alt="Screenshot 2025-09-06 at 11 25 03 PM" src="https://github.com/user-attachments/assets/a130bf7a-90ce-48ca-b37e-fd1541b0857b" />
Threats
All information classified as threatening to an organisation or information would be classified under threats. These will include:

Threat Actors: An individual or group of attackers seeking to propagate malicious actions against a target.
Intrusion Sets: An array of TTPs, tools, malware and infrastructure used by a threat actor against targets who share some attributes. APTs and threat groups are listed under this category on the platform due to their known pattern of actions.
Campaigns: Series of attacks taking place within a given period and against specific victims initiated by advanced persistent threat actors who employ various TTPs. Campaigns usually have specified objectives and are orchestrated by threat actors from a nation state, crime syndicate or other disreputable organisation.
See Image.
<img width="675" height="387" alt="Screenshot 2025-09-06 at 11 25 12 PM" src="https://github.com/user-attachments/assets/43c5adf2-5c83-44d5-beac-58702ae8870a" />
Arsenal
This tab lists all items related to an attack and any legitimate tools identified from the entities.

Malware: Known and active malware and trojan are listed with details of their identification and mapping based on the knowledge ingested into the platform. In our example, we analyse the 4H RAT malware and we can extract information and associations made about the malware.
Attack Patterns: Adversaries implement and use different TTPs to target, compromise, and achieve their objectives. Here, we can look at the details of the Command-Line Interface and make decisions based on the relationships established on the platform and navigate through an investigation associated with the technique.
Courses of Action: MITRE maps out concepts and technologies that can be used to prevent an attack technique from being employed successfully. These are represented as Courses of Action (CoA) against the TTPs.
Tools: Lists all legitimate tools and services developed for network maintenance, monitoring and management. Adversaries may also use these tools to achieve their objectives. For example, for the Command-Line Interface attack pattern, it is possible to narrow down that CMD would be used as an execution tool. As an analyst, one can investigate reports and instances associated with the use of the tool.
Vulnerabilities: Known software bugs, system weaknesses and exposures are listed to provide enrichment for what attackers may use to exploit and gain access to systems. The Common Vulnerabilities and Exposures (CVE) list maintained by MITRE is used and imported via a connector.
See Image.
<img width="668" height="383" alt="Screenshot 2025-09-06 at 11 25 30 PM" src="https://github.com/user-attachments/assets/5b0cfe7c-2e8a-4923-86d8-cb6fb26c6c9c" />
Entities
This tab categorises all entities based on operational sectors, countries, organisations and individuals. This information allows for knowledge enrichment on attacks, organisations or intrusion sets.

See Image
<img width="668" height="377" alt="Screenshot 2025-09-06 at 11 25 39 PM" src="https://github.com/user-attachments/assets/dd8e541a-c628-4004-984a-73d4a080d962" />
Answer the questions below
What is the name of the group that uses the 4H RAT malware?
So we learned from the Arsenal section above that we can find out about Malware on the Arsenal tab. So head over to the OpenCTI dashboard.

Press enter or click to view image in full size
<img width="725" height="112" alt="Screenshot 2025-09-06 at 11 25 47 PM" src="https://github.com/user-attachments/assets/be610323-2280-482b-ae86-e6790c80b8f3" />
Once on the OpenCTI dashboard, look to the panel on the left. You will see Arsenal in grey close to the bottom, click on it. This will open the Malware section in the main part of the window on the right.
<img width="165" height="400" alt="Screenshot 2025-09-06 at 11 25 53 PM" src="https://github.com/user-attachments/assets/65cdc020-9329-4c03-80e1-82457f6d7f6c" />
You could use the search bar to look for the 4H RAT malware but, because it is in alphebetical order you can find it right at the top. Click on the 4H RAT box.
<img width="671" height="280" alt="Screenshot 2025-09-06 at 11 26 01 PM" src="https://github.com/user-attachments/assets/8fa351bb-e62d-4172-930d-2364740290b3" />
You will see two panels in the middle of the screen, the panel on the right is the Details panel and the one you want to focus on. If you read the description you will find the answer. Once you find it, highlight copy (ctrl + c) and paste (ctrl + v) or type, the answer into the TryHackMe answer field and click submit.
<img width="678" height="283" alt="Screenshot 2025-09-06 at 11 26 13 PM" src="https://github.com/user-attachments/assets/c94f44d3-f4d7-4235-b48b-3d89028191fd" />

Answer: Putter Panda

What kill-chain execution phase is linked with the Command-Line Interface Attack Pattern?
Go back to the panel on the left, click on Arsenal again.

<img width="160" height="400" alt="Screenshot 2025-09-06 at 11 26 25 PM" src="https://github.com/user-attachments/assets/0b5bfbe6-50b4-4692-a459-1c68dfa6e793" />
Above the center panels you will see this tab panel, click on Attack patterns.
<img width="657" height="57" alt="Screenshot 2025-09-06 at 11 26 33 PM" src="https://github.com/user-attachments/assets/d55b3ac6-ed8f-4664-9366-04f27f0c6341" />
At the top of the Attack pattern panel is a search bar, type Command-Line Interface, into the search bar and press enter to search it.
<img width="655" height="116" alt="Screenshot 2025-09-06 at 11 26 53 PM" src="https://github.com/user-attachments/assets/82baa8c1-3246-4d73-a293-de60624ec39a" />
Your top result will be what you are looking for, click on it.
<img width="678" height="44" alt="Screenshot 2025-09-06 at 11 27 09 PM" src="https://github.com/user-attachments/assets/2acd274f-da95-47f8-877c-be775515683f" />
Again you will have two panels in the middle of the screen, and again we will be focusing on the Details panel. This time though, on the right side of the panel you should see Kill Chain Phase, right underneath it is the answer. Once you find it, highlight copy (ctrl + c) and paste (ctrl + v) or type, the answer into the TryHackMe answer field and click submit.
<img width="678" height="280" alt="Screenshot 2025-09-06 at 11 27 20 PM" src="https://github.com/user-attachments/assets/a091f840-763a-4421-8462-0db7e6f267ee" />
Answer: execution-ics

Within the Activities category, which tab would house the Indicators?
This answer can be found above, in these section it mentions that under this tab can be found one or several indicators. Once you find it, highlight copy (ctrl + c) and paste (ctrl + v) or type, the answer into the TryHackMe answer field and click submit.
<img width="691" height="100" alt="Screenshot 2025-09-06 at 11 27 27 PM" src="https://github.com/user-attachments/assets/3cc32cee-dcd5-4190-902e-cae68775dd8d" />
On OpenCTI this is where you can find it.
<img width="664" height="459" alt="Screenshot 2025-09-06 at 11 33 15 PM" src="https://github.com/user-attachments/assets/1452ad7d-efef-4736-b6ed-d5f93862a024" />
Answer: Observations

Task 5 OpenCTI Dashboard 2
General Tabs Navigation
The day-to-day usage of OpenCTI would involve navigating through different entities within the platform to understand and utilise the information for any threat analysis. We will be looking at the Cobalt Strike malware entity for our walkthrough, mainly found under the Arsenal tab we’ve covered previously. When you select an intelligence entity, the details are presented to the user through:

Overview Tab: Provides the general information about an entity being analysed and investigated. In our case, the dashboard will present you with the entity ID, confidence level, description, relations created based on threats, intrusion sets and attack patterns, reports mentioning the entity and any external references.
See Image
<img width="671" height="378" alt="Screenshot 2025-09-06 at 11 33 23 PM" src="https://github.com/user-attachments/assets/c58c0e2a-5ff7-490d-80e2-fff3b113c5d6" />
Knowledge Tab: Presents linked information associated with the entity selected. This tab will include the reports associated, indicators, relations and attack pattern timeline of the entity. Additionally, an analyst can view fine-tuned details from the tabs on the right-hand pane, where information about the threats, attack vectors, events and observables used within the entity are presented.
See Image.
<img width="650" height="384" alt="Screenshot 2025-09-06 at 11 33 32 PM" src="https://github.com/user-attachments/assets/e77a4546-43a1-4e45-9221-b7bdb0e14fd3" />
Analysis Tab: Provides the reports where the identified entry has been seen. The analysis provides usable information about a threat and guides investigation tasks.
See Image.
<img width="670" height="390" alt="Screenshot 2025-09-06 at 11 33 39 PM" src="https://github.com/user-attachments/assets/6af97420-fa7f-4bcb-8847-4b12ec03a7bc" />
Indicators Tab: Provides information on IOC identified for all the threats and entities.
Data Tab: Contains the files uploaded or generated for export that are related to the entity. These assist in communicating information about threats being investigated in either technical or non-technical formats.
History Tab: Changes made to the element, attributes, and relations are tracked by the platform worker and this tab will outline the changes.
Answer the questions below
What Intrusion sets are associated with the Cobalt Strike malware with a Good confidence level? (Intrusion1, Intrusion2)
Once on the OpenCTI dashboard, look to the panel on the left. You will see Arsenal in grey close to the bottom, click on it. This will open the Malware section in the main part of the window on the right.
<img width="166" height="411" alt="Screenshot 2025-09-06 at 11 33 52 PM" src="https://github.com/user-attachments/assets/aea5a972-592a-4bcd-a8c3-9f1d13b5f5e3" />
Using the search bar type Cobalt Strike into it and press enter.
<img width="655" height="161" alt="Screenshot 2025-09-06 at 11 34 01 PM" src="https://github.com/user-attachments/assets/99002c5e-0299-47ba-baf2-f4df2fe28bed" />
Your first result will be Cobalt Strike, click on it.
<img width="685" height="169" alt="Screenshot 2025-09-06 at 11 34 08 PM" src="https://github.com/user-attachments/assets/0378197a-44bc-4d81-9aec-99c210bd472f" />
When the Knowledge panel loads in the middle of the screen you will see another panel on the right-side of the page now. Go to that new panel and click on the diamond icon that says Intrusion sets.
<img width="197" height="709" alt="Screenshot 2025-09-06 at 11 34 26 PM" src="https://github.com/user-attachments/assets/9e62d88c-789d-422a-9a02-5a3f1197b317" />
When the Intrusion sets panel loads, the first entry gives us the first half of the answer. Now just scroll down till you see the next Intrusion set with a confidencence score of Good, when you find it that is the second half of the answer. Once you find it, type the answer into the TryHackMe answer field and click submit.
<img width="674" height="280" alt="Screenshot 2025-09-06 at 11 34 38 PM" src="https://github.com/user-attachments/assets/cc1e60cd-b000-4412-9098-a686b6f2d08e" />
Answer: CopyKittens, FIN7

Who is the author of the entity?
Go back to the top panel and click on the Overview tab.
<img width="664" height="48" alt="Screenshot 2025-09-06 at 11 34 48 PM" src="https://github.com/user-attachments/assets/00cab9f7-6f1d-4fda-86d3-2acd664f28da" />
This time instead of looking at the Details panel on the right, we are going to look at the Basic Information panel on the left. Above the Distribution of Opinions is the Author. Once you find it, type the answer into the TryHackMe answer field and click submit.
<img width="677" height="284" alt="Screenshot 2025-09-06 at 11 34 58 PM" src="https://github.com/user-attachments/assets/b75da455-4201-4484-b242-86fe1e237d7a" />
Answer: The MITRE Corporation

You have finished these tasks and can now move onto Task 6 Investigative Scenario & Task 7 Room Conclusion.


