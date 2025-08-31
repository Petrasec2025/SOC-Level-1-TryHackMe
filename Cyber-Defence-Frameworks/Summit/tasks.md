TryHackMe Room — Summit
This is a subscribers only room on TryHackMe. It was created by TryHackMe. Here it the link to said room, TryHackMe Room — Summit.

Can you chase a simulated adversary up the Pyramid of Pain until they finally back down?

Press enter or click to view image in full size

<img width="293" height="295" alt="Screenshot 2025-08-31 at 10 53 28 PM" src="https://github.com/user-attachments/assets/151c826e-5f50-4572-a571-28bb85e2e31f" />
Task 1 Challenge
Objective
After participating in one too many incident response activities, PicoSecure has decided to conduct a threat simulation and detection engineering engagement to bolster its malware detection capabilities. You have been assigned to work with an external penetration tester in an iterative purple-team scenario. The tester will be attempting to execute malware samples on a simulated internal user workstation. At the same time, you will need to configure PicoSecure’s security tools to detect and prevent the malware from executing.

Following the Pyramid of Pain’s ascending priority of indicators, your objective is to increase the simulated adversaries’ cost of operations and chase them away for good. Each level of the pyramid allows you to detect and prevent various indicators of attack.

Room Prerequisites
Completing the preceding rooms in the Cyber Defence Frameworks module will be beneficial before venturing into this challenge. Specifically, the following:

The Pyramid of Pain
MITRE
Connection Details
Please click Start Machine to deploy the application, and navigate to https://LAB_WEB_URL.p.thmlabs.com once the URL has been populated.

Start by clicking on the green Start Machine box in the top right of the Task 1 section.

<img width="663" height="275" alt="Screenshot 2025-08-31 at 10 56 13 PM" src="https://github.com/user-attachments/assets/aa6393e6-bc77-41c9-9ea6-f87c31a2c43f" />
Once the URL is available, give it a click. You should be greated with the following below

<img width="709" height="339" alt="Screenshot 2025-08-31 at 10 56 20 PM" src="https://github.com/user-attachments/assets/6fec2981-715e-4a26-8883-e7d810fdc921" />
Note: It may take a few minutes to deploy the machine entirely. If you receive a “Bad Gateway” response, wait a few minutes and refresh the page.

Answer the questions below
What is the first flag you receive after successfully detecting sample1.exe?
From the VM URL page, first read through the email from Sphinx. Afterwards we have a sample to check out. Click on the sample1.exe box at the bottom of the email to move over to the Malware Sandbox tool.

Press enter or click to view image in full size


<img width="699" height="283" alt="Screenshot 2025-08-31 at 10 56 35 PM" src="https://github.com/user-attachments/assets/e83c118a-c0a3-4275-bfd7-46bf6aeef382" />
We can analysis the sample by clicking the bluish/gray box labeled Submit for Analysis.

Press enter or click to view image in full size

<img width="687" height="321" alt="Screenshot 2025-08-31 at 10 56 42 PM" src="https://github.com/user-attachments/assets/275633c6-927d-4e49-889d-6e6711a6694b" />
After the analysis has completed, we will have the General Info for sample1.exe. Remebering from the Pyramid of Pain, Hashes are Trival and can easily be change. But we can use them here to detect sample1.exe. So copy the SHA256 hash, then click on the hamburger in the top left of the screen. From the drop-down menu, click on Manage Hashes.


<img width="664" height="608" alt="Screenshot 2025-08-31 at 10 56 52 PM" src="https://github.com/user-attachments/assets/dc3787a3-912b-42e1-8a74-3b9f0465d84a" />
In Manage Hashes, we can add the SHA256 hash that was detected. To do this, click on the circle to the left of SHA256 which will make it blue and have it selected. Then paste the hash value in the box below it. Finally, click the bluish/gray Submit Hash button.

<img width="695" height="274" alt="Screenshot 2025-08-31 at 10 57 00 PM" src="https://github.com/user-attachments/assets/f2aa41b6-27b0-44f4-8a07-609e7a3f5697" />
If done correctly, you will see The hash value was added to the blocklist! After which you will see Nice work! You prevented sample1.exe from executing by detecting its unique hash value. Check your inbox for the next steps. Click on the inbox link from the statement above the Hash Blocklist.

