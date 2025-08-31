MITRE [TryHackMe]


This room will discuss the various resources MITRE has made available for the cybersecurity community.

<img width="389" height="254" alt="Screenshot 2025-08-31 at 9 54 34 PM" src="https://github.com/user-attachments/assets/02835a20-6aa0-49c4-947d-67fe5a091c9e" />
Lab link: https://tryhackme.com/room/mitre
Task 1 Introduction to MITRE

#1.1 Read above.

Answer: No answer is needed.

Task 2 Basic Terminology

#2.1 Read above.

Answer: No answer is needed.

Task 3 ATT&CK® Framework

#3.1 Besides blue teamers, who else will use the ATT&CK Matrix?

To respond to this question, we should read this part of the text:
<img width="688" height="88" alt="Screenshot 2025-08-31 at 9 59 42 PM" src="https://github.com/user-attachments/assets/391b4221-20ce-4d91-a8e1-6acf99d81c09" />
Answer: Red Teamers

#3.2 What is the ID for this technique?

To respond to this question, we should go to this website:

https://attack.mitre.org/

Then we should scroll down and search “Initial Access”. In this column, we can find the Phishing technique and we select it. It will pop out a text with the response.
<img width="655" height="296" alt="Screenshot 2025-08-31 at 9 59 51 PM" src="https://github.com/user-attachments/assets/59e699de-024c-4b74-b2ec-5f2d1873938f" />
Answer: T1566

#3.3 Based on this technique, what mitigation covers identifying social engineering techniques?

We should click on “Phishing” technique, and we can see the following page:
<img width="709" height="267" alt="Screenshot 2025-08-31 at 10 00 51 PM" src="https://github.com/user-attachments/assets/cb0e5f85-0d9d-419e-9290-866c6cfeaaaa" />
Then, we scroll down, and we can find the mitigation table. Next, we should read different mitigation tactics and select the right one.
<img width="685" height="305" alt="Screenshot 2025-08-31 at 10 00 58 PM" src="https://github.com/user-attachments/assets/00a37b7b-bf50-4dc0-970b-60c0e4bce61d" />
For this case, we select “User training”.

Answer: User Training

#3.4 What are the data sources for Detection? (Format: source1, source2, source3 with no spaces after commas)

Go back to the MITRE ATT&CK Phishing Technique page. Then, we need to scroll down and find the Detection table.

We should see the next table:
<img width="668" height="374" alt="Screenshot 2025-08-31 at 10 02 04 PM" src="https://github.com/user-attachments/assets/cec7d995-f5f5-488f-a90c-cf63286b34b5" />
We can find our response in the column called “Data Source”. We write our response according to the format mentioned in the question.

Answer: Application Log,File,Nework Traffic

#3.5 What groups have used spear-phishing in their campaigns? (Format: group1, group2)

Go back to the MITRE ATT&CK Phishing Technique page and look at the procedures example table.

We should see the next table:

Press enter or click to view image in full size
<img width="737" height="235" alt="Screenshot 2025-08-31 at 10 02 13 PM" src="https://github.com/user-attachments/assets/6b5d0979-874c-4dd5-8b81-1ecf63e507c5" />
We can find our response in the column called “Name”. We write our response according to the format mentioned in the question.

Answer: Axiom,Gold SOUTHFIELD

#3.6 Based on the information for the first group, what are their associated groups?

Go back to the MITRE ATT&CK Phishing Technique page and look at the procedures example table. Then, click on the first name link in the table, this will take you to the group page:
<img width="684" height="266" alt="Screenshot 2025-08-31 at 10 03 20 PM" src="https://github.com/user-attachments/assets/7a994745-c802-436f-9e16-aa47d7e05abd" />
As we can see in the image, we can find our response in the label “Associated Groups”.

Answer: Group 72

#3.7 What software is associated with this group that lists phishing as a technique?

Returning to the Group page, we are going to use the find feature of the browser. On your keyboard, press ctrl + f, at the top a search bar should pop down. In that search bar, type Phishing
<img width="705" height="455" alt="Screenshot 2025-08-31 at 10 04 14 PM" src="https://github.com/user-attachments/assets/82628be0-cbf4-4a8c-9166-c58a8224fb55" />
Answer: Hikit

