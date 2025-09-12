<img width="1415" height="326" alt="Screenshot 2025-09-12 at 4 25 11 PM" src="https://github.com/user-attachments/assets/b557de4b-5314-4912-8275-27c7c90f136e" />

Network Security is a set of operations for protecting data, applications, devices and systems connected to the network. It is accepted as one of the significant subdomains of cyber security. It focuses on the system design, operation and management of the architecture/infrastructure to provide network accessibility, integrity, continuity and reliability. Traffic analysis (often called Network Traffic Analysis) is a subdomain of the Network Security domain, and its primary focus is investigating the network data to identify problems and anomalies.

This room will cover the foundations of Network Security and Traffic analysis and introduce the essential concepts of these disciplines to help you step into Traffic/Packet Analysis. We suggest completing the "Network Fundamentals module before starting working in this room.
<img width="683" height="421" alt="Screenshot 2025-09-12 at 4 25 36 PM" src="https://github.com/user-attachments/assets/08ce6f62-689d-4b3c-bd73-37ad6308ba4a" />
Network Security

The essential concern of Network Security focuses on two core concepts: authentication and authorisation. There are a variety of tools, technologies, and approaches to ensure and measure implementations of these two key concepts and go beyond to provide continuity and reliability. Network security operations contain three base control levels to ensure the maximum available security management.

Base Network Security Control Levels:

Physical	Physical security controls prevent unauthorised physical access to networking devices, cable boards, locks, and all linked components.
Technical	Data security controls prevent unauthorised access to network data, like installing tunnels and implementing security layers.
Administrative	Administrative security controls provide consistency in security operations like creating policies, access levels and authentication processes.

There are two main approaches and multiple elements under these control levels. The most common elements used in network security operations are explained below.

The main approaches:

Access Control	Threat Control
The starting point of Network Security. It is a set of controls to ensure authentication and authorisation. 	
Detecting and preventing anomalous/malicious activities on the network. It contains both internal (trusted) and external traffic data probes.

The key elements of Access Control:

Firewall Protection
Controls incoming and outgoing network traffic with predetermined security rules. Designed to block suspicious/malicious traffic and application-layer threats while allowing legitimate and expected traffic.
Network Access Control (NAC)
Controls the devices' suitability before access to the network. Designed to verify device specifications and conditions are compliant with the predetermined profile before connecting to the network.
Identity and Access Management (IAM)	Controls and manages the asset identities and user access to data systems and resources over the network.
Load Balancing	Controls the resource usage to distribute (based on metrics) tasks over a set of resources and improve overall data processing flow.
Network Segmentation
Creates and controls network ranges and segmentation to isolate the users' access levels, group assets with common functionalities, and improve the protection of sensitive/internal devices/data in a safer network.
Virtual Private Networks (VPN)
Creates and controls encrypted communication between devices (typically for secure remote access) over the network (including communications over the internet).
Zero Trust Model	Suggests configuring and implementing the access and permissions at a minimum level (providing access required to fulfil the assigned role). The mindset is focused on: "Never trust, always verify".
The key elements of Threat Control:

Intrusion Detection and Prevention (IDS/IPS)
Inspects the traffic and creates alerts (IDS) or resets the connection (IPS) when detecting an anomaly/threat.
Data Loss Prevention (DLP)
Inspects the traffic (performs content inspection and contextual analysis of the data on the wire) and blocks the extraction of sensitive data.
Endpoint Protection
Protecting all kinds of endpoints and appliances that connect to the network by using a multi-layered approach like encryption, antivirus, antimalware, DLP, and IDS/IPS.
Cloud Security	Protecting cloud/online-based systems resources from threats and data leakage by applying suitable countermeasures like VPN and data encryption.
Security Information and Event Management (SIEM)
Technology that helps threat detection, compliance, and security incident management, through available data (logs and traffic statistics) by using event and context analysis to identify anomalies, threats, and vulnerabilities.
Security Orchestration Automation and Response (SOAR)
Technology that helps coordinate and automates tasks between various people, tools, and data within a single platform to identify anomalies, threats, and vulnerabilities. It also supports vulnerability management, incident response, and security operations.
Network Traffic Analysis & Network Detection and Response	Inspecting network traffic or traffic capture to identify anomalies and threats.
Typical Network Security Management Operation is explained in the given table:

