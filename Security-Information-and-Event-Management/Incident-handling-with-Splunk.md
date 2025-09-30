# Incident Handling with Splunk Room Walkthrough

![Room Banner](https://github.com/user-attachments/assets/0a84a1bb-cba4-4c2e-a925-82a31e2d9ad1)

## 🏆 Badges
![SIEM](https://img.shields.io/badge/SIEM-Splunk_Incident_Response-0078D6?style=for-the-badge&logo=splunk&logoColor=white)
![Incident Response](https://img.shields.io/badge/Incident_Response-Kill_Chain_Analysis-00C800?style=for-the-badge&logo=shield&logoColor=white)
![Difficulty](https://img.shields.io/badge/Difficulty-Intermediate-FFA500?style=for-the-badge)
![Platform](https://img.shields.io/badge/Platform-TryHackMe-FF0000?style=for-the-badge&logo=tryhackme&logoColor=white)
![Completion](https://img.shields.io/badge/Completion-100%25-00FF00?style=for-the-badge)
![Forensics](https://img.shields.io/badge/Forensics-Malware_Analysis-800080?style=for-the-badge)

## Overview
I did the introductory Splunk room after a long break. I felt like the introductory room was pretty basic the second time around but it doesn't feel overwhelming as a beginner, so that's also good! Again, I will be doing all the Splunk room in the SOC Level 1 path again for more practice, and to write the corresponding write-up. Let's get started!

---

## Task 4 Reconnaissance Phase

### Question 1: One suricata alert highlighted the CVE value associated with the attack attempt. What is the CVE value?
First, I used my Kali machine to do this lab. To connect to TryHackMe's network, follow this guide I wrote until step 6. Once you are connected, open a browser and connect to the IP that will be unique to you in task 3. It should show "Explore Splunk" in the middle. From there, go to the right and click on "Search & Reporting" so we can start our search queries.

![Splunk Search](https://github.com/user-attachments/assets/c926cf10-f65f-4380-8c60-b332254cf3eb)

I used the following query to find the answer `index=botsv1 imreallynotbatman.com sourcetype=suricata CVE`. index=botsv1 imreallynotbatman.com is given to us from the reading. I used sourcetype=suricata because we are looking for suricata alerts. You can look at the left side and click on suricata or you can type it in. I typed in CVE to narrow search results that mentions "CVE" in the results.

![Suricata Search](https://github.com/user-attachments/assets/62753aa3-ddef-4f31-9ac2-f32db273311b)

![CVE Results](https://github.com/user-attachments/assets/064157b0-18ef-419d-9a94-bfbcfecdb453)

Once the results populate, I clicked on "Show as raw text" to let me see the text. There's a few different results so keep looking through the other results.

![Raw Text View](https://github.com/user-attachments/assets/333385a5-cec5-40e6-bd84-b2ec0eda6e81)

**Answer:** `CVE-2014-6271`

### Question 2: What is the CMS our web server is using?
I searched what CMS meant first since I had no idea. It stands for content management system. Since it helps us build websites, I looked at http.url fields. I clicked on it and saw lots of joomla. I also searched what it was, and it said that it's a CMS. Please note that I did change my search query back to `index=botsv1 imreallynotbatman.com` first. You may need to do that so you can see the http.url field at the left.

![Joomla CMS](https://github.com/user-attachments/assets/d49723a5-0387-46c3-bd16-e5ca4ab33bad)

**Answer:** `joomla`

### Question 3: What is the web scanner, the attacker used to perform the scanning attempts?
I spent about 20 minutes on this, and solved question 4 while doing this. This was my search query `index=botsv1 imreallynotbatman.com sourcetype=suricata eventtype=suricata_eve_ids_attack dest="imreallynotbatman.com" dest_ip="192.168.250.70" status=404`. Some might not be needed. My thought process is that I wanted to limit my search results as much as possible. The eventtype filter is because we are under attack, which the IDS detected. The destination and destination IP is because we are being scanned. The status=404 filter is because if we are getting scanned, it should return some 404 results because web scanners check for subdirectories that may not exist for us.

I was able to find this from my search query. ET SCAN Acenetix seemed interesting, so I checked what what ET SCAN Acenetix was and found out Acenetix is a vulnerability scanner. That's what we needed!

![Acunetix Scanner](https://github.com/user-attachments/assets/132aae2a-cfcb-47e0-924b-805d6fcde3de)

**Answer:** `Acunetix`

---

## Task 5 Exploitation Phase

### Question 1: What was the URI which got multiple brute force attempts?
This can be found in the text.

**Answer:** `/joomla/administrator/index.php`

### Question 2: Against which username was the brute force attempt made?
By following the text and trying the queries given, we will get the answer.

**Answer:** `admin`

### Question 3: What was the correct password for admin access to the content management system running imreallynotbatman.com?
By following the text and trying the queries given, we will get the answer.

**Answer:** `batman`

### Question 4: How many unique passwords were attempted in the brute force attempt?
This can be found in the screenshot in the text.

**Answer:** `412`

### Question 5: What IP address is likely attempting a brute force password attack against imreallynotbatman.com?
This can be found in the screenshot in the text. This is the query I used from the text `index=botsv1 sourcetype=stream:http dest_ip="192.168.250.70" http_method=POST form_data=*username*passwd* | rex field=form_data "passwd=(?<creds>\w+)" | table src_ip creds`. We will know which IP brute forced us since their IP will show up a lot.

**Answer:** `23.22.63.114`

### Question 6: After finding the correct password, which IP did the attacker use to log in to the admin panel?
This can be found in the screenshot in the text. Using the same query, I navigated over to interesting fields and checked src_ip for different IPs. Only one different IP is shown which is probably what they used to log in.

![Admin Login IP](https://github.com/user-attachments/assets/d239cf78-68f0-416c-b54b-ce1f8e1f0866)

**Answer:** `40.80.148.42`

---

## Task 6 Installation Phase

### Question 1: Sysmon also collects the Hash value of the processes being created. What is the MD5 HASH of the program 3791.exe?
I modified the query a bit that was given in the text. `index=botsv1 "3791.exe" sourcetype="XmlWinEventLog" EventCode=1 MD5` I added "MD5" at the end so it will help highlight the text for me, helping me find the hash a lot easier. There were 5 results for me. I tried a few of them before finding out one result showed 3791.exe twice for me. I thought that could be it.

**Answer:** `AAE3F5A29935E6ABCC2C2754D12A9AF0`

### Question 2: Looking at the logs, which user executed the program 3791.exe on the server?
This time, I used the same query, except I replaced "MD5" with "User" to help highlight the name for me.

![User Execution](https://github.com/user-attachments/assets/ab02c095-4099-4bce-98b9-72a7ea1246de)

**Answer:** `NT AUTHORITY\IUSR`

### Question 3: Search hash on the virustotal. What other name is associated with this file 3791.exe?
I pasted the hash onto VirusTotal and went to the details tab. Scroll down a bit and you'll find other names the program uses here.

![VirusTotal Names](https://github.com/user-attachments/assets/9e31ef78-0975-48fc-b97d-0f48d9b1ac5c)

**Answer:** `ab.exe`

---

## Task 7 Action on Objectives

### Question 1: What is the name of the file that defaced the imreallynotbatman.com website?
This can be found in the text and by following the example.

**Answer:** `poisonivy-is-coming-for-you-batman.jpeg`

### Question 2: Fortigate Firewall 'fortigate_utm' detected SQL attempt from the attacker's IP 40.80.148.42. What is the name of the rule that was triggered during the SQL Injection attempt?
This took me a little while. First, I changed the query into `index=botsv1 src=40.80.148.42 sourcetype=fortigate_utm`. We know we want to look at the data coming from fortigate_utm, and we also need to filter to make sure the source is from the attacker's IP. After that, I looked at the attack field on the left and looked at the results. We know it can't be the vulnerability scanner because the attacker has done the reconnaissance phase. SQL injection sounds right because they're attacking us now, besides the obvious that that the question tells us it's an SQL injection too.

![SQL Injection Rule](https://github.com/user-attachments/assets/4976fe2e-1fac-4df8-905b-e0138bb6a637)

**Answer:** `HTTP.URI.SQL.Injection`

---

## Task 8 Command and Control Phase

### Question 1: This attack used dynamic DNS to resolve to the malicious IP. What fully qualified domain name (FQDN) is associated with this attack?
This can be found in the screenshot in the text and by following the example query too.

**Answer:** `prankglassinebracket.jumpingcrab.com`

---

## Task 9 Weaponization Phase

### Question 1: What IP address has P01s0n1vy tied to domains that are pre-staged to attack Wayne Enterprises?
There were a lot of IPs throughout searching on VirusTotal and Robtex that I admittedly just looked at the answer format to see how many numbers were in each octet.

**Answer:** `23.22.63.114`

### Question 2: Based on the data gathered from this attack and common open-source intelligence sources for domain names, what is the email address that is most likely associated with the P01s0n1vy APT group?
I had to use the hint for this. I searched for about 5-10 minutes each on VirusTotal and Robtex and couldn't find anything. I used the site the hint gave and looked through the results.

**Answer:** `lillian.rose@po1s0n1vy.com`

---

## Task 10 Delivery Phase

### Question 1: What is the HASH of the Malware associated with the APT group?
This can be found in the screenshot in the text.

**Answer:** `c99131e0169171935c5ac32615ed6261`

### Question 2: What is the name of the Malware associated with the Poison Ivy Infrastructure?
I simply just copied the hash and put it onto VirusTotal. I went to details tab and looked at the names at the bottom.

![Malware Name](https://github.com/user-attachments/assets/16b8e0fe-c66a-4789-91af-c4d4327b1d0b)

**Answer:** `MirandaTateScreensaver.scr.exe`

---

## 🎯 Final Badges
![APT](https://img.shields.io/badge/APT-Poison_Ivy-FF69B4?style=for-the-badge)
![Kill Chain](https://img.shields.io/badge/Kill_Chain-Analysis-000080?style=for-the-badge)
![Room](https://img.shields.io/badge/Room-Incident_Handling-FF4500?style=for-the-badge)
![Malware](https://img.shields.io/badge/Malware-Hash_Analysis-008080?style=for-the-badge)

## Thoughts & Conclusion

Ah this was a good refresher! It walked you through a lot of stuff but also gave you a few questions where you had to figure out some queries yourself. I think I prefer this sort of training rather than those that doesn't give you anything. I usually struggle the most with where to start. Once I know how to start, I can start working my way to solving problems. That being said, I know in real-life scenarios, it will be different. That is one thing I want to improve on, knowing how to start. I know other training programs have Boss of the SOC that does minimal handholding. I hope to get better with Splunk before attempting those sorts of labs!

The room provided excellent practical experience with Splunk incident response, teaching valuable skills in kill chain analysis, malware investigation, and advanced search query creation. The hands-on exercises helped reinforce how to investigate sophisticated attacks from reconnaissance through command and control phases using real-world techniques.

---

**Room Link:** [https://tryhackme.com/room/investigatingwithsplunk](https://tryhackme.com/room/investigatingwithsplunk)