<img width="710" height="284" alt="Screenshot 2025-08-31 at 10 57 09 PM" src="https://github.com/user-attachments/assets/e915763d-f247-4e79-9113-6feb0bd141b0" />

An email update has appeared in the Mail section. Read through it as it gives great information. At the end of the email you will find the flag and the answer to the question. Copy and paste it into the THM answer field, then click Submit.

<img width="746" height="307" alt="Screenshot 2025-08-31 at 11 00 45 PM" src="https://github.com/user-attachments/assets/33668ad6-9b14-47da-8909-364f1afcb9f1" />
ANSWER: THM{f3cbf08151a11a6a331db9c6cf5f4fe4}

What is the second flag you receive after successfully detecting sample2.exe?
Reading through the new email, Sphinx has recompiled the malware and was able to run it again. They gave us the sample to analyze again, so click on the sample at the bottom of the email to hop over to the Malware analysis screen.

<img width="697" height="261" alt="Screenshot 2025-08-31 at 11 00 53 PM" src="https://github.com/user-attachments/assets/575dca97-f71e-4470-81b1-07749fdf38e2" />
We are now at the Malware Sandbox screen. Before we can analyze, we need to change the sample to sample2.exe. This can be done by clicking the down caret on the File: drop-down box. In the drop-down select choose sample2.exe. Finally click the bluish/gray Submit for Analysis but

<img width="635" height="543" alt="Screenshot 2025-08-31 at 11 01 04 PM" src="https://github.com/user-attachments/assets/d73a1013-6617-4f8a-93de-a55d88e26fc1" />

After the analysis of the file has completed, we can review the findings. If you scroll down to the bottom we can see this time we have some new findings in the way of Network Activity. As per the next stage up on the pyramid we want to look at the IP address. As we can see the IP address 154.35.10.113 goes to a very suspicious URL. Highlight and copy the IP address, then we need to head to the firewall to block it.

<img width="666" height="346" alt="Screenshot 2025-08-31 at 11 01 12 PM" src="https://github.com/user-attachments/assets/3a425cf1-953d-48e2-b26a-019adc6d5ab9" />

So get to the Firewall Manager, click on the hamburger in the top left of the window. In the drop-down you will see Firewall Manager, click on it.

<img width="266" height="504" alt="Screenshot 2025-08-31 at 11 01 21 PM" src="https://github.com/user-attachments/assets/2c181ec6-4371-4cb6-bb9a-11707bcb6963" />

Next you will need to click on the Create Firewall Rule button.

<img width="678" height="188" alt="Screenshot 2025-08-31 at 11 01 29 PM" src="https://github.com/user-attachments/assets/23def009-08d7-4df0-9878-816cd72a7a6d" />
New options will propagate indicating to Create Firewall Rule. For the Type we want to choose Egress as that mean leaving (I think of it as E as in Escape). Next up is Source IP, for it to work on all systems of the company, you will want to type Any. What this means is that it will cover any system reaching out to the destination IP. Which brings us to the next section, Destination IP. This is where you will paste the IP address from the Malware Analysis page. Lastly the Action section, you will want to keep it as Deny. This is so that any system reaching out to 154.35.10.113 will be deny and not allow to connect. Now click on the Save Rule button.

<img width="686" height="419" alt="Screenshot 2025-08-31 at 11 01 36 PM" src="https://github.com/user-attachments/assets/466d711d-2256-4fd1-8552-1839de9f8cba" />
After clicking Save Rule, it will be indicated that sample2.exe was blocked. Additionally, it will let us know we have a new email. Click on the inbox link to head over and read it.

<img width="684" height="287" alt="Screenshot 2025-08-31 at 11 01 43 PM" src="https://github.com/user-attachments/assets/05849f8b-c11a-4bc6-af8a-a10dc2b1438b" />
Again, the flag can be found towards the bottom of the email. Copy and paste it into the THM answer field, then click Submit.

<img width="687" height="296" alt="Screenshot 2025-08-31 at 11 01 50 PM" src="https://github.com/user-attachments/assets/67181b23-a98d-4a14-8147-23b7f15eeb13" />
ANSWER: THM{2ff48a3421a938b388418be273f4806d}

