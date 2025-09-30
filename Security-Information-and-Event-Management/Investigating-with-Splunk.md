<img width="1227" height="272" alt="Screenshot 2025-09-30 at 3 56 56 PM" src="https://github.com/user-attachments/assets/2f8142b8-4c80-4182-ac5e-2495a2ecdeb8" />
This room by TryHackMe explores the process of investigating a compromised web server using Splunk SIEM. It focuses on analyzing various Windows data sources such as Sysmon, PowerShell, and event logs to identify indicators of compromise (IOCs). By correlating events, analyzing fields, and pivoting data, anomalies can be detected and the attacker’s actions can be reconstructed. This exercise aims to improve log analysis skills for efficient threat detection and response.

Room link: Investigating with Splunk

Task 1 Investigating with Splunk
SOC Analyst Johny has observed some anomalous behaviours in the logs of a few windows machines. It looks like the adversary has access to some of these machines and successfully created some backdoor. His manager has asked him to pull those logs from suspected hosts and ingest them into Splunk for quick investigation. Our task as SOC Analyst is to examine the logs and identify the anomalies.

To learn more about Splunk and how to investigate the logs, look at the rooms splunk101 and splunk201.

Room MachineBefore moving forward, deploy the machine. When you deploy the machine, it will be assigned an IP Machine IP: MACHINE_IP. You can visit this IP from the VPN or the Attackbox. The machine will take up to 3-5 minutes to start. All the required logs are ingested in the index main.

Answer the questions below
How many events were collected and Ingested in the index main?
Answer: 12256

Query the “main” index.
<img width="647" height="72" alt="Screenshot 2025-09-30 at 3 58 55 PM" src="https://github.com/user-attachments/assets/811b4c74-5577-43d1-b848-deff0c212e4d" />
<img width="635" height="266" alt="Screenshot 2025-09-30 at 3 59 02 PM" src="https://github.com/user-attachments/assets/4c28cd50-c712-4510-aa4a-f986c6331522" />

On one of the infected hosts, the adversary was successful in creating a backdoor user. What is the new username?
Answer: A1berto

Event ID 4720 is logged when a user account is created.
<img width="676" height="66" alt="Screenshot 2025-09-30 at 3 59 10 PM" src="https://github.com/user-attachments/assets/9821106a-7eb5-4650-88f5-e7d62e2e325c" />
<img width="682" height="289" alt="Screenshot 2025-09-30 at 3 59 21 PM" src="https://github.com/user-attachments/assets/152d0ed6-57ae-40bc-993b-cd7e384a86cb" />
<img width="685" height="386" alt="Screenshot 2025-09-30 at 3 59 43 PM" src="https://github.com/user-attachments/assets/d206dee1-dec7-439f-8f46-077ac7023d9e" />

On the same host, a registry key was also updated regarding the new backdoor user. What is the full path of that registry key?
Answer: HKLM\SAM\SAM\Domains\Account\Users\Names\A1berto

This would query to Sysmon events that logged modifications of a registry value.

<img width="637" height="76" alt="Screenshot 2025-09-30 at 3 59 50 PM" src="https://github.com/user-attachments/assets/7ac0436e-71ed-4dd7-b039-4aebadeaa037" />
<img width="649" height="128" alt="Screenshot 2025-09-30 at 3 59 56 PM" src="https://github.com/user-attachments/assets/c2b46911-b3b8-47f2-96b0-684b908df212" />
Click on the “TargetObject” field to display the value of the object that was modified.
<img width="603" height="287" alt="Screenshot 2025-09-30 at 4 00 06 PM" src="https://github.com/user-attachments/assets/f94ffe78-c71c-49f8-82b1-a3c87c598577" />
Examine the logs and identify the user that the adversary was trying to impersonate.
Answer: Alberto
<img width="673" height="71" alt="Screenshot 2025-09-30 at 4 00 13 PM" src="https://github.com/user-attachments/assets/9328f1c3-86d4-4c48-9f0c-befc4b7b2126" />

The names of users are found in the “User” field. The newly created user “A1berto” is not the same as “Alberto”; therefore, “Alberto” is being impersonated.
<img width="687" height="280" alt="Screenshot 2025-09-30 at 4 00 21 PM" src="https://github.com/user-attachments/assets/406a2ade-4be8-4b54-a735-a18863f79edb" />
What is the command used to add a backdoor user from a remote computer?
Answer: C:\windows\System32\Wbem\WMIC.exe” /node:WORKSTATION6 process call create “net user /add A1berto paw0rd1

