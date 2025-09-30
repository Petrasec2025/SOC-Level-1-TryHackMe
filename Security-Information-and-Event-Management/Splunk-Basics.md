# Splunk Basics Room Walkthrough

![Room Banner](https://github.com/user-attachments/assets/c27fc3ce-b4e3-45c1-8475-bfb5a43a533c)

## 🏆 Badges
![SIEM](https://img.shields.io/badge/SIEM-Splunk-0078D6?style=for-the-badge&logo=splunk&logoColor=white)
![Data Analysis](https://img.shields.io/badge/Data_Analysis-Log_Ingestion-00C800?style=for-the-badge&logo=search&logoColor=white)
![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-FFFF00?style=for-the-badge)
![Platform](https://img.shields.io/badge/Platform-TryHackMe-FF0000?style=for-the-badge&logo=tryhackme&logoColor=white)
![Completion](https://img.shields.io/badge/Completion-100%25-00FF00?style=for-the-badge)
![Log Management](https://img.shields.io/badge/Log_Management-Forwarders-800080?style=for-the-badge)

## Overview
I recently came back from my break and, as promised, will be redoing Splunk rooms to create a write-up. This also doubles as a review for me as I did this early on in the SOC Level 1 learning path, so this will help me reinforce what I learned before. Just like before, I will document my thinking and even include my wrong answer attempts to show that we are all learning. I will also be documenting if I used external help.

---

## Task 3 Splunk Components

### Question 1: Which component is used to collect and send data over the Splunk instance?
This can be found in the reading.

**Answer:** `Forwarder`

---

## Task 4 Navigating Splunk

### Question 1: In the Add Data tab, which option is used to collect data from files and ports?
I used my own virtual machine instead of TryHackMe's Attack Box. To connect your own VM to TryHackMe's network, follow my article on RDP until you connect to the network.

Once I connected, I opened Firefox and typed in the IP address that should display from Task 2. If the IP Address doesn't work, try typing in http:// too. Once your Splunk loads, click on Add Data. Then scroll to the bottom and you'll find the answer.

![Add Data Options](https://github.com/user-attachments/assets/0b57af24-9004-4598-aedd-6a37e4fded07)

**Answer:** `Monitor`

---

## Task 5 Adding Data

I downloaded the files from my host machine and then uploaded it to file.io and then downloaded it to my VM. There's probably more effective ways to do it but that's just how I did it. Once the file is in file.io, I used the command `wget -O VPNLogs.json (link)` in the terminal. Remember where your current directory is as it will save it to that directory. The -O option allows us to rename the file. In this case, it will be renamed to VPNLogs.json.

Follow the instructions and gif in the reading to upload data. I took a couple of pics to show what was inputted since the gif is pretty long.

![Upload Data Settings](https://github.com/user-attachments/assets/557a4162-3e7a-4eed-90e8-dc906ce27156)

![Source Type Selection](https://github.com/user-attachments/assets/ffc91b9b-67de-4b0c-aaaf-83e2227d218e)

Here's how it should like when you review it.

![Review Settings](https://github.com/user-attachments/assets/67bd59ab-6f13-4f01-9fcd-0de2bd6e43b6)

### Question 1: Upload the data attached to this task and create an index "VPN_Logs". How many events are present in the log file?
When you finish uploading and start searching, it should already display the results. If it doesn't, type `index=vpn_logs` in the search bar and change the present to "All time."

![Search Results](https://github.com/user-attachments/assets/b007f05b-6431-4234-869f-126fce831a4b)

![Event Count](https://github.com/user-attachments/assets/a99c305b-daa8-410b-934a-b3fdd9613de2)

Alternatively, you can just click on UserName and look at the count.

![UserName Count](https://github.com/user-attachments/assets/f345fca8-0d7f-4f68-a338-7fcf83cfcdad)

**Answer:** `2862`

### Question 2: What is the name associated with IP 107.14.182.38?
Similar to above, I looked at the interesting fields. Source_ip is something we might need. I adjusted the filter to what I need and looked at the results and the accompanying user.

![IP User Association](https://github.com/user-attachments/assets/c099b99e-9ca9-493a-8a44-498793abd1ab)

**Answer:** `Smith`

### Question 3: What is the number of events that originated from all countries except France?
Look at the interesting fields again. This time, it looks like Source_Country is what we need. I clicked on France so it will create the search query for me. Then I added "NOT" in front of Source_Country. How did I know to use "NOT"? I vaguely remember Splunk accepts boolean expressions.

![Exclude France Query](https://github.com/user-attachments/assets/9abb3f03-ed2f-441d-8587-1c8279240225)

Alternatively, you can do some math. Since we know there is a total of 2862 events from question 1, we can click on Source_Country to see how many events have France as a source country. Then we subtract 48 to get 2814.

![France Count](https://github.com/user-attachments/assets/8c15fcab-c30c-4a5e-a4dc-8c5897d5bef8)

**Answer:** `2814`

### Question 4: How many VPN Events were observed by the IP 107.3.206.58?
Similar to question 3, I will be using Source_ip field as we are looking for a specific IP. I adjusted my search query to the one below and hit enter.

![Specific IP Query](https://github.com/user-attachments/assets/48ff710d-6449-4cc8-93c9-a121807cebb4)

**Answer:** `14`

---

## 🎯 Final Badges
![Indexing](https://img.shields.io/badge/Indexing-Data_Management-FF69B4?style=for-the-badge)
![Search](https://img.shields.io/badge/Search-Queries-000080?style=for-the-badge)
![Room](https://img.shields.io/badge/Room-Splunk_Basics-FF4500?style=for-the-badge)
![VPN](https://img.shields.io/badge/VPN-Log_Analysis-008080?style=for-the-badge)

## Thoughts & Conclusion

While it is a review, I think this was a bit too basic for me. It is a introductory room, so it is absolutely understandable. I'm looking forward to the rest of the Splunk rooms to work on my querying skills. Thank you for being patient while I was gone. I'll be redoing the Splunk rooms, phishing rooms, and I believe the first two Wireshark rooms so I can complete the SOC Level 1 path write-ups.

The room provided excellent foundational experience with Splunk, teaching valuable skills in data ingestion, index creation, basic search queries, and field analysis. The practical exercises helped reinforce how to navigate the Splunk interface and perform basic log analysis tasks.

---

**Room Link:** [https://tryhackme.com/room/splunk101](https://tryhackme.com/room/splunk101)