#3.8 What is the description for this software?

Going back to where you got the answer to the previous question, you should click on the name of the software. This will take you to the software page:
<img width="609" height="270" alt="Screenshot 2025-08-31 at 10 04 24 PM" src="https://github.com/user-attachments/assets/a4523696-fb79-432b-af63-aa4b13a142ba" />
Then, we should copy the description of the tool.

Answer: Hikit is malware that has been used by Axiom for late-stage persistence and exfiltration after the initial compromise.

#3.9 This group overlaps (slightly) with which other group?

To respond to this question, we should go back to the Axiom group page. Read through the description, the answer can be found at the end of the paragraph.

<img width="732" height="251" alt="Screenshot 2025-08-31 at 10 05 46 PM" src="https://github.com/user-attachments/assets/6ec02303-9097-41db-82d9-c4c134feb310" />
Answer: Winnti Group

#3.10 How many techniques are attributed to this group?

Going back to where you got the answer to the previous question, we should scroll down to the techniques table, and count the number of times, you see Enterprise in the Domain column, this will be your answer.
<img width="694" height="277" alt="Screenshot 2025-08-31 at 10 06 06 PM" src="https://github.com/user-attachments/assets/b65b7630-9c64-4544-9ff1-b15d9f4f51f1" />
Answer: 15

Task 4 CAR Knowledge Base

#4.1 For the above analytic, what is the pseudocode a representation of?

To respond to this question, we should visit the next website: https://car.mitre.org/analytics/CAR-2020-09-001/

Scroll down and you will find the answer:

Press enter or click to view image in full size
<img width="627" height="124" alt="Screenshot 2025-08-31 at 10 06 15 PM" src="https://github.com/user-attachments/assets/7993ae86-d2c3-4be7-a447-d1b8d25560c3" />

Answer: Splunk search

#4.2 What tactic has an ID of TA0003?

To respond to this question, we should enter the ATT&CK Powered Suit.

First, we should download the extension in our browser.

Link: https://chrome.google.com/webstore/detail/attck-powered-suit/gfhomppaadldngjnmbefmmiokgefjddd
<img width="683" height="194" alt="Screenshot 2025-08-31 at 10 08 44 PM" src="https://github.com/user-attachments/assets/91697df7-95ab-420d-bf98-e6ccbd8d596f" />

Second, open the extension.
<img width="657" height="400" alt="Screenshot 2025-08-31 at 10 08 51 PM" src="https://github.com/user-attachments/assets/54b4ffdf-0bbf-42fd-9fe7-0b487f3acf39" />
Finally, write our id “TA0003” and search for it. As we can see in the next image, we can find our response.
<img width="547" height="450" alt="Screenshot 2025-08-31 at 10 09 03 PM" src="https://github.com/user-attachments/assets/c9d39c3f-49e5-45d2-8de2-9247ac161a63" />

Answer: Persistence

#4.3 What is the name of the library that is a collection of Zeek (BRO) scripts?

To respond to this question, we should go to the next website:

https://car.mitre.org/

Next, we scroll down and search the Analytic Source Code Libraries section.

Read the whole paragraph and at the end sentence, we can find our response.

<img width="678" height="90" alt="Screenshot 2025-08-31 at 10 09 16 PM" src="https://github.com/user-attachments/assets/c2d40c72-6e90-400f-b0f9-75600a63b617" />
Answer: BZAR

#4.4 What is the name of the technique for running executables with the same hash and different names?

To respond to this question, we should click the Analytics link at the top of the page.
<img width="693" height="113" alt="Screenshot 2025-08-31 at 10 09 24 PM" src="https://github.com/user-attachments/assets/28bdc2ec-f027-43e6-805a-f11f1c013e11" />

Next, press ctrl + f to open the find feature. Click in the search bar, then paste (ctrl + v) in the latter half of the question. You will only one result:

Press enter or click to view image in full size
<img width="672" height="315" alt="Screenshot 2025-08-31 at 10 09 35 PM" src="https://github.com/user-attachments/assets/3f4c878d-7d16-4e5c-b42a-c5bb00434e1e" />

Answer: Masquerading

#4.5 Examine CAR-2013–05–004, besides Implementations, what additional information is provided to analysts to ensure coverage for this technique?

