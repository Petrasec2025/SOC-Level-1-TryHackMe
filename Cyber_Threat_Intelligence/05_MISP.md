<img width="1438" height="300" alt="Screenshot 2025-09-06 at 11 51 48 PM" src="https://github.com/user-attachments/assets/b21acee7-2e7b-481e-b347-ce5f1279110c" />
Hey all, this is the eleventh installment in my walkthrough series on TryHackMe’s SOC Level 1 path and the fifth and final room in this module on Cyber Threat Intelligence, where we‘re learning about identifying and using available security knowledge to mitigate and manage potential adversary actions.

This room will provide a walk-through on the use of MISP as a Threat Sharing Platform.

Link: https://tryhackme.com/room/misp
Task 1: Room Overview
MISP — MALWARE INFORMATION SHARING PLATFORM

This room explores the MISP Malware & Threat Sharing Platform through its core objective to foster sharing of structured threat information among security analysts, malware researchers and IT professionals.

Room Objectives
We will be covering the following areas within the room:

Introduction to MISP and why it was developed.
Use cases MISP can be applied to
Core features and terminologies.
Dashboard Navigation.
Event Creation and Management.
Feeds and Taxonomies.
Room Prerequisites
General familiarity with security concepts is: check out the Pre-Security path and the Jr. Security Analyst room.

At the end of the room, we will have an exercise task to test your knowledge of using MISP.
<img width="701" height="485" alt="Screenshot 2025-09-06 at 11 51 58 PM" src="https://github.com/user-attachments/assets/077a1c2d-4853-4f1d-ab0e-4607e827e2e7" />
Task 2: MISP Introduction: Features & Terminologies
What is MISP?
MISP (Malware Information Sharing Platform) is an open-source threat information platform that facilitates the collection, storage and distribution of threat intelligence and Indicators of Compromise (IOCs) related to malware, cyber attacks, financial fraud or any intelligence within a community of trusted members.

Information sharing follows a distributed model, with supported closed, semi-private, and open communities (public). Additionally, the threat information can be distributed and consumed by Network Intrusion Detection Systems (NIDS), log analysis tools and Security Information and Event Management Systems (SIEM).

MISP is effectively useful for the following use cases:

Malware Reverse Engineering: Sharing of malware indicators to understand how different malware families function.
Security Investigations: Searching, validating and using indicators in investigating security breaches.
Intelligence Analysis: Gathering information about adversary groups and their capabilities.
Law Enforcement: Using Indicators to support forensic investigations.
Risk Analysis: Researching new threats, their likelihood and occurrences.
Fraud Analysis: Sharing of financial indicators to detect financial fraud.
What does MISP support?
<img width="555" height="487" alt="Screenshot 2025-09-06 at 11 52 09 PM" src="https://github.com/user-attachments/assets/c74f009e-8f12-49fb-9e39-a001700647d0" />
MISP provides the following core functionalities:

IOC database: This allows for the storage of technical and non-technical information about malware samples, incidents, attackers and intelligence.
Automatic Correlation: Identification of relationships between attributes and indicators from malware, attack campaigns or analysis.
Data Sharing: This allows for sharing of information using different models of distributions and among different MISP instances.
Import & Export Features: This allows the import and export of events in different formats to integrate other systems such as NIDS, HIDS, and OpenIOC.
Event Graph: Showcases the relationships between objects and attributes identified from events.
API support: Supports integration with own systems to fetch and export events and intelligence.
The following terms are commonly used within MISP and are related to the functionalities described above and the general usage of the platform:

Events: Collection of contextually linked information.
Attributes: Individual data points associated with an event, such as network or system indicators.
Objects: Custom attribute compositions.
Object References: Relationships between different objects.
Sightings: Time-specific occurrences of a given data point or attribute detected to provide more credibility.
Tags: Labels attached to events/attributes.
Taxonomies: Classification libraries are used to tag, classify and organise information.
Galaxies: Knowledge base items used to label events/attributes.
Indicators: Pieces of information that can detect suspicious or malicious cyber activity.
Task 3: Using the System
For you to understand how MISP works and follow along in the task, launch the attached machine and use the credentials provided to log in to the Analyst Account on https://LAB_WEB_URL.p.thmlabs.com/. Wait 1 minute for the URL and lab to start up.

Username: Analyst@THM.thm Password: Analyst12345&

Dashboard
The analyst’s view of MISP provides you with the functionalities to track, share and correlate events and IOCs identified during your investigation. The dashboard’s menu contains the following options, and we shall look into them further:

