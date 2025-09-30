<img width="1241" height="229" alt="Screenshot 2025-09-30 at 1 57 13 PM" src="https://github.com/user-attachments/assets/20bad875-6ea0-4245-b75a-87749eff9187" />

Scenario
Swiftspend Finance, the coolest fintech company in town, is on a mission to level up its cyber security game to keep those digital adversaries at bay and ensure their customers stay safe and sound.

Led by the tech-savvy Senior Security Engineer John Sterling, Swiftspend’s latest project is about beefing up their endpoint monitoring using Wazuh and Sysmon. They’ve been running some tests to see how well their cyber guardians can sniff out trouble. And guess what? You’re the cyber sleuth they’ve called in to crack the code!

The tests were run on Apr 29, 2024, between 12:00:00 and 20:00:00.

As you dive into the logs, you’ll look for any suspicious process shenanigans or weird network connections, you name it! Your mission? Unravel the mysteries within the logs and dish out some epic insights to fine-tune Swiftspend’s defences.

Machine Access
Click the Start Machine button attached to this task to start the VM. Give the machine about 5 minutes to fully set up the environment. Access the Wazuh Dashboard using your browser at https://10-10-166-179.p.thmlabs.com and use the credentials listed below:
<img width="679" height="184" alt="Screenshot 2025-09-30 at 1 58 12 PM" src="https://github.com/user-attachments/assets/d8e87f06-f429-45de-bb00-c7e8e6c8be5b" />
Once logged in, navigate to the Security events module and use the saved query Monday_Monitor to access the logs.
Okay, so we understand that we need to use the Wazuh software to complete this task. First, as stated in the scenario, we need to monitor events between 12:00 and 20:00 on April 29, 2024. Therefore, we must configure the settings to reflect this specific date and time
<img width="665" height="481" alt="Screenshot 2025-09-30 at 1 58 29 PM" src="https://github.com/user-attachments/assets/0646f1e8-7cb0-42e2-8415-575191cca932" />
<img width="657" height="569" alt="Screenshot 2025-09-30 at 1 58 37 PM" src="https://github.com/user-attachments/assets/ee9e4284-f902-45a2-bdb6-36517377efb2" />
Lastly, please don’t forget to access the Monday_monitor queries that have been saved by the system.
<img width="561" height="393" alt="Screenshot 2025-09-30 at 1 58 44 PM" src="https://github.com/user-attachments/assets/5857135b-a677-4f86-bfc3-52beff9a7d3a" />
Let’s dive into the question, shall we?

Question 1
Initial access was established using a downloaded file. What is the file name saved on the host?

A: SwiftSpend_Financial_Expenses.xlsm

I understand that the first question might be a bit confusing at first glance. But don’t worry, we’ll figure it out together.

Firstly, the question asks for the file name saved on the host. To find this, you should navigate to: Events → search bar (localhost).
<img width="692" height="96" alt="Screenshot 2025-09-30 at 1 58 56 PM" src="https://github.com/user-attachments/assets/e4a05bc4-4c98-44e5-abc1-1fbad59bd025" />
You will see three hits displayed above the table. Please direct your attention to the top document
<img width="684" height="256" alt="Screenshot 2025-09-30 at 1 59 02 PM" src="https://github.com/user-attachments/assets/0e86bdb3-0b41-4c4e-8b6f-c02cacd27892" />
Then, you will find the answer in the data.win.event.data.commandLine section
<img width="710" height="230" alt="Screenshot 2025-09-30 at 1 59 08 PM" src="https://github.com/user-attachments/assets/3fbdcbc4-9695-445a-9c9a-05e99d26545c" />
Question 2
What is the full command run to create a scheduled task?

A: \”cmd.exe\” /c \”reg add HKCU\\SOFTWARE\\ATOMIC-T1053.005 /v test /t REG_SZ /d cGluZyB3d3cueW91YXJldnVsbmVyYWJsZS50aG0= /f &amp; schtasks.exe /Create /F /TN \”ATOMIC-T1053.005\” /TR \”cmd /c start /min \\\”\\\” powershell.exe -Command IEX([System.Text.Encoding]::ASCII.GetString([System.Convert]::FromBase64String((Get-ItemProperty -Path HKCU:\\\\SOFTWARE\\\\ATOMIC-T1053.005).test)))\” /sc daily /st 12:34\”

