<img width="1368" height="268" alt="Screenshot 2025-09-06 at 6 39 25 PM" src="https://github.com/user-attachments/assets/5ea5afa0-7942-438b-b6d0-a21a7a65e7b2" />

Explore different OSINT tools used to conduct security threat assessments and investigations.

Task 1 Room Outline
This room will cover the concepts of Threat Intelligence and various open-source tools that are useful. The learning objectives include:

Understanding the basics of threat intelligence & its classifications.
Using UrlScan.io to scan for malicious URLs.
Using Abuse.ch to track malware and botnet indicators.
Investigate phishing emails using PhishTool
Using Cisco’s Talos Intelligence platform for intel gathering.
Task 2 Threat Intelligence
Threat Intelligence is the analysis of data and information using tools and techniques to generate meaningful patterns on how to mitigate against potential risks associated with existing or emerging threats targeting organisations, industries, sectors or governments.

To mitigate against risks, we can start by trying to answer a few simple questions:

Who’s attacking you?
What’s their motivation?
What are their capabilities?
What artefacts and indicators of compromise should you look out for?
Threat Intelligence Classifications:
<img width="552" height="556" alt="Screenshot 2025-09-06 at 6 42 31 PM" src="https://github.com/user-attachments/assets/c8d63601-08fb-4d7c-983c-d2ebbff80ac8" />
Threat Intel is geared towards understanding the relationship between your operational environment and your adversary. With this in mind, we can break down threat intel into the following classifications:

Strategic Intel: High-level intel that looks into the organisation’s threat landscape and maps out the risk areas based on trends, patterns and emerging threats that may impact business decisions.
Technical Intel: Looks into evidence and artefacts of attack used by an adversary. Incident Response teams can use this intel to create a baseline attack surface to analyse and develop defence mechanisms.
Tactical Intel: Assesses adversaries’ tactics, techniques, and procedures (TTPs). This intel can strengthen security controls and address vulnerabilities through real-time investigations.
Operational Intel: Looks into an adversary’s specific motives and intent to perform an attack. Security teams may use this intel to understand the critical assets available in the organisation (people, processes, and technologies) that may be targeted.
Task 3 UrlScan.io
Urlscan.io is a free service developed to assist in scanning and analysing websites. It is used to automate the process of browsing and crawling through websites to record activities and interactions.
<img width="785" height="581" alt="Screenshot 2025-09-06 at 6 43 23 PM" src="https://github.com/user-attachments/assets/b5ace4b2-6fb2-4b67-b45f-cab4a58a4ea5" />
<img width="772" height="627" alt="Screenshot 2025-09-06 at 6 43 16 PM" src="https://github.com/user-attachments/assets/7068b20f-a347-414e-a72e-b68296973a90" />

Scan Results
URL scan results provide ample information, with the following key areas being essential to look at:

Summary: Provides general information about the URL, ranging from the identified IP address, domain registration details, page history and a screenshot of the site.
HTTP: Provides information on the HTTP connections made by the scanner to the site, with details about the data fetched and the file types received.
Redirects: Shows information on any identified HTTP and client-side redirects on the site.
Links: Shows all the identified links outgoing from the site's homepage.
Behaviour: Provides details of the variables and cookies found on the site. These may be useful in identifying the frameworks used in developing the site.
Indicators: Lists all IPs, domains and hashes associated with the site. These indicators do not imply malicious activity related to the site.
<img width="1360" height="763" alt="Screenshot 2025-09-06 at 6 44 18 PM" src="https://github.com/user-attachments/assets/81a69748-5bb2-4e7d-a3c1-eb3398aed1a9" />

Note: Due to the dynamic nature of internet activities, data searched can produce different results on different days as new information gets updated.

Scenario
You have been tasked to perform a scan on TryHackMe's domain. The results obtained are displayed in the image below. Use the details on the image to answer the questions:

<img width="1360" height="763" alt="Screenshot 2025-09-06 at 6 44 18 PM" src="https://github.com/user-attachments/assets/f119e976-57d9-4d2f-8df7-493a2b27482c" />

When a URL is submitted, the information recorded includes the domains and IP addresses contacted, resources requested from the domains, a snapshot of the web page, technologies utilised and other metadata about the website.

The site provides two views, the first one showing the most recent scans performed and the second one showing current live scans.
Answer the questions below
The answers can be found in the screen shot above, so I won’t be posting the answers. Follow along so that you can better find the answer if you are not sure.

What is TryHackMe’s Cisco Umbrella Rank?
This answer can be found under the Summary section, if you look towards the end. Once you find it, type it into the Answer field on TryHackMe, then click submit.
<img width="531" height="143" alt="Screenshot 2025-09-06 at 6 46 31 PM" src="https://github.com/user-attachments/assets/70d75ea6-4973-4589-a03a-a04a9154524c" />
How many domains did UrlScan.io identify?
This answer can be found under the Summary section, it can be found in the first sentence. Once you find it, type it into the Answer field on TryHackMe, then click submit.
<img width="628" height="155" alt="Screenshot 2025-09-06 at 6 46 36 PM" src="https://github.com/user-attachments/assets/bc3556d4-86d4-41d9-8100-09602b1aa455" />
What is the main domain registrar listed?
Move down to the Live Information section, this answer can be found in the last line of this section. Once you find it, type it into the Answer field on TryHackMe, then click submit.
<img width="496" height="116" alt="Screenshot 2025-09-06 at 6 46 41 PM" src="https://github.com/user-attachments/assets/5ff42e6b-d336-486c-84ec-77bd328eb26a" />
What is the main IP address identified?
This answer can be found under the Summary section, it can be found in the second sentence. Once you find it, type it into the Answer field on TryHackMe, then click submit.
<img width="540" height="143" alt="Screenshot 2025-09-06 at 6 46 47 PM" src="https://github.com/user-attachments/assets/e670c803-589b-4f22-8bcb-1e8650c18a7f" />

You have finished these tasks and can now move onto Task 4 Abuse.ch, Task 5 PhishTool, & Task 6 Cisco Talos Intelligence.