To respond to this question, we should search our CARD id “CAR-2013–05–004” on the MITRE repository.
<img width="704" height="268" alt="Screenshot 2025-08-31 at 10 09 42 PM" src="https://github.com/user-attachments/assets/47db12e8-8190-4870-bda1-0922825d3e53" />
Then, click on “CAR-2013–05–004” and pop out the new page.

Scroll down and you will find the answer:
<img width="651" height="199" alt="Screenshot 2025-08-31 at 10 13 24 PM" src="https://github.com/user-attachments/assets/3ad22263-3405-4482-ba6c-bbf88fcb199a" />
Task 5 MITRE Engage

#5.1 Under Prepare, what is ID SAC0002?

To respond to this question, we should go to the next website:

https://engage.mitre.org/

When the page loads, go to the link at the top and click on Tools > Matrix.
<img width="403" height="244" alt="Screenshot 2025-08-31 at 10 14 01 PM" src="https://github.com/user-attachments/assets/59bc75c9-e234-4d4e-9d9b-80ee95b7445d" />
The page will load, click on Prepare.
<img width="749" height="590" alt="Screenshot 2025-08-31 at 10 15 18 PM" src="https://github.com/user-attachments/assets/3e7fd73f-4746-45b0-9ae1-e2c5c6230dec" />
Click on different plans until you find the correct one and match with the id “SAC0002.”

In this case, we found that “PERSONA CREATION” has the correct ID.

Press enter or click to view image in full size
<img width="740" height="231" alt="Screenshot 2025-08-31 at 10 15 25 PM" src="https://github.com/user-attachments/assets/362bc040-5177-47cf-a3af-497485c839d4" />
Answer: Persona Creation

#5.2 What is the name of the resource to aid you with the engagement activity from the previous question?

Go back to the ENGAGE MITRE Matrix site. Go back to the top and over to the magnifying glass/search icon and click on it and write persona.

<img width="751" height="137" alt="Screenshot 2025-08-31 at 10 15 31 PM" src="https://github.com/user-attachments/assets/b8dfec6c-8e7c-4f90-a315-6f1286417da8" />
Once the page loads, we can find our response:
Answer: Persona Profile Worksheet
<img width="638" height="105" alt="Screenshot 2025-08-31 at 10 15 36 PM" src="https://github.com/user-attachments/assets/ca422fa1-5f9b-4103-b4d6-739554ee864e" />

#5.3 Which engagement activity baits a specific response from the adversary?
<img width="898" height="337" alt="Screenshot 2025-08-31 at 10 17 59 PM" src="https://github.com/user-attachments/assets/53a33691-ea0d-46f9-a40e-f88b57d491f4" />

Use the Back button to head back to the ENGAGE MITRE Matrix. Once the page loads, you can look through the different activities listed below in the Matrix.
<img width="898" height="337" alt="Screenshot 2025-08-31 at 10 17 59 PM" src="https://github.com/user-attachments/assets/c41e5e97-d6d5-4f2c-b66b-52bc297e5b47" />

We can find our response in the next image:

<img width="538" height="275" alt="Screenshot 2025-08-31 at 10 18 04 PM" src="https://github.com/user-attachments/assets/8b5ca9f8-479f-4443-85a2-3b1d4d7f0db4" />
Answer: Lures

#5.4 What is the definition of Threat Model?

Last time, head back to the ENGAGE MITRE Matrix site, this time click on the PREPARE tab to open it.
<img width="625" height="243" alt="Screenshot 2025-08-31 at 10 18 38 PM" src="https://github.com/user-attachments/assets/81950499-9a16-40b7-970c-20e1a8fba199" />
Then click on Threat Model at the bottom of the list.

The page loads and we will have our response in the description:
<img width="676" height="252" alt="Screenshot 2025-08-31 at 10 18 44 PM" src="https://github.com/user-attachments/assets/fd2e85f7-aac6-49dc-bc54-36fabf7f5e0b" />
Answer: A risk assessment that models organizational strengths and weaknesses

Task 6 MITRE D3FEND

#6.1 What is the first MITRE ATT&CK technique listed in the ATT&CK Lookup dropdown?

To respond to this question, we should go to the next link:

