<img width="1439" height="316" alt="Screenshot 2025-10-01 at 10 35 33 AM" src="https://github.com/user-attachments/assets/bf2f21b1-43f3-4d24-9a7a-70701a66483f" />
Phishing Analysis Tools
Learn the tools used to aid an analyst to investigate suspicious emails.

link : https://tryhackme.com/room/phishingemails3tryoe
Task 1: Introduction
No answer needed
<img width="1297" height="548" alt="Screenshot 2025-10-01 at 10 37 10 AM" src="https://github.com/user-attachments/assets/25745ada-1690-46c0-af87-aa150a468667" />
Task 2: What information should we collect?
No answer needed
<img width="1278" height="743" alt="Screenshot 2025-10-01 at 10 37 24 AM" src="https://github.com/user-attachments/assets/9f5a3460-9420-4221-a283-64dfb03dccc1" />
Task 3 Email header analysis
What is the official site name of the bank that capitai-one.com tried to resemble?

Google the website capitai-one.com
<img width="452" height="382" alt="Screenshot 2025-10-01 at 10 39 30 AM" src="https://github.com/user-attachments/assets/18d08306-5cc6-4f44-afae-e859146893b5" />
capitalone.com

Task 4: Email body analysis
How can you manually get the location of a hyperlink?

<img width="1391" height="266" alt="Screenshot 2025-10-01 at 10 40 43 AM" src="https://github.com/user-attachments/assets/0fb1c8ee-12e4-4811-b857-7a27fdc8f270" />
Copy Link Location

Task 5: Malware Sandbox
No answer needed
<img width="1338" height="205" alt="Screenshot 2025-10-01 at 10 41 18 AM" src="https://github.com/user-attachments/assets/c5efa7b3-b2f9-47f9-9301-e8ba4bb2d99b" />
Task 6 PhishTool
Look at the Strings output. What is the name of the EXE file?

You can find the answer in the strings section :
<img width="610" height="440" alt="Screenshot 2025-10-01 at 10 41 59 AM" src="https://github.com/user-attachments/assets/c898576e-1a9f-4522-ac39-2d945ef353af" />
#454326_PDF.exe

Task 7: Phishing Case 1
What brand was this email tailored to impersonate?

I used phishtool to get informations
<img width="689" height="261" alt="Screenshot 2025-10-01 at 10 43 06 AM" src="https://github.com/user-attachments/assets/c8fa95f0-7876-4d14-9052-14ae5b9d1f77" />
Netflix

What is the From email address?
<img width="675" height="472" alt="Screenshot 2025-10-01 at 10 43 15 AM" src="https://github.com/user-attachments/assets/02523cb0-8b11-4fca-b8ec-c14736fbfc72" />
JGQ47wazXe1xYVBrkeDg-JOg7ODDQwWdR@JOg7ODDQwWdR-yVkCaBkTNp.gogolecloud.com

What is the originating IP? Defang the IP address.
<img width="683" height="291" alt="Screenshot 2025-10-01 at 10 43 25 AM" src="https://github.com/user-attachments/assets/1cdecee8-285b-4629-be53-983e4f8d3c68" />
I used cyberchef to defang the IP adress
<img width="687" height="459" alt="Screenshot 2025-10-01 at 10 43 33 AM" src="https://github.com/user-attachments/assets/da822ab1-5c88-442d-90fc-ba892db3f7ac" />
209[.]85[.]167[.]226

From what you can gather, what do you think will be a domain of interest? Defang the domain.

You can find this information in the Return-path of the mail :
<img width="683" height="270" alt="Screenshot 2025-10-01 at 10 43 42 AM" src="https://github.com/user-attachments/assets/63d9649b-bf77-453e-9d04-efaca3cfa95e" />
Defang it with cyberchef

etekno[.]xyz

What is the shortened URL? Defang the URL.

In the message URLs you have the link
<img width="639" height="266" alt="Screenshot 2025-10-01 at 10 43 50 AM" src="https://github.com/user-attachments/assets/79409c7a-6f3c-4fa2-9f8e-eb2266c7435a" />

Just defang it with cyberchef

