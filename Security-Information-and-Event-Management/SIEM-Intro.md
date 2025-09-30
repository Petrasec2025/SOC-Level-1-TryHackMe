<img width="1440" height="299" alt="Screenshot 2025-09-30 at 2 31 42 PM" src="https://github.com/user-attachments/assets/a913dd7c-aef7-42ec-9a65-9131374e4b6b" />
This my write-up for TryHackMe’s Introduction to SIEM, which provides an overview of what SIEM is, its significance, and how it works. I will explore fundamental concepts such as network visibility, log sources, and the analysis of logs and alerts. The objective is to gain an understanding of how SIEM protects networks and data, offering improved visibility, faster threat detection, and enhanced security outcomes.

Room link: Introduction to SIEM

Task 1: Introduction
A SIEM, which stands for Security Information and Event Management system, is a powerful tool that gathers data from multiple devices on a network, centralizes and stores it, and then performs analysis to identify correlations. This post will provide an overview of the fundamental concepts of SIEM and its functioning.

Learning Objective
Learning objectives covered in this room are:

What is SIEM, and how does it work?
Why is SIEM needed?
What is Network Visibility?
What are Log Sources, and how is log ingestion done?
What are the capabilities a SIEM provides?
Answer the questions below
What does SIEM stand for?
Answer: Security Information and Event Management system.

Task 2: Network Visibility through SIEM
In order to understand the significance of SIEM, let us first grasp the rationale behind the need for enhanced visibility of network activities. The diagram provided illustrates a basic network structure consisting of various Linux/Windows endpoints, a data server, and a website. Each element interacts with others or connects to the internet via a router.

Press enter or click to view image in full size
<img width="944" height="568" alt="Screenshot 2025-09-30 at 2 31 57 PM" src="https://github.com/user-attachments/assets/6e3cc5f5-c32b-4619-8763-61ba78be634a" />
As we know, each network component can have one or more log sources generating different logs. One example could be setting up Sysmon along with Windows Event logs to have better visibility of Windows Endpoint. We can divide our network log sources into two logical parts:

1) Host-Centric Log Sources
These are log sources that capture events that occurred within or related to the host. Some log sources that generate host-centric logs are Windows Event logs, Sysmon, Osquery, etc. Some examples of host-centric logs are:

A user accessing a file
A user attempting to authenticate.
A process Execution Activity
A process adding/editing/deleting a registry key or value.
Powershell execution
2) Network-Centric Log Sources
Network-related logs are generated when the hosts communicate with each other or access the internet to visit a website. Some network-based protocols are SSH, VPN, HTTP/s, FTP, etc. Examples of such events are:

SSH connection
A file being accessed via FTP
Web traffic
A user accessing company’s resources through VPN.
Network file sharing Activity
Importance of SIEM
<img width="404" height="433" alt="Screenshot 2025-09-30 at 2 32 13 PM" src="https://github.com/user-attachments/assets/987eb3cd-a5d4-468c-ad41-6eccc381471f" />
Now that we have covered various types of logs, it’s time to understand the importance of SIEM. As all these devices generate hundreds of events per second, examining the imglogs on each device one by one in case of any incident can be a tedious task. That is one of the advantages of having a SIEM solution in place. It not only takes logs from various sources in real-time but also provides the ability to correlate between events, search through the logs, investigate incidents and respond promptly. Some key features provided by SIEM are:

Real-time log Ingestion
Alerting against abnormal activities
24/7 Monitoring and visibility
Protection against the latest threats through early detection
Data Insights and visualization
Ability to investigate past incidents.
Answer the questions below
Is Registry-related activity host-centric or network-centric?
Answer: host-centric

Is VPN related activity host-centric or network-centric?
Answer: network-centric

Task 3: Log Sources and Log Ingestion
Every device in the network generates some kind of log whenever an activity is performed on it, like a user visiting a website, connecting to SSH, logging into his workstation, etc. Some common devices that are found in a network environment are discussed below:

Windows Machine
Windows records every event that can be viewed through the Event Viewer utility. It assigns a unique ID to each type of log activity, making it easy for the analyst to examine and keep track of. To view events in a Windows environment, type Event Viewer in the search bar, and it takes you to the tool where different logs are stored and can be viewed, as shown below. These logs from all windows endpoints are forwarded to the SIEM solution for monitoring and better visibility.

Linux
Linux OS stores all the related logs, such as events, errors, warnings, etc. Which are then ingested into SIEM for continuous monitoring. Some of the common locations where Linux store logs are:

/var/log/httpd : Contains HTTP Request / Response and error logs.
/var/log/cron : Events related to cron jobs are stored in this location.
/var/log/auth.log and /var/log/secure : Stores authentication related logs.
/var/log/kern : This file stores kernel related events.
Here is a sample of a cron log:
<img width="679" height="168" alt="Screenshot 2025-09-30 at 2 34 44 PM" src="https://github.com/user-attachments/assets/41aaf8eb-dcdb-4c5d-8d32-a1d192eea471" />
Web Server
It is important to keep an eye on all the requests/responses coming in and out of the webserver for any potential web attack attempt. In Linux, common locations to write all apache related logs are /var/log/apache or /var/log/httpd.

Here is an example of Apache Logs:

<img width="672" height="76" alt="Screenshot 2025-09-30 at 2 34 50 PM" src="https://github.com/user-attachments/assets/df292bc6-34f4-423f-b10c-858772dfc6db" />
<img width="729" height="567" alt="Screenshot 2025-09-30 at 2 35 00 PM" src="https://github.com/user-attachments/assets/8b2d0bca-2bd8-4cdd-875b-fce53373b6fc" />
All these logs provide a wealth of information and can help in identifying security issues. Each SIEM solution has its own way of ingesting the logs. Some common methods used by these SIEM solutions are explained below:

Agent / Forwarder: These SIEM solutions provide a lightweight tool called an agent (forwarder by Splunk) that gets installed in the Endpoint. It is configured to capture all the important logs and send them to the SIEM server.
Syslog: Syslog is a widely used protocol to collect data from various systems like web servers, databases, etc., are sent real-time data to the centralized destination.
Manual Upload: Some SIEM solutions, like Splunk, ELK, etc., allow users to ingest offline data for quick analysis. Once the data is ingested, it is normalized and made available for analysis.
Port-Forwarding: SIEM solutions can also be configured to listen on a certain port, and then the endpoints forward the data to the SIEM instance on the listening port.
An example of how Splunk provides various methods for log Ingestion is shown below:
<img width="680" height="209" alt="Screenshot 2025-09-30 at 2 35 09 PM" src="https://github.com/user-attachments/assets/93499e9d-9087-4356-8dea-167204f634ea" />


Answer the questions below
In which location within a Linux environment are HTTP logs are stored?
Answer: /var/log/httpd

Task 4: Why SIEM
SIEM is used to provide correlation on the collected data to detect threats. Once a threat is detected, or a certain threshold is crossed, an alert is raised. This alert enables the analysts to take suitable actions based on the investigation. SIEM plays an important role in the Cyber Security domain and helps detect and protect against the latest threats in a timely manner. It provides good visibility of what’s happening within the network infrastructure.

SIEM
SIEM is one major component of a Security Operations Center (SOC) ecosystem, as illustrated below. SIEM starts by collecting logs and examining if any event/flow has matched the condition set in the rule or crossed a certain threshold

Some of the common capabilities of SIEM are:

Correlation between events from different log sources.
Provide visibility on both Host-centric and Network-centric activities.
Allow analysts to investigate the latest threats and timely responses.
Hunt for threats that are not detected by the rules in place.
<img width="783" height="629" alt="Screenshot 2025-09-30 at 2 35 16 PM" src="https://github.com/user-attachments/assets/97f2dd0b-0272-45b0-bb69-a90ee0f2782b" />
SOC Analyst Responsibilities
SOC Analysts utilize SIEM solutions in order to have better visibility of what is happening within the network. Some of their responsibilities include:

Monitoring and Investigating.
Identifying False positives.
Tuning Rules which are causing the noise or False positives.
Reporting and Compliance.
Identifying blind spots in the network visibility and covering them.
Answer the questions below
Read the task above.