https://d3fend.mitre.org/

Once the page loads, we should click on the next box:

<img width="595" height="252" alt="Screenshot 2025-08-31 at 10 18 50 PM" src="https://github.com/user-attachments/assets/cbc3ccec-3416-4676-a1a3-44e7f10feaa7" />

As we can see in the preview image, we have our response.

Answer: Data Obfuscation

#6.2 In D3FEND Inferred Relationships, what does the ATT&CK technique from the previous question produce?

Going back to the D3FEND site, click on the ATT&CK Lookup again, and this time click on Data Obfuscation.

We will see a pop-up with information:
<img width="490" height="341" alt="Screenshot 2025-08-31 at 10 18 56 PM" src="https://github.com/user-attachments/assets/f9d4d69b-676a-4586-9822-aa26c0e6b2c0" />
Scroll down and you will see a diagram with our response:
<img width="529" height="417" alt="Screenshot 2025-08-31 at 10 19 03 PM" src="https://github.com/user-attachments/assets/e9e22f2b-e3aa-42ae-a21d-be4f97d41540" />

Answer: Outbound Internet Network Traffic

Task 7 ATT&CK® Emulation Plans

#7.1 In Phase 1 for the APT3 Emulation Plan, what is listed first?

To respond to this question, we should go to the next link:

https://attack.mitre.org/resources/adversary-emulation-plans/

When the page loads, you might have to scroll down a bit, but you will see the APT 3 Emulation Plan. Under Phase 1 the first blue box, the answer is inside of this.
<img width="530" height="278" alt="Screenshot 2025-08-31 at 10 19 08 PM" src="https://github.com/user-attachments/assets/30fd8d3b-520e-4305-86e3-a7ef99eba116" />
Answer: C2 Setup

#7.2 Under Persistence, what binary was replaced with cmd.exe?

Head back to the MITRE ATT&CK APT 3 Emulation Plan page, and scroll to the bottom of the page.

Click on the link APT3 Adversary Emulation Plan. This will open a PDF in a new tab.

When the PDF loads, scroll down to the table of content and search Persistence.

Press enter or click to view image in full size
<img width="644" height="178" alt="Screenshot 2025-08-31 at 10 19 17 PM" src="https://github.com/user-attachments/assets/2f685597-e833-497c-8a6a-54112f57d93a" />
The answer can be found in the second paragraph of the Persistence section.
<img width="721" height="359" alt="Screenshot 2025-08-31 at 10 19 26 PM" src="https://github.com/user-attachments/assets/4e58c37d-d914-42f1-9e6b-34149f3bfd6a" />
Answer: sethc.exe

#7.3 Examining APT29, what C2 frameworks are listed in Scenario 1 Infrastructure? (format: tool1,tool2)

To respond to this question, we should go to the next link:

<img width="702" height="188" alt="Screenshot 2025-08-31 at 10 19 33 PM" src="https://github.com/user-attachments/assets/7cb68c96-c50d-465b-a11a-03093ff723f0" />
<img width="779" height="353" alt="Screenshot 2025-08-31 at 10 19 38 PM" src="https://github.com/user-attachments/assets/0d01e872-1c19-4513-8c5e-45c35376683e" />
Then, open the file README.md.

Once the page loads, search the table of contents and click on “Scenario 1 — Infrastructure”.
Once the page loads, we can see our response in the following image:
<img width="536" height="396" alt="Screenshot 2025-08-31 at 10 19 46 PM" src="https://github.com/user-attachments/assets/83832d82-6ea5-47a9-ac24-2bcbc1bad69f" />
Answer: Pupy,Metasploit Framework

#7.4 What C2 framework is listed in Scenario 2 Infrastructure?

Head back to GitHub for APT29 Adversary Emulation and click the back button on your browser. Then, back on the Table of Contents of the README click on Scenario 2 — Infrastructure.

Search the Emulation Team Infrastructure section.

As we can see, we have our response:
<img width="863" height="292" alt="Screenshot 2025-08-31 at 10 19 52 PM" src="https://github.com/user-attachments/assets/f6278f8d-ab83-4146-b146-744b74e1be6d" />
Answer: PoshC2