What is the third flag you receive after successfully detecting
As before, read through the email as it gives great insight. Once you have finished click on sample3.exe at the bottom to move over to the Malware Sandbox page


<img width="676" height="309" alt="Screenshot 2025-08-31 at 11 02 00 PM" src="https://github.com/user-attachments/assets/5019bd87-2d96-4cae-835e-ca3a6a4073ce" />

On the Malware Sandbox page, click the down caret. This will drop-down all the samples we have access to. Click on sample3.exe, then click on the Submit for Analysis button.


<img width="640" height="340" alt="Screenshot 2025-08-31 at 11 02 05 PM" src="https://github.com/user-attachments/assets/fe9325e4-fa03-4804-aab6-6acabf985d19" />
When the analaysis has completed, we can read the Behaviour Analysis. This section gives you an idea of what the Malware is doing. After you have done this, it’s time to scroll down and look at the artifacts.

<img width="682" height="310" alt="Screenshot 2025-08-31 at 11 10 31 PM" src="https://github.com/user-attachments/assets/c21428e6-ec8a-4530-bd59-61268d9dc075" />
Scrolling down we can see we have some more information this time. As we can see, there is a suspicious looking domain appearing in our results. Highlight the suspicious domain from the Domain section at the bottom. Now lets head over to the DNS Filter page.

<img width="671" height="356" alt="Screenshot 2025-08-31 at 11 10 38 PM" src="https://github.com/user-attachments/assets/b51ac904-2271-4622-920d-e4d9d038583c" />
Click on the hamburger in the top left of the window. In the drop-down you will see DNS Filter, click on it.

<img width="276" height="475" alt="Screenshot 2025-08-31 at 11 10 46 PM" src="https://github.com/user-attachments/assets/ab2f320f-8910-405d-8df6-a5aacb8be3a5" />
Once on the DNS Rule Manager page, click on the Create DNS Rule.

<img width="680" height="331" alt="Screenshot 2025-08-31 at 11 10 53 PM" src="https://github.com/user-attachments/assets/51713460-46e5-4467-9c3d-aaee76f147ba" />
Starting at the top, we need to name the rule. This can be however you want to name it. I chose Stop Malware download, which goes back to what we saw in the Behavior Analysis section. Next up is the Category section, we can leave this as Malware. Following that section is Domain Name, which we can paste in the domain from the analysis page. The last section is Action, which can be left to Deny. Our rule basically means that any traffic going to or coming from emudyn.bresonicz.info will be denied. The last step is to click the Save Rule button.

<img width="684" height="428" alt="Screenshot 2025-08-31 at 11 11 00 PM" src="https://github.com/user-attachments/assets/15c97e8f-8373-491e-9202-61fde2dfb6a9" />
After clicking Save Rule, it will be indicated that sample3.exe was blocked. Additionally, it will let us know we have a new email. Click on the inbox link to head over and read it.

<img width="682" height="276" alt="Screenshot 2025-08-31 at 11 11 09 PM" src="https://github.com/user-attachments/assets/79a4c650-e1c9-445d-b8ee-a110d9b6a525" />
The flag can be found towards the bottom of the email. Copy and paste it into the THM answer field, then click Submit.

Press enter or click to view image in full size

<img width="682" height="321" alt="Screenshot 2025-08-31 at 11 11 15 PM" src="https://github.com/user-attachments/assets/4074e0cb-243b-46ec-9b42-8d5b05e77a43" />
ANSWER: THM{4eca9e2f61a19ecd5df34c788e7dce16}

What is the fourth flag you receive after successfully detecting sample4.exe?
Read through the email again. Once you have finished click on sample4.exe at the bottom to move over to the Malware Sandbox page.

<img width="663" height="305" alt="Screenshot 2025-08-31 at 11 11 27 PM" src="https://github.com/user-attachments/assets/0fd39c6d-39b7-40bd-b5c7-1a410efc068c" />
On the Malware Sandbox page, click the down caret. This will drop-down all the samples we have access to. Click on sample4.exe, then click on the Submit for Analysis button.

<img width="406" height="359" alt="Screenshot 2025-08-31 at 11 11 34 PM" src="https://github.com/user-attachments/assets/5c9ab69d-31f5-4078-a950-94d19fb7e3a0" />
After the analysis has completed, we can take a look at the Behaviour Analysis section. In it we can see the Malwave Disables Windows Defender Real-time monitoring. With this knowledge, let’s scroll down to see how Sphinx accomplished this.