As we learned in the Wazuh module, you can search for ‘scheduler’ in the search bar. To find the full command used to create the scheduled task, add the filter data.win.eventdata.parentCommandLine, which will display the complete command
<img width="493" height="656" alt="Screenshot 2025-09-30 at 1 59 29 PM" src="https://github.com/user-attachments/assets/4b04ca11-a41e-48f2-8a36-560955d048ef" />
Then, you’ll find that one of the documents contains a lengthy command
<img width="678" height="112" alt="Screenshot 2025-09-30 at 1 59 38 PM" src="https://github.com/user-attachments/assets/d4edb771-beb6-4856-b70e-5e0110af9cd3" />
So, there they are!
<img width="677" height="116" alt="Screenshot 2025-09-30 at 1 59 47 PM" src="https://github.com/user-attachments/assets/3502e21e-8697-458a-82c8-d8844cfb821f" />

Question 3
What time is the scheduled task meant to run?

A: 12:34

This one is quite simple. Scroll up a bit, and you’ll find the answer in the original data.win.eventdata.CommandLine fields
<img width="683" height="92" alt="Screenshot 2025-09-30 at 1 59 53 PM" src="https://github.com/user-attachments/assets/92e42e5e-1da0-4d7e-88f5-75b85f1c1065" />

Question 4
What was encoded?

A: ping www.youarevulnerable.thm

This one might seem a bit confusing, but it’s actually quite straightforward. Notice that the data.win.eventdata.parentCommandLine field contains a long string with seemingly random code. We need to address this, as it includes an encoded string: cGluZyB3d3cueW91YXJldnVsbmVyYWJsZS50aG0=.
<img width="723" height="120" alt="Screenshot 2025-09-30 at 1 59 59 PM" src="https://github.com/user-attachments/assets/d7410c65-2617-49c4-9c2f-338c8c1ebe22" />
We use the powerful tool CyberChef to decode this string easily. And there you have it — our answer!
<img width="682" height="307" alt="Screenshot 2025-09-30 at 2 00 07 PM" src="https://github.com/user-attachments/assets/c360a247-a68d-45bf-917e-946d7b4b9bb9" />
Question 5
What password was set for the new user account?

A: I_AM_M0NIT0R1NG

To answer this question, search for ‘net’ in the search bar. Then, look for the answer in the data.win.eventdata.parentCommandLine fields.
<img width="461" height="615" alt="Screenshot 2025-09-30 at 2 00 14 PM" src="https://github.com/user-attachments/assets/365e32fc-4126-4201-912b-951c0262fa0c" />
Finally, we find it among the other documents!
<img width="707" height="86" alt="Screenshot 2025-09-30 at 2 00 20 PM" src="https://github.com/user-attachments/assets/c663f2d5-1e1e-4f77-8393-b5a955ec4cb7" />

Question 6
What is the name of the .exe that was used to dump credentials?

A: memotech.exe

To answer this question, search for ‘mimikatz’ since the question emphasizes dumping credentials.

Press enter or click to view image in full size
<img width="661" height="120" alt="Screenshot 2025-09-30 at 2 00 27 PM" src="https://github.com/user-attachments/assets/a8e77f4e-31bb-4673-8c2a-6784126fca9a" />
After that, filter by data.win.eventdata.Image.
<img width="469" height="492" alt="Screenshot 2025-09-30 at 2 00 36 PM" src="https://github.com/user-attachments/assets/e1c4f846-7442-4c07-bba9-7d835aeacc9e" />
And you’ll get the answer right away.
<img width="699" height="114" alt="Screenshot 2025-09-30 at 2 00 43 PM" src="https://github.com/user-attachments/assets/1db228ce-9c65-4ee1-9ca7-3783c1e3a23e" />
Question 7
Data was exfiltrated from the host. What was the flag that was part of the data?

A: THM{M0N1T0R_1$_1N_3FF3CT}

This one is straightforward. To find the THM flag, simply search for ‘THM’ in the search bar to avoid missing it. Additionally, focus on data.win.eventdata.CommandLine to locate the flag.
<img width="705" height="111" alt="Screenshot 2025-09-30 at 2 01 00 PM" src="https://github.com/user-attachments/assets/9fe53d38-417d-408c-8200-4e1f9066fad0" />

That concludes today’s write-up. I hope you followed the step-by-step guide and didn’t just seek the answer.

By understanding how to use Wazuh, a Security Information and Event Management tool, you can gain valuable knowledge for your career or enhance your understanding of cybersecurity tools. :)