Task 5: Analysing Logs and Alerts
SIEM tool gets all the security-related logs ingested through agents, port forwarding, etc. Once the logs are ingested, SIEM looks for unwanted behavior or suspicious pattern within the logs with the help of the conditions set in the rules by the analysts. If the condition is met, a rule gets triggered, and the incident is investigated.

Dashboard
Dashboards are the most important components of any SIEM. SIEM presents the data for analysis after being normalized and ingested. The summary of these analyses is presented in the form of actionable insights with the help of multiple dashboards. Each SIEM solution comes with some default dashboards and provides an option for custom Dashboard creation. Some of the information that can be found in a dashboard are:

Alert Highlights
System Notification
Health Alert
List of Failed Login Attempts
Events Ingested Count
Rules triggered
Top Domains Visited
An example of a Default dashboard in Qradar SIEM is shown below:
<img width="669" height="337" alt="Screenshot 2025-09-30 at 2 35 25 PM" src="https://github.com/user-attachments/assets/22176a50-5cfd-43db-9289-4a31f58815ea" />
Correlation Rules
Correlation rules play an important role in the timely detection of threats allowing analysts to take action on time. Correlation rules are pretty much logical expressions set to be triggered. A few examples of correlation rules are:

If a User gets 5 failed Login Attempts in 10 seconds — Raise an alert for Multiple Failed Login Attempts
If login is successful after multiple failed login attempts — Raise an alert for Successful Login After multiple Login Attempts
A rule is set to alert every time a user plugs in a USB (Useful if USB is restricted as per the company policy)
If outbound traffic is > 25 MB — Raise an alert to potential Data exfiltration Attempt (Usually, it depends on the company policy)
How a correlation rule is created
To explain how the rule works, consider the following Eventlog use cases:

Use-Case 1:

Adversaries tend to remove the logs during the post-exploitation phase to remove their tracks. A unique Event ID 104 is logged every time a user tries to remove or clear event logs. To create a rule based on this activity, we can set the condition as follows:

Rule: If the Log source is WinEventLog AND EventID is 104 — Trigger an alert Event Log Cleared

Use-Case 2: Adversaries use commands like whoami after the exploitation/privilege escalation phase. The following Fields will be helpful to include in the rule.

Log source: Identify the log source capturing the event logs
Event ID: which Event ID is associated with Process Execution activity? In this case, event id 4688 will be helpful.
NewProcessName: which process name will be helpful to include in the rule?
**Rule:**If Log Source is WinEventLog AND EventCode is 4688, and NewProcessName contains whoami, then Trigger an ALERT WHOAMI command Execution DETECTED

In the previous task, the importance of field-value pairs was discussed. Correlation rules keep an eye on the values of certain fields to get triggered. That is the reason why it is important to have normalized logs ingested.

Alert Investigation
When monitoring SIEM, analysts spend most of their time on dashboards as it displays various key details about the network in a very summarized way. Once an alert is triggered, the events/flows associated with the alert are examined, and the rule is checked to see which conditions are met. Based on the investigation, the analyst determines if it’s a True or False positive. Some of the actions that are performed after the analysis are:

Alert is False Alarm. It may require tuning the rule to avoid similar False positives from occurring again.
Alert is True Positive. Perform further investigation.
Contact the asset owner to inquire about the activity.
Suspicious activity is confirmed. Isolate the infected host.
Block the suspicious IP.
Let’s move on to the next task and explore how SIEM works.

Answer the questions below
Which Event ID is generated when event logs are removed?
Answer: 104

What type of alert may require tuning?
Answer: false alarms

Task 6: Lab Work
Lab Work
Click on the View Site button, which will display the lab on the right side of the screen.