<img width="684" height="476" alt="Screenshot 2025-08-31 at 11 11 41 PM" src="https://github.com/user-attachments/assets/68ff8d01-4575-430f-9d65-117a1719a41c" />
We have a new section called Registry Activity, in this section we can see registry modifications that were made during the malware execution. Since we saw in the Behavior Analysis that Windows Defender was disabled. Its safe to say that out of the three registry events that top one is the one we are looking for. Highlight and copy all the infomation from registry event and paste it notepad for the time being. Now lets head over to Sigma Rule Builder to create a Sigma rule that detects when this registry value has changed to 1.

Press enter or click to view image in full size

<img width="680" height="476" alt="Screenshot 2025-08-31 at 11 11 48 PM" src="https://github.com/user-attachments/assets/2a2cc005-8f85-4341-b1fe-4a80661c44c1" />
Click on the hamburger in the top left of the window. In the drop-down you will see Sigma Rule Builder, click on it.

<img width="265" height="444" alt="Screenshot 2025-08-31 at 11 12 07 PM" src="https://github.com/user-attachments/assets/963a7844-a4d0-4ccc-be19-57b6d839c2b0" />
On the Sigma Rule Builder we need to click on the Create Sigma Rule button to open the options to create the Sigma rule.

<img width="522" height="423" alt="Screenshot 2025-08-31 at 11 12 14 PM" src="https://github.com/user-attachments/assets/0b7f53ff-d020-4f66-a62e-c7cad3f09cca" />
We are given four options to start step 1 of creating our Sigma Rule. Read through the options, a registry change doesn’t apply to Web Server Logs, VPN Logs, or Application Logs. Meaning that Sysmon Event Logs are our best option at this point. Click on Sysmon Event Logs.

<img width="516" height="721" alt="Screenshot 2025-08-31 at 11 12 37 PM" src="https://github.com/user-attachments/assets/42afe250-a4e7-41ed-8eff-3ef564eb4ae2" />
We are given another four choices. Looking them over the obvious choice is Registry Modifications, as we know that the Malware made a registry value change. Click on Registry Modifications.

<img width="491" height="559" alt="Screenshot 2025-08-31 at 11 12 45 PM" src="https://github.com/user-attachments/assets/15ae50bc-a443-4a8c-813e-537dc763f257" />
Using the information we copied and pasted into our notepad, we will use it to fill out the final step of our Sigma Rule Creation. Starting with the Registry Key, paste HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Defender\Real-Time Protection into this input field. Next up is the Resgistry Name, which we will use DisableRealtimeMonitoring. The Value that the registry entry was changed to was 1. Lastly, we need to map it to a MITRE ATT&CK ID. Looking over the list we can see Defense Evasion (TA0005). Since the Malware disables Windows Defender, it’s safe to say it is trying to evade our defenses. Lastly, we need to click on Validate Rule. Which will create the Sigma rule and Validate that it detects the Malware.

Press enter or click to view image in full size

<img width="668" height="323" alt="Screenshot 2025-08-31 at 11 12 54 PM" src="https://github.com/user-attachments/assets/5d489019-2da5-4214-bb03-6c656f1bdd49" />
After clicking Validate Rule, you will see a quick pop up at the top of the window (so fast I didn’t get a chance to screenshot it) indicating that the rule did detect the Malware. Additionally, a sound that you have a new message will play as well. Let’s head to our Mailbox to see what Sphinx has to say. Again, click the hamburger in the top left of the window. Then click on Mail(1).

<img width="268" height="422" alt="Screenshot 2025-08-31 at 11 13 01 PM" src="https://github.com/user-attachments/assets/e4213bbe-da39-4f18-9c9d-1fec8cba2100" />
Once you are back at your Inbox, you will see the new email. The final flag can be found at the bottom of the email. Copy and paste it into the THM answer field, then click Submit.

<img width="685" height="368" alt="Screenshot 2025-08-31 at 11 13 18 PM" src="https://github.com/user-attachments/assets/d35c872e-2940-4755-9003-2c5ab5cf2747" />