#7.5 Examine the emulation plan for Sandworm. What webshell is used for Scenario 1? Check MITRE ATT&CK for the Software ID for the webshell. What is the id? (format: webshell,id)

To respond to this question, we should go to the next link:

https://github.com/center-for-threat-informed-defense/adversary_emulation_library

Once the page loads, search for the full emulation plans column and click on “Sandworm”:
<img width="622" height="156" alt="Screenshot 2025-08-31 at 10 19 57 PM" src="https://github.com/user-attachments/assets/13f36c49-f249-4dd7-8ab3-6862a65093e7" />
Click on the Emulation_Plan Folder.

<img width="652" height="150" alt="Screenshot 2025-08-31 at 10 27 04 PM" src="https://github.com/user-attachments/assets/bc68d864-9dc0-40a9-951e-ae69b132056b" />

Click on the Scenario_1 folder.
<img width="666" height="180" alt="Screenshot 2025-08-31 at 10 27 11 PM" src="https://github.com/user-attachments/assets/583bbb3c-bcb1-4a3d-8bc5-b833889c2c37" />
<img width="680" height="176" alt="Screenshot 2025-08-31 at 10 27 16 PM" src="https://github.com/user-attachments/assets/aa3dbe10-dcca-4982-8c6d-dfb9d36091bd" />
So, the first part of the answer can be found under Scenario Overview, after number one.
<img width="681" height="470" alt="Screenshot 2025-08-31 at 10 27 22 PM" src="https://github.com/user-attachments/assets/74f4d8db-0ce2-48b0-a101-d912efaa0d63" />
Answer: P.A.S.,S0598

Task 8 ATT&CK® and Threat Intelligence

#8.1 What is a group that targets your sector who has been in operation since at least 2013?

To respond to this question, we are going to use the following page: https://attack.mitre.org/groups/

Search on the search bar the word “Aviation”.
<img width="827" height="348" alt="Screenshot 2025-08-31 at 10 27 29 PM" src="https://github.com/user-attachments/assets/e37ccc6c-ffc8-457d-a9f6-1018df7404d8" />
<img width="744" height="547" alt="Screenshot 2025-08-31 at 10 27 36 PM" src="https://github.com/user-attachments/assets/cbddde4e-fe60-4799-bf9b-0c20986b27ef" />
Answer: APT33

#8.2 As your organization is migrating to the cloud, is there anything attributed to this APT group that you should focus on? If so, what is it?

Head back to the Groups site and click on the APT group link to be taken to the APT Group page.

Once the page loads use the find feature (ctrl + f).
<img width="772" height="541" alt="Screenshot 2025-08-31 at 10 27 42 PM" src="https://github.com/user-attachments/assets/a3552cb2-eff6-44d8-afe0-70c707a40055" />
Type “Cloud”
<img width="828" height="728" alt="Screenshot 2025-08-31 at 10 30 19 PM" src="https://github.com/user-attachments/assets/a7be2641-2e7b-4ce0-83fa-6c55f780772c" />
Answer: Ruler

#8.4 Referring to the technique from question 2, what mitigation method suggests using SMS messages as an alternative for its implementation?

Head Back to the APT Group page, this time click on the link that was the answer to two questions ago.

Click on “Cloud Accounts”.
<img width="707" height="104" alt="Screenshot 2025-08-31 at 10 30 33 PM" src="https://github.com/user-attachments/assets/380d8ce2-1e76-4925-bd86-d4b151734514" />
Then, search the Mitigation section. According to the question, the method suggests using SMS messages.

Read every description and select the correct one.
<img width="758" height="217" alt="Screenshot 2025-08-31 at 10 30 40 PM" src="https://github.com/user-attachments/assets/f0d9125f-7221-49bb-b612-876d3855fce6" />
Answer: Multi-factor Authentication

#8.5 What platforms does the technique from question #2 affect?

To respond to this question on the same page of Valid Accounts: Cloud Accounts, search the label Platforms.

You can see your response.

Press enter or click to view image in full size

<img width="691" height="369" alt="Screenshot 2025-08-31 at 10 30 46 PM" src="https://github.com/user-attachments/assets/f10e48d9-900f-4019-8629-2c68fef0f7a6" />
Answer: Azure AD, Google Workspace, IaaS, Office 365, SaaS

Task 9 Conclusion














