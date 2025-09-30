# Monday Monitor Room Walkthrough

![Room Banner](https://github.com/user-attachments/assets/20bad875-6ea0-4245-b75a-87749eff9187)

## 🏆 Badges
![Incident Response](https://img.shields.io/badge/Incident_Response-Forensics-0078D6?style=for-the-badge&logo=shield&logoColor=white)
![SIEM](https://img.shields.io/badge/SIEM-Wazuh_Analysis-00C800?style=for-the-badge&logo=search&logoColor=white)
![Difficulty](https://img.shields.io/badge/Difficulty-Intermediate-FFA500?style=for-the-badge)
![Platform](https://img.shields.io/badge/Platform-TryHackMe-FF0000?style=for-the-badge&logo=tryhackme&logoColor=white)
![Completion](https://img.shields.io/badge/Completion-100%25-00FF00?style=for-the-badge)
![Monitoring](https://img.shields.io/badge/Monitoring-Endpoint_Security-800080?style=for-the-badge)

## Scenario
Swiftspend Finance, the coolest fintech company in town, is on a mission to level up its cyber security game to keep those digital adversaries at bay and ensure their customers stay safe and sound.

Led by the tech-savvy Senior Security Engineer John Sterling, Swiftspend's latest project is about beefing up their endpoint monitoring using Wazuh and Sysmon. They've been running some tests to see how well their cyber guardians can sniff out trouble. And guess what? You're the cyber sleuth they've called in to crack the code!

The tests were run on Apr 29, 2024, between 12:00:00 and 20:00:00.

As you dive into the logs, you'll look for any suspicious process shenanigans or weird network connections, you name it! Your mission? Unravel the mysteries within the logs and dish out some epic insights to fine-tune Swiftspend's defences.

## Machine Access
Click the Start Machine button attached to this task to start the VM. Give the machine about 5 minutes to fully set up the environment. Access the Wazuh Dashboard using your browser at https://10-10-166-179.p.thmlabs.com and use the credentials listed below:

![Wazuh Credentials](https://github.com/user-attachments/assets/d8e87f06-f429-45de-bb00-c7e8e6c8be5b)

Once logged in, navigate to the Security events module and use the saved query Monday_Monitor to access the logs.

Okay, so we understand that we need to use the Wazuh software to complete this task. First, as stated in the scenario, we need to monitor events between 12:00 and 20:00 on April 29, 2024. Therefore, we must configure the settings to reflect this specific date and time.

![Time Configuration](https://github.com/user-attachments/assets/0646f1e8-7cb0-42e2-8415-575191cca932)

![Date Selection](https://github.com/user-attachments/assets/ee9e4284-f902-45a2-bdb6-36517377efb2)

Lastly, please don't forget to access the Monday_monitor queries that have been saved by the system.

![Monday Monitor Query](https://github.com/user-attachments/assets/5857135b-a677-4f86-bfc3-52beff9a7d3a)

Let's dive into the question, shall we?

---

## Question 1: Initial access was established using a downloaded file. What is the file name saved on the host?

**A:** `SwiftSpend_Financial_Expenses.xlsm`

I understand that the first question might be a bit confusing at first glance. But don't worry, we'll figure it out together.

Firstly, the question asks for the file name saved on the host. To find this, you should navigate to: Events → search bar (localhost).

![Localhost Search](https://github.com/user-attachments/assets/e4a05bc4-4c98-44e5-abc1-1fbad59bd025)

You will see three hits displayed above the table. Please direct your attention to the top document.

![Top Document](https://github.com/user-attachments/assets/0e86bdb3-0b41-4c4e-8b6f-c02cacd27892)

Then, you will find the answer in the data.win.event.data.commandLine section.

![Command Line Data](https://github.com/user-attachments/assets/3fbdcbc4-9695-445a-9c9a-05e99d26545c)

---

## Question 2: What is the full command run to create a scheduled task?

**A:** `"cmd.exe" /c "reg add HKCU\\SOFTWARE\\ATOMIC-T1053.005 /v test /t REG_SZ /d cGluZyB3d3cueW91YXJldnVsbmVyYWJsZS50aG0= /f & schtasks.exe /Create /F /TN "ATOMIC-T1053.005" /TR "cmd /c start /min \\"\\" powershell.exe -Command IEX([System.Text.Encoding]::ASCII.GetString([System.Convert]::FromBase64String((Get-ItemProperty -Path HKCU:\\\\SOFTWARE\\\\ATOMIC-T1053.005).test)))" /sc daily /st 12:34`

As we learned in the Wazuh module, you can search for 'scheduler' in the search bar. To find the full command used to create the scheduled task, add the filter data.win.eventdata.parentCommandLine, which will display the complete command.

![Scheduler Search](https://github.com/user-attachments/assets/4b04ca11-a41e-48f2-8a36-560955d048ef)

Then, you'll find that one of the documents contains a lengthy command.

![Scheduled Task Command](https://github.com/user-attachments/assets/d4edb771-beb6-4856-b70e-5e0110af9cd3)

So, there they are!

![Full Command](https://github.com/user-attachments/assets/3502e21e-8697-458a-82c8-d8844cfb821f)

---

## Question 3: What time is the scheduled task meant to run?

**A:** `12:34`

This one is quite simple. Scroll up a bit, and you'll find the answer in the original data.win.eventdata.CommandLine fields.

![Scheduled Task Time](https://github.com/user-attachments/assets/92e42e5e-1da0-4d7e-88f5-75b85f1c1065)

---

## Question 4: What was encoded?

**A:** `ping www.youarevulnerable.thm`

This one might seem a bit confusing, but it's actually quite straightforward. Notice that the data.win.eventdata.parentCommandLine field contains a long string with seemingly random code. We need to address this, as it includes an encoded string: `cGluZyB3d3cueW91YXJldnVsbmVyYWJsZS50aG0=`.

![Encoded String](https://github.com/user-attachments/assets/d7410c65-2617-49c4-9c2f-338c8c1ebe22)

We use the powerful tool CyberChef to decode this string easily. And there you have it — our answer!

![CyberChef Decoding](https://github.com/user-attachments/assets/c360a247-a68d-45bf-917e-946d7b4b9bb9)

---

## Question 5: What password was set for the new user account?

**A:** `I_AM_M0NIT0R1NG`

To answer this question, search for 'net' in the search bar. Then, look for the answer in the data.win.eventdata.parentCommandLine fields.

![Net User Search](https://github.com/user-attachments/assets/365e32fc-4126-4201-912b-951c0262fa0c)

Finally, we find it among the other documents!

![User Password](https://github.com/user-attachments/assets/c663f2d5-1e1e-4f77-8393-b5a955ec4cb7)

---

## Question 6: What is the name of the .exe that was used to dump credentials?

**A:** `memotech.exe`

To answer this question, search for 'mimikatz' since the question emphasizes dumping credentials.

![Mimikatz Search](https://github.com/user-attachments/assets/a8e77f4e-31bb-4673-8c2a-6784126fca9a)

After that, filter by data.win.eventdata.Image.

![Image Filter](https://github.com/user-attachments/assets/e1c4f846-7442-4c07-bba9-7d835aeacc9e)

And you'll get the answer right away.

![Credential Dumping Tool](https://github.com/user-attachments/assets/1db228ce-9c65-4ee1-9ca7-3783c1e3a23e)

---

## Question 7: Data was exfiltrated from the host. What was the flag that was part of the data?

**A:** `THM{M0N1T0R_1$_1N_3FF3CT}`

This one is straightforward. To find the THM flag, simply search for 'THM' in the search bar to avoid missing it. Additionally, focus on data.win.eventdata.CommandLine to locate the flag.

![THM Flag Search](https://github.com/user-attachments/assets/9fe53d38-417d-408c-8200-4e1f9066fad0)

---

## 🎯 Final Badges
![Forensics](https://img.shields.io/badge/Forensics-Log_Analysis-FF69B4?style=for-the-badge)
![Malware](https://img.shields.io/badge/Malware-Analysis-000080?style=for-the-badge)
![Room](https://img.shields.io/badge/Room-Monday_Monitor-FF4500?style=for-the-badge)
![Detection](https://img.shields.io/badge/Detection-Threat_Hunting-008080?style=for-the-badge)

## Conclusion

That concludes today's write-up. I hope you followed the step-by-step guide and didn't just seek the answer.

By understanding how to use Wazuh, a Security Information and Event Management tool, you can gain valuable knowledge for your career or enhance your understanding of cybersecurity tools. This exercise demonstrates practical incident response skills including log analysis, threat hunting, and understanding attacker techniques like scheduled tasks, credential dumping, and data exfiltration.

---

**Room Link:** [https://tryhackme.com/room/mondaymonitor](https://tryhackme.com/room/mondaymonitor)
