# Investigating with Splunk Room Walkthrough

![Room Banner](https://github.com/user-attachments/assets/2f8142b8-4c80-4182-ac5e-2495a2ecdeb8)

## 🏆 Badges
![SIEM](https://img.shields.io/badge/SIEM-Splunk_Investigation-0078D6?style=for-the-badge&logo=splunk&logoColor=white)
![Incident Response](https://img.shields.io/badge/Incident_Response-Windows_Forensics-00C800?style=for-the-badge&logo=shield&logoColor=white)
![Difficulty](https://img.shields.io/badge/Difficulty-Intermediate-FFA500?style=for-the-badge)
![Platform](https://img.shields.io/badge/Platform-TryHackMe-FF0000?style=for-the-badge&logo=tryhackme&logoColor=white)
![Completion](https://img.shields.io/badge/Completion-100%25-00FF00?style=for-the-badge)
![Forensics](https://img.shields.io/badge/Forensics-Log_Analysis-800080?style=for-the-badge)

## Overview
This room by TryHackMe explores the process of investigating a compromised web server using Splunk SIEM. It focuses on analyzing various Windows data sources such as Sysmon, PowerShell, and event logs to identify indicators of compromise (IOCs). By correlating events, analyzing fields, and pivoting data, anomalies can be detected and the attacker's actions can be reconstructed. This exercise aims to improve log analysis skills for efficient threat detection and response.

**Room link:** [Investigating with Splunk](https://tryhackme.com/room/investigatingwithsplunk)

---

## Task 1 Investigating with Splunk

SOC Analyst Johny has observed some anomalous behaviours in the logs of a few windows machines. It looks like the adversary has access to some of these machines and successfully created some backdoor. His manager has asked him to pull those logs from suspected hosts and ingest them into Splunk for quick investigation. Our task as SOC Analyst is to examine the logs and identify the anomalies.

To learn more about Splunk and how to investigate the logs, look at the rooms splunk101 and splunk201.

### Room Machine
Before moving forward, deploy the machine. When you deploy the machine, it will be assigned an IP Machine IP: MACHINE_IP. You can visit this IP from the VPN or the Attackbox. The machine will take up to 3-5 minutes to start. All the required logs are ingested in the index main.

### Answer the questions below

#### How many events were collected and Ingested in the index main?
**Answer:** `12256`

Query the "main" index.

![Main Index Query](https://github.com/user-attachments/assets/811b4c74-5577-43d1-b848-deff0c212e4d)

![Event Count](https://github.com/user-attachments/assets/4c28cd50-c712-4510-aa4a-f986c6331522)

#### On one of the infected hosts, the adversary was successful in creating a backdoor user. What is the new username?
**Answer:** `A1berto`

Event ID 4720 is logged when a user account is created.

![User Account Creation Query](https://github.com/user-attachments/assets/9821106a-7eb5-4650-88f5-e7d62e2e325c)

![User Account Events](https://github.com/user-attachments/assets/152d0ed6-57ae-40bc-993b-cd7e384a86cb)

![Backdoor User](https://github.com/user-attachments/assets/d206dee1-dec7-439f-8f46-077ac7023d9e)

#### On the same host, a registry key was also updated regarding the new backdoor user. What is the full path of that registry key?
**Answer:** `HKLM\SAM\SAM\Domains\Account\Users\Names\A1berto`

This would query to Sysmon events that logged modifications of a registry value.

![Registry Modification Query](https://github.com/user-attachments/assets/7ac0436e-71ed-4dd7-b039-4aebadeaa037)

![Registry Events](https://github.com/user-attachments/assets/c2b46911-b3b8-47f2-96b0-684b908df212)

Click on the "TargetObject" field to display the value of the object that was modified.

![TargetObject Field](https://github.com/user-attachments/assets/f94ffe78-c71c-49f8-82b1-a3c87c598577)

#### Examine the logs and identify the user that the adversary was trying to impersonate.
**Answer:** `Alberto`

![User Impersonation Query](https://github.com/user-attachments/assets/9328f1c3-86d4-4c48-9f0c-befc4b7b2126)

The names of users are found in the "User" field. The newly created user "A1berto" is not the same as "Alberto"; therefore, "Alberto" is being impersonated.

![User Field Analysis](https://github.com/user-attachments/assets/406a2ade-4be8-4b54-a735-a18863f79edb)

#### What is the command used to add a backdoor user from a remote computer?
**Answer:** `C:\windows\System32\Wbem\WMIC.exe" /node:WORKSTATION6 process call create "net user /add A1berto paw0rd1`

Filter events with ID of 4688 of Sysmon event ID of 1.

![Process Creation Query](https://github.com/user-attachments/assets/d4b6d261-5fef-458a-9f1a-852048d4674a)

Select the "CommandLine" field. Of the values, the first set of commands is a command a remote user would used because the "wmic" is a command-line tool which can be leveraged for remote execution of commands.

![CommandLine Field](https://github.com/user-attachments/assets/6f6752cf-1965-458b-8812-0e9d45ffeb41)

![Remote Command](https://github.com/user-attachments/assets/9cbe03dc-47d0-4955-9a3e-f5f96081fd7d)

#### How many times was the login attempt from the backdoor user observed during the investigation?
**Answer:** `0`

The query will filter events where successful and failed account logon attempts were made by the backdoor user.

![Login Attempt Query](https://github.com/user-attachments/assets/d256fb88-11e7-46ca-b647-811b2e46b7be)

![Login Events](https://github.com/user-attachments/assets/b1467adb-a3dd-4d85-8ea7-ba08ed1813cf)

![No Login Attempts](https://github.com/user-attachments/assets/ccfbfc0b-c21d-4175-aad7-d15bd1f3b05a)

#### What is the name of the infected host on which suspicious Powershell commands were executed?
**Answer:** `James.browne`

The following query would filter Powershell events.

![PowerShell Query](https://github.com/user-attachments/assets/46cda3b3-7fce-42d4-b4df-3e92ef1d6a7b)

Only one host was identified where the PowerShell commands were executed.

![Infected Host](https://github.com/user-attachments/assets/56a98e37-94ef-4a7c-944b-ddfa98a19aa5)

**Reference:** [Logging Powershell activities](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_logging_windows?view=powershell-7.3)

#### PowerShell logging is enabled on this device. How many events were logged for the malicious PowerShell execution?
**Answer:** `79`

Using the same query from the previous question, there were 79 PowerShell activities that were monitored.

![PowerShell Event Count](https://github.com/user-attachments/assets/d5882932-5fed-4784-8dd4-243f43bb8e93)

#### An encoded Powershell script from the infected host initiated a web request. What is the full URL?
**Answer:** `hxxp[://]10[.]10[.]10[.]5/news[.]php`

The modified query will extract the value of "Host Application" from the field "ContextInfo", present it on a table without duplicate commands.

![Encoded PowerShell Query](https://github.com/user-attachments/assets/58e4a46b-29bd-4d69-93dd-0c71bd69029a)

There is only one command value and it is base64 encoded.

![Base64 Encoded Command](https://github.com/user-attachments/assets/5d9f8ebf-8453-4273-bc11-3982d3e3f1ee)

Copied the encoded value and decoded it in cyberchef.

![CyberChef Decoding](https://github.com/user-attachments/assets/0488e264-ce91-441c-b6a4-7e44129a853d)

The decoded strings included a script to modify the PowerShell script block logging setting. Additionally, there seems to be a base64-encoded value that may refer to a domain name or an IP address, given that "/news.php" could be a URL or subdirectory.

Copied the value of the base64 string, decoded them, then defanged the output. So the base64 encoded string refers to an IP address.

![URL Decoding](https://github.com/user-attachments/assets/2971f842-71e9-415b-983d-8681177e9fe0)

---

## 🎯 Final Badges
![Backdoor](https://img.shields.io/badge/Backdoor-User_Creation-FF69B4?style=for-the-badge)
![PowerShell](https://img.shields.io/badge/PowerShell-Malicious_Scripts-000080?style=for-the-badge)
![Room](https://img.shields.io/badge/Room-Investigating_with_Splunk-FF4500?style=for-the-badge)
![Registry](https://img.shields.io/badge/Registry-Modification-008080?style=for-the-badge)

## Conclusion

This investigation demonstrated comprehensive log analysis skills using Splunk SIEM to identify various attack techniques including backdoor user creation, registry modification, PowerShell script execution, and remote command execution. The exercise highlighted the importance of correlating events from multiple data sources (Windows Event Logs, Sysmon, PowerShell logs) to reconstruct the attacker's activities and identify indicators of compromise.

### Key Investigation Findings:
- Backdoor user "A1berto" created to impersonate legitimate user "Alberto"
- Registry modifications to establish persistence
- Remote command execution using WMIC
- PowerShell script execution with encoded commands
- Web requests to suspicious IP addresses

The room provided excellent practical experience in Windows forensics and SIEM investigation techniques, reinforcing the importance of comprehensive logging and systematic analysis in incident response.

---

**Room Link:** [https://tryhackme.com/room/investigatingwithsplunk](https://tryhackme.com/room/investigatingwithsplunk)

### References
- [Ultimate Windows Security](https://www.ultimatewindowssecurity.com/)
- [Logging PowerShell activities](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_logging_windows?view=powershell-7.3)
- [Sysmon Documentation](https://docs.microsoft.com/en-us/sysinternals/downloads/sysmon)