Home button: Returns you to the application’s start screen, the event index page or the page set as a custom home page using the star in the top bar.
Event Actions: All the malware data entered into MISP comprises an event object described by its connected attributes. The Event actions menu gives access to all the functionality related to the creation, modification, deletion, publishing, searching and listing of events and attributes.
Dashboard: This allows you to create a custom dashboard using widgets.
Galaxies: Shortcut to the list of MISP Galaxies on the MISP instance. More on these on the Feeds & Taxonomies Task.
Input Filters: Input filters alter how users enter data into this instance. Apart from the basic validation of attribute entry by type, the site administrators can define regular expression replacements and blocklists for specific values and block certain values from being exportable. Users can view these replacement and blocklist rules here, while an administrator can alter them.
Global Actions: Access to information about MISP and this instance. You can view and edit your profile, view the manual, read the news or the terms of use again, see a list of the active organisations on this instance and a histogram of their contributions by an attribute type.
MISP: Simple link to your baseurl.
Name: Name (Auto-generated from Mail address) of currently logged in user.
Envelope: Link to User Dashboard to consult some of your notifications and changes since the last visit. Like some of the proposals received for your organisation.
Log out: The Log out button to end your session immediately.
<img width="1252" height="635" alt="Screenshot 2025-09-06 at 11 55 42 PM" src="https://github.com/user-attachments/assets/a31b1aaa-8625-46af-9de2-ebfdeb1c7d5d" />
<img width="1260" height="708" alt="Screenshot 2025-09-06 at 11 56 07 PM" src="https://github.com/user-attachments/assets/d2dffb10-c245-4e78-80ad-ead9e6021a0f" />
<img width="1201" height="610" alt="Screenshot 2025-09-06 at 11 56 18 PM" src="https://github.com/user-attachments/assets/de45c29e-45e5-4214-8c41-b09e835d4c49" />
<img width="1296" height="737" alt="Screenshot 2025-09-06 at 11 56 30 PM" src="https://github.com/user-attachments/assets/57581ddc-a728-43fc-b49d-54737300ccc7" />

Attributes can be added manually or imported through other formats such as OpenIOC and ThreatConnect. To add them manually, click the Add Attribute and populate the form fields.

Some essential options to note are:

For Intrusion Detection System: This allows the attribute to be used as an IDS signature when exporting the NIDS data unless it overrides the permitted list. If not set, the attribute is considered contextual information and not used for automatic detection.
Batch import: If there are several attributes of the same type to enter (such as a list of IP addresses, it is possible to join them all into the same value field, separated by a line break between each line. This will allow the system to create separate lines for each attribute.
In our example below, we add an Emotet Epoch 4 C2 IP address associated with the infection as our attributes, obtained from the IOC text file.

Press enter or click to view image in full size
<img width="1280" height="690" alt="Screenshot 2025-09-06 at 11 56 38 PM" src="https://github.com/user-attachments/assets/19360891-e33a-476f-9d31-3b07aec867f4" />
The analyst can also add file attachments to the event. These may include malware, report files from external analysis or simply artefacts dropped by the malware. We have added the Cobalt Strike EXE binary file to our event in our example. You also have to check the Malware checkbox to mark the file as malware. This will ensure that it is zipped and passworded to protect users from accidentally downloading and executing the file.

Press enter or click to view image in full size
<img width="1301" height="713" alt="Screenshot 2025-09-06 at 11 56 46 PM" src="https://github.com/user-attachments/assets/a0444d24-7292-4816-8a6b-397eb24a8dc9" />
Publish Event

Once the analysts have created events, the organisation admin will review and publish those events to add them to the pool of events. This will also share the events to the distribution channels set during the creation of the events.
<img width="1311" height="729" alt="Screenshot 2025-09-06 at 11 56 55 PM" src="https://github.com/user-attachments/assets/78e03b42-e626-4ada-8e69-cf32c2cc0414" />
Answer the questions below:

3a. How many distribution options does MISP provide to share threat information?

In the task text:

Press enter or click to view image in full size

Answer: 4

3b. Which user has the role to publish events?


Answer: organisation admin

Task 4: Feeds & Taxonomies
Feeds
Feeds are resources that contain indicators that can be imported into MISP and provide attributed information about security events. These feeds provide analysts and organisations with continuously updated information on threats and adversaries and aid in their proactive defence against attacks.

MISP Feeds provide a way to:

Exchange threat information.
Preview events along with associated attributes and objects.
Select and import events to your instance.
Correlate attributes identified between events and feeds.
Feeds are enabled and managed by the Site Admin for the analysts to obtain information on events and indicators.

Press enter or click to view image in full size

Taxonomies
A taxonomy is a means of classifying information based on standard features or attributes. On MISP, taxonomies are used to categorise events, indicators and threat actors based on tags that identify them.

Press enter or click to view image in full size

Analysts can use taxonomies to:

Set events for further processing by external tools such as VirusTotal.
Ensure events are classified appropriately before the Organisation Admin publishes them.
Enrich intrusion detection systems’ export values with tags that fit specific deployments.
Taxonomies are expressed in machine tags, which comprise three vital parts:

Namespace: Defines the tag’s property to be used.
Predicate: Specifies the property attached to the data.
Value: Numerical or text details to map the property.
(Source: MISP)

Taxonomies are listed under the Event Actions tab. The site admin can enable relevant taxonomies.

Press enter or click to view image in full size

Tagging
Information from feeds and taxonomies, tags can be placed on events and attributes to identify them based on the indicators or threats identified correctly. Tagging allows for effective sharing of threat information between users, communities and other organisations using MISP to identify various threats.

In our CobaltStrike event example, we can add tags by clicking on the buttons in the Tags section and searching from the available options appropriate to the case. The buttons represent global tags and local tags, respectively. It is also important to note that you can add your unique tags to your MISP instance as an analyst or organisation that would allow you to ingest, navigate through and share information quickly within the organisation.

Press enter or click to view image in full size

Tagging Best Practices
Tagging at Event level vs Attribute Level

Tags can be added to an event and attributes. Tags are also inheritable when set. It is recommended to set tags on the entire event and only include tags on attributes when they are an exception from what the event indicates. This will provide a more fine-grained analysis.

The minimal subset of Tags

The following tags can be considered a must-have to provide a well-defined event for distribution:

Traffic Light Protocol: Provides a colour schema to guide how intelligence can be shared.
Confidence: Provides an indication as to whether or not the data being shared is of high quality and has been vetted so that it can be trusted to be good for immediate usage.
Origin: Describes the source of information and whether it was from automation or manual investigation.
Permissible Actions Protocol: An advanced classification that indicates how the data can be used to search for compromises within the organisation.
Task 5: Scenario Event

CIRCL (Computer Incident Respons Center Luxembourg) published an event associated with PupyRAT infection. Your organisation is on alert for remote access trojans and malware in the wild, and you have been tasked to investigate this event and correlate the details with your SIEM. Use what you have learned from the room to identify the event and complete this task.

Answer the questions below:

5a. What event ID has been assigned to the PupyRAT event?

For this you’ll either need to use the attackbox to launch the webapp or connect through a vpn, which is how I’ll be doing it. Launch the webapp using the link provided in task 3, login using the creds provided in the same task and then search pupyrat, ID will be displayed after:

Press enter or click to view image in full size

Answer: 1145

5b. The event is associated with the adversary gaining ______ into organisations.

Click on the event ID and under Tags we’ll get our answer:

Press enter or click to view image in full size

Answer: remote access

5c. What IP address has been mapped as the PupyRAT C2 Server

For this I just did a Ctrl+F for “c2” which got no relevant hits, then searched “command” and that got me the answer:

Press enter or click to view image in full size

Answer: 89.107.62.39

5d. From the Intrusion Set Galaxy, what attack group is known to use this form of attack?

just scroll down to galaxies and it’s right there:


Answer: magic hound

5e. There is a taxonomy tag set with a Certainty level of 50. Which one is it?

Press enter or click to view image in full size

Answer: osint

Task 6: Conclusion
Recap
Hopefully, you learned a lot about MISP and its use in sharing malware and threat information in this room. This tool is useful in the real world regarding incident reporting. You should be able to use the knowledge gained to effectively document, report and share incident information.

Additional Resources

There is plenty of information and capabilities that were not covered in this room. This leaves plenty of room for research and learning more about MISP. To guide you towards that, look at the following attached links and feel free to come back to the room to practice.

MISP Book
MISP GitHub
CIRCL MISP Training Module 1
CIRCL MISP Training Module 2
We wish to give credit to CIRCL for providing guidelines that supported this room.

This concludes the MISP room on TryHackMe and the Cyber Threat Intelligence module, the second of seven modules in this SOC Level 1 path. This was a great module, very interactive and challenging at times and I’m looking forward to that ramping up in future modules and rooms.

Thanks for joining me on this walkthrough and we’ll see you tomorrow in the next one where we will begin the Network Security and Traffic Analysis module and tackle the trivial Traffic Analysis Essentials and begin our exploration into Snort with the Snort room.