Deployment	Configuration	Management	Monitoring	Maintenance
Device and software installation
Initial configuration
Automation
Feature configuration
Initial network access configuration
Security policy implementation
NAT and VPN implementation
Threat mitigation
System monitoring
User activity monitoring
Threat monitoring
Log and traffic sample capturing
Upgrades
Security updates
Rule adjustments
Licence management
Configuration updates
Managed Security Services

Not every organisation has enough resources to create dedicated groups for specific security domains. There are plenty of reasons for this: budget, employee skillset, and organisation size could determine how security operations are handled. At this point, Managed Security Services (MSS) come up to fulfil the required effort to ensure/enhance security needs. MSS are services that have been outsourced to service providers. These service providers are called Managed Security Service Providers (MSSPs). Today, most MSS are time and cost effective, can be conducted in-house or outsourced, are easy to engage, and ease the management process. There are various elements of MSS, and the most common ones are explained below.

Network Penetration Testing 	Assessing network security by simulating external/internal attacker techniques to breach the network.
Vulnerability Assessment	Assessing network security by discovering and analysing vulnerabilities in the environment.
Incident Response
An organised approach to addressing and managing a security breach. It contains a set of actions to identify, contain, and eliminate incidents.
Behavioural Analysis	An organised approach to addressing system and user behaviours, creating baselines and traffic profiles for specific patterns to detect anomalies, threats, vulnerabilities, and attacks.
Answer the questions below
Which Security Control Level covers contain creating security policies?
Administrative

Correct Answer
Which Access Control element works with data metrics to manage data flow?

Load Balancing

Correct Answer
Which technology helps correlate different tool outputs and data sources?
SOAR
<img width="1330" height="520" alt="Screenshot 2025-09-12 at 4 27 12 PM" src="https://github.com/user-attachments/assets/0a6eea31-4249-4159-b665-dc06b93032b2" />
Traffic Analysis / Network Traffic Analysis

Traffic Analysis is a method of intercepting, recording/monitoring, and analysing network data and communication patterns to detect and respond to system health issues, network anomalies, and threats. The network is a rich data source, so traffic analysis is useful for security and operational matters. The operational issues cover system availability checks and measuring performance, and the security issues cover anomaly and suspicious activity detection on the network. 

Traffic analysis is one of the essential approaches used in network security, and it is part of multiple disciplines of network security operations listed below:

Network Sniffing and Packet Analysis (Covered in Wireshark room)
Network Monitoring (Covered in Zeek room)
Intrusion Detection and Prevention (Covered in Snort room)
Network Forensics (Covered in NetworkMiner room)
Threat Hunting (Covered in Brim room)
There are two main techniques used in Traffic Analysis:

Flow Analysis	Packet Analysis
Collecting data/evidence from the networking devices. This type of analysis aims to provide statistical results through the data summary without applying in-depth packet-level investigation.

Advantage: Easy to collect and analyse.
Challenge: Doesn't provide full packet details to get the root cause of a case.
Collecting all available network data. Applying in-depth packet-level investigation (often called Deep Packet Inspection (DPI) ) to detect and block anomalous and malicious packets.

Advantage: Provides full packet details to get the root cause of a case.
Challenge: Requires time and skillset to analyse.
Benefits of the Traffic Analysis:

Provides full network visibility.
Helps comprehensive baselining for asset tracking.
Helps to detect/respond to anomalies and threats.
Does the Traffic Analysis Still Matter?

The widespread usage of security tools/services and an increasing shift to cloud computing force attackers to modify their tactics and techniques to avoid detection. Network data is a pure and rich data source. Even if it is encoded/encrypted, it still provides a value by pointing to an odd, weird or unexpected pattern/situation. Therefore traffic analysis is still a must-to-have skill for any security analyst who wants to detect and respond to advanced threats.

Now you know what Traffic Analysis is and how it operates. Now use the static site to simulate a traffic analysis operation and find the flags.

Answer the questions below
Level-1 is simulating the identification and filtering of malicious IP addresses.