In the static lab attached, a sample dashboard and events are displayed. When a suspicious activity happens, an Alert is triggered, which means some events match the condition of some rule already configured. Complete the lab and answer the following questions.
<img width="683" height="693" alt="Screenshot 2025-09-30 at 2 35 37 PM" src="https://github.com/user-attachments/assets/e56b8adc-8890-4613-83cc-f8f607cb8fdf" />
Click on “Start Suspicious Activity”
<img width="685" height="706" alt="Screenshot 2025-09-30 at 2 35 50 PM" src="https://github.com/user-attachments/assets/d48629bb-b6ce-4c2c-9776-a177efbe3ae4" />
Answer the questions below
Click on Start Suspicious Activity, which process caused the alert?
Answer: cudominer.exe
<img width="679" height="637" alt="Screenshot 2025-09-30 at 2 35 59 PM" src="https://github.com/user-attachments/assets/b9ba5a40-d7db-4692-9076-37d599a27dba" />
cudominer.exe process is highlighted which is very suspicious.
<img width="681" height="611" alt="Screenshot 2025-09-30 at 2 36 08 PM" src="https://github.com/user-attachments/assets/7f655cd7-bf96-4074-8598-d0b9ffbd775b" />
Navigate to the event logs and locate the event that triggered the alert.
<img width="677" height="493" alt="Screenshot 2025-09-30 at 2 36 16 PM" src="https://github.com/user-attachments/assets/81c253ac-4245-4853-9a13-c723d6cbbb07" />
Below shows where the suspicious process is.
<img width="685" height="503" alt="Screenshot 2025-09-30 at 2 36 23 PM" src="https://github.com/user-attachments/assets/34877b6f-c418-4473-bcbd-6f2ceb8ec719" />
Click on the event to get more details.
<img width="670" height="498" alt="Screenshot 2025-09-30 at 2 36 33 PM" src="https://github.com/user-attachments/assets/77a5d2f5-7159-4652-acb0-dbbe5e0b5100" />
Next is to click on the rule ID that triggered the alert.
<img width="671" height="504" alt="Screenshot 2025-09-30 at 2 36 42 PM" src="https://github.com/user-attachments/assets/0e289d2f-c7d6-495d-9d95-d63ed986711c" />
The following shows the rule.
<img width="675" height="321" alt="Screenshot 2025-09-30 at 2 36 56 PM" src="https://github.com/user-attachments/assets/3ed77a7a-ad28-40a0-b0bb-89768a844f4c" />
Following the next task to be taken is to decide whether the alert was True-positive or False-positive and take corrective response.
<img width="674" height="320" alt="Screenshot 2025-09-30 at 2 37 02 PM" src="https://github.com/user-attachments/assets/30176906-4f8a-475a-8d87-972fb97a609f" />
Based from the information gathered, the alert is categorized as True-positive
<img width="675" height="237" alt="Screenshot 2025-09-30 at 2 37 10 PM" src="https://github.com/user-attachments/assets/8e0b8dde-d52f-47ad-b5ba-00e121e02839" />
<img width="679" height="227" alt="Screenshot 2025-09-30 at 2 37 16 PM" src="https://github.com/user-attachments/assets/d4e99ed4-9d0c-462f-9d9d-7f7855f50ad6" />

Find the event that caused the alert, which user was responsible for the process execution?
Answer: Christ.fort

What is the hostname of the suspect user?
Answer: HR_02

Examine the rule and the suspicious process; which term matched the rule that caused the alert?
Answer: miner

What is the best option that represents the event? Choose from the following:
False-Positive
True-Positive
Answer: True-Positive

Selecting the right ACTION will display the FLAG. What is the FLAG?
Answer: THM{000_SIEM_INTRO}

Task 7: Conclusion
This room provides comprehensive information on SIEM, including its capabilities and the visibility it offers. For a more thorough understanding of incident investigations, available resources include various rooms and challenges.

Jr. SOC Analyst
Splunk101
Splunk201
Benign
InvestigatingwithSplunk
InvestgatingwithELK
ItsyBitsy
Answer the questions below
Complete this room.

SIEM platforms play a vital role in network security, aiding in the identification of potential incidents and constant monitoring of activities. This post explores essential principles and elements of SIEM solutions. It touches on processes such as log collection, data normalization, and the establishment of correlation rules to effectively identify threats. Dashboards provide valuable insights, while the ability to delve deeper into events aids in incident response.

Thank you for reading. Until next time :-)