Filter events with ID of 4688 of Sysmon event ID of 1.
<img width="680" height="80" alt="Screenshot 2025-09-30 at 4 00 28 PM" src="https://github.com/user-attachments/assets/d4b6d261-5fef-458a-9f1a-852048d4674a" />
Select the “CommandLine” field. Of the values, the first set of commands is a command a remote user would used because the “wmic” is a command-line tool which can be leveraged for remote execution of commands.
<img width="590" height="416" alt="Screenshot 2025-09-30 at 4 00 37 PM" src="https://github.com/user-attachments/assets/6f6752cf-1965-458b-8812-0e9d45ffeb41" />
<img width="685" height="530" alt="Screenshot 2025-09-30 at 4 00 45 PM" src="https://github.com/user-attachments/assets/9cbe03dc-47d0-4955-9a3e-f5f96081fd7d" />
How many times was the login attempt from the backdoor user observed during the investigation?
Answer: 0

The query will filter events where successful and failed account logon attempts were made by the backdoor user.
<img width="667" height="68" alt="Screenshot 2025-09-30 at 4 00 53 PM" src="https://github.com/user-attachments/assets/d256fb88-11e7-46ca-b647-811b2e46b7be" />
<img width="925" height="575" alt="Screenshot 2025-09-30 at 4 01 01 PM" src="https://github.com/user-attachments/assets/b1467adb-a3dd-4d85-8ea7-ba08ed1813cf" />
<img width="683" height="226" alt="Screenshot 2025-09-30 at 4 01 12 PM" src="https://github.com/user-attachments/assets/ccfbfc0b-c21d-4175-aad7-d15bd1f3b05a" />
What is the name of the infected host on which suspicious Powershell commands were executed?
Answer: James.browne
The following query would filter Powershell events.
<img width="681" height="76" alt="Screenshot 2025-09-30 at 4 01 19 PM" src="https://github.com/user-attachments/assets/46cda3b3-7fce-42d4-b4df-3e92ef1d6a7b" />
Only one host was identified where the PowerShell commands were executed
<img width="804" height="696" alt="Screenshot 2025-09-30 at 4 01 26 PM" src="https://github.com/user-attachments/assets/56a98e37-94ef-4a7c-944b-ddfa98a19aa5" />

Reference: Logging Powershell activities

PowerShell logging is enabled on this device. How many events were logged for the malicious PowerShell execution?
Answer: 79
Using the same query from the previous question, there were 79 PowerShell activities that were monitored.
<img width="546" height="216" alt="Screenshot 2025-09-30 at 4 01 33 PM" src="https://github.com/user-attachments/assets/d5882932-5fed-4784-8dd4-243f43bb8e93" />

An encoded Powershell script from the infected host initiated a web request. What is the full URL?
Answer: hxxp[://]10[.]10[.]10[.]5/news[.]php

The modified query will extract the value of “Host Application” from the field “ContextInfo”, present it on a table without duplicate commands

<img width="677" height="140" alt="Screenshot 2025-09-30 at 4 01 40 PM" src="https://github.com/user-attachments/assets/58e4a46b-29bd-4d69-93dd-0c71bd69029a" />

There is only one command value and it is base64 encoded.
<img width="682" height="203" alt="Screenshot 2025-09-30 at 4 01 52 PM" src="https://github.com/user-attachments/assets/5d9f8ebf-8453-4273-bc11-3982d3e3f1ee" />
Copied the encoded value and decoded it in cyberchef.
<img width="681" height="646" alt="Screenshot 2025-09-30 at 4 02 02 PM" src="https://github.com/user-attachments/assets/0488e264-ce91-441c-b6a4-7e44129a853d" />
The decoded strings included a script to modify the PowerShell script block logging setting. Additionally, there seems to be a base64-encoded value that may refer to a domain name or an IP address, given that “/news.php” could be a URL or subdirectory.

Copied the value of the base64 string, decoded them, then defanged the output. So the base64 encoded string refers to an IP address.
<img width="680" height="357" alt="Screenshot 2025-09-30 at 4 02 11 PM" src="https://github.com/user-attachments/assets/2971f842-71e9-415b-983d-8681177e9fe0" />

References
ultimatewindowssecurity

Logging Powershell activities

Sysmon