What is the flag?

THM{PACKET_MASTER}

Correct Answer
Hint

What is the flag?
Click the black Start Network Traffic button.
<img width="545" height="397" alt="Screenshot 2025-09-12 at 4 29 44 PM" src="https://github.com/user-attachments/assets/584915c2-59a5-4b40-93fc-500b706ae5c3" />
You will see traffic running across the network, but uh-no we got malware!!! So a black button labeled Restore the Network and record the traffic for further investigation, click this button.
<img width="1432" height="780" alt="Screenshot 2025-09-12 at 4 28 19 PM" src="https://github.com/user-attachments/assets/9a768297-ad33-4a72-9069-a9691326c284" />
So we will have traffic run over the network again, this time we are getting logs of what is running over it. Once we have enough logs, you will be instructed to analyze the data to find two IP addresses to filter through the firewall. Looking through the IDS/IPS system, we can see a couple of suspicious IP addesses.
<img width="673" height="716" alt="Screenshot 2025-09-12 at 4 30 09 PM" src="https://github.com/user-attachments/assets/f277b1b0-7c39-4058-9dee-7f9eb6d65185" />
Highlight copy (ctrl + c) and paste (ctrl + v) or type the IP addresses into the Filter box, then click the blue Add to Filter.
<img width="606" height="426" alt="Screenshot 2025-09-12 at 4 30 26 PM" src="https://github.com/user-attachments/assets/e3dbe570-e166-4cc5-8e5b-4678c805b19e" />
Once you have added both of them, you will have a black Restart Network Traffic Button. Click it.
<img width="517" height="478" alt="Screenshot 2025-09-12 at 4 30 36 PM" src="https://github.com/user-attachments/assets/6c0bf0fe-aa30-4f5b-afaf-a900fc7267fa" />
After restarting the Network Traffic, you will have successfully block the malware. You will get a pop-up window, this window will contain the first flag. Type the answer into the TryHackMe answer field, then click submit.
<img width="311" height="243" alt="Screenshot 2025-09-12 at 4 30 51 PM" src="https://github.com/user-attachments/assets/f84255e3-cd77-4b6a-9694-b161860d66c3" />

Level-2 is simulating the identification and filtering of malicious IP and Port addresses.
Now we are tasked with blocking destination ports, we need to get these from the Traffic Analyzer table. If we look at the sus IP addresses from the previous question, along with number five, since it is labeled as Suspicious ARP Behavior. We can see the destination ports they correlate to in the Traffic Analyzer table on the right.
<img width="557" height="721" alt="Screenshot 2025-09-12 at 4 35 07 PM" src="https://github.com/user-attachments/assets/bbca05b6-2801-43e0-aebe-8f0619c5d443" />
Since we only need the port numbers, Highlight copy (ctrl + c) and paste (ctrl + v) or type, the port number into the Filter box, then click the blue Add to Filter.
<img width="548" height="727" alt="Screenshot 2025-09-12 at 4 35 30 PM" src="https://github.com/user-attachments/assets/46dee19b-5cfa-4d6f-bbcc-42b750018200" />
Once you have added all the ports, a black Restart Network Traffic button will apper. Click it.
<img width="538" height="471" alt="Screenshot 2025-09-12 at 4 35 42 PM" src="https://github.com/user-attachments/assets/2e85ab3b-b388-4801-b515-4dc08e56887e" />
After restarting the Network Traffic, you will have successfully block the malware. You will get a pop-up window, this window will contain the first flag. Type the answer into the TryHackMe answer field, then click submit.

<img width="272" height="215" alt="Screenshot 2025-09-12 at 4 35 48 PM" src="https://github.com/user-attachments/assets/13306f32-fb40-4dfa-af88-302e9cedfa7e" />
Task 4 Conclusion
Congratulations! You just finished the “Traffic Analysis Essentials” room.

In this room, we covered the foundations of the network security and traffic analysis concepts:

Network Security Operations
Network Traffic Analysis
Now, you are ready to complete the “Network Security and Traffic Analysis” module.

🎉🎉🎉CONGRAT!!!! You completed the Traffic Analysis Essentials Room🎉🎉🎉