hxxps[://]t[.]co/yuxfzm8kpg?amp=1

Task 8: Phishing Case 2
What does AnyRun classify this email as?

You have the banner on the right of anyrun
<img width="677" height="260" alt="Screenshot 2025-10-01 at 10 46 27 AM" src="https://github.com/user-attachments/assets/21f7e737-aa09-4ee5-bf1c-d79a5abc4f7b" />
Suspicious activity

What is the name of the PDF file?
<img width="679" height="93" alt="Screenshot 2025-10-01 at 10 46 36 AM" src="https://github.com/user-attachments/assets/0d93a841-47df-49ba-8bd5-e7f0a4bbded0" />
Open the text report
<img width="685" height="173" alt="Screenshot 2025-10-01 at 10 46 42 AM" src="https://github.com/user-attachments/assets/d8c952f5-39ed-463f-a862-db6933a4a7fb" />
<img width="697" height="271" alt="Screenshot 2025-10-01 at 10 46 49 AM" src="https://github.com/user-attachments/assets/af999667-bd5c-44d3-bf71-a70caa0beca3" />
CC6F1A04B10BCB168AEEC8D870B97BD7C20FC161E8310B5BCE1AF8ED420E2C24

What two IP addresses are classified as malicious? Defang the IP addresses. (answer: IP_ADDR,IP_ADDR)

On the text report document, find the connections section, get malicious reputation IP
<img width="683" height="366" alt="Screenshot 2025-10-01 at 10 46 58 AM" src="https://github.com/user-attachments/assets/30a730ee-f939-4268-8fd7-1123af7ad871" />
<img width="678" height="325" alt="Screenshot 2025-10-01 at 10 47 04 AM" src="https://github.com/user-attachments/assets/2d728772-61f3-44c4-9d6c-20ec3502f75b" />
Defang with cyberchief

2[.]16[.]107[.]24,2[.]16[.]107[.]83

What Windows process was flagged as Potentially Bad Traffic?
<img width="675" height="97" alt="Screenshot 2025-10-01 at 10 47 12 AM" src="https://github.com/user-attachments/assets/3adb9f8a-f1d8-4ecd-a2e1-be9ca4475620" />
svchost.exe

Task 9: Phishing Case 3
What is this analysis classified as?
<img width="678" height="645" alt="Screenshot 2025-10-01 at 10 49 39 AM" src="https://github.com/user-attachments/assets/88daa4af-a29b-40b5-b59a-5829c786f587" />

Malicious activity

What is the name of the Excel file?

<img width="680" height="504" alt="Screenshot 2025-10-01 at 10 49 49 AM" src="https://github.com/user-attachments/assets/f5a346e2-e600-44b6-ae06-ee06bff7c049" />

CBJ200620039539.xlsx

What is the SHA 256 hash for the file?

Open details
<img width="678" height="432" alt="Screenshot 2025-10-01 at 10 49 58 AM" src="https://github.com/user-attachments/assets/3506d172-9eb5-41c2-b056-3298bf73aba5" />
5F94A66E0CE78D17AFC2DD27FC17B44B3FFC13AC5F42D3AD6A5DCFB36715F3EB

What domains are listed as malicious? Defang the URLs & submit answers in alphabetical order. (answer: URL1,URL2,URL3)
<img width="678" height="364" alt="Screenshot 2025-10-01 at 10 50 06 AM" src="https://github.com/user-attachments/assets/a920e8cb-8245-463f-8db3-c2eacf12b3ca" />

biz9holdings[.]com,findresults[.]site, ww38[.]findresults[.]site

What IP addresses are listed as malicious? Defang the IP addresses & submit answers from lowest to highest. (answer: IP1,IP2,IP3)
<img width="667" height="352" alt="Screenshot 2025-10-01 at 10 50 15 AM" src="https://github.com/user-attachments/assets/4ab03571-cc71-4f1d-812c-85142b64e652" />
204[.]11[.]56[.]48,103[.]224[.]182[.]251,75[.]2[.]11[.]242

What vulnerability does this malicious attachment attempt to exploit?
<img width="689" height="285" alt="Screenshot 2025-10-01 at 10 50 21 AM" src="https://github.com/user-attachments/assets/b7e7fcc9-12a2-414a-9d92-70ad9be8ae09" />

CVE-2017–11882

Task 10: Conclusion
No Answer Needed
<img width="1314" height="517" alt="Screenshot 2025-10-01 at 10 54 34 AM" src="https://github.com/user-attachments/assets/4ac7a1a5-04c4-48f5-a48f-060b87803447" />
