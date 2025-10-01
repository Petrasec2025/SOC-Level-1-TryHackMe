<img width="1424" height="324" alt="Screenshot 2025-10-01 at 6 35 16 PM" src="https://github.com/user-attachments/assets/2abe1bc3-9f4d-47a6-afcc-65a6ecc4db50" />
We just finished Linux Forensics, utilizing the terminal to view artifacts. We’re going to be using an application called Autopsy to continue our Digital Forensics training. I wanted to utilize it more during Windows Forensics room but looks like we will have a chance now since it’s all about Autopsy!

Task 2 Workflow Overview and Case Analysis

I will be RDPing into THM’s machine. Directions can be found here.

1: What is the file extension of the Autopsy files?

I followed the instructions and imported Sample Case.aut. The reading also states what file extension Autopsy has.

Answer: .aut

Task 3 Data Sources

1: What is the disk image name of the “e01” format?

I used EnCase in school so I remember this. The reading does specify which application uses .e01 format though!

Answer: EnCase

Task 5 The User Interface I

1: Expand the “Data Sources” option; what is the number of available sources?

On the left side, click on “Data Sources” to expand the menu, then expand the “sample-case.dd” too and count the number of volumes.
<img width="384" height="202" alt="Screenshot 2025-10-01 at 6 37 08 PM" src="https://github.com/user-attachments/assets/277f4956-092e-48d6-b25c-33097104fc56" />
Answer: 4

2: What is the number of the detected “Removed” files?
<img width="314" height="541" alt="Screenshot 2025-10-01 at 6 37 14 PM" src="https://github.com/user-attachments/assets/e3ff5add-14d6-436b-bb02-9aacacd75607" />
Answer: 10

3: What is the filename found under the “Interesting Files” section?

On the left hand side, expand “Interesting Items” until you can get to the files. Click on the files and on the right side, you can see two .exe files. That is the answer.
<img width="1205" height="391" alt="Screenshot 2025-10-01 at 6 37 20 PM" src="https://github.com/user-attachments/assets/e389cfbe-b148-4c4f-b886-66094c54f79c" />
Answer: googledrivesync.exe

Task 6 The User Interface II

1: What is the full name of the operating system version?

Using what I just read, I right clicked “sample-case.dd” and then selected “View Summary Information” to get an overview of what I’m working with. We can see the OS in this screen.
<img width="406" height="355" alt="Screenshot 2025-10-01 at 6 37 27 PM" src="https://github.com/user-attachments/assets/ce4a8d4d-827d-47b1-b914-cfb8d7a40f51" />

Answer: Windows 7 Ultimate Service Pack 1

2: What percentage of the drive are documents? Include the % in your answer.

The answer can be found in the same screen as the OS version.

Answer: 40.8%

3: Generate an HTML report as shown in the task and view the “Case Summary” section.
What is the job number of the “Interesting Files Identifier” module?

At the top, click on “Generate Report”, and select “HTLM” option. Then select “Next” twice and then click on “Finish.”
<img width="683" height="40" alt="Screenshot 2025-10-01 at 6 37 32 PM" src="https://github.com/user-attachments/assets/93d46cd3-f3dc-4b34-82c5-e4346d1e485a" />
To open the report we generated, head back over to Sample Case -> Reports ->Sample Case HTML Report -> report. That should be the default location it exports to.
<img width="676" height="305" alt="Screenshot 2025-10-01 at 6 37 37 PM" src="https://github.com/user-attachments/assets/049c052a-46fc-4e1a-a31a-d7a2471b2abf" />
Once you open it, the report should look like this. Scroll down to get the job number related to Interesting Files. If your screen doesn’t look like mine, just click on Case Summary at the top left and then scroll down.
<img width="705" height="447" alt="Screenshot 2025-10-01 at 6 37 45 PM" src="https://github.com/user-attachments/assets/e35cf927-10f4-4070-b458-6c08fe561b97" />

Answer: 10

Task 7 Data Analysis

1: What is the name of an Installed Program with the version number of 6.2.0.2962?

The first thing I did was searching for the version number by utilizing the “Keyword Search” on the top right.
<img width="361" height="265" alt="Screenshot 2025-10-01 at 6 37 52 PM" src="https://github.com/user-attachments/assets/c86d054c-474b-4726-997f-a56fb4e91563" />
Out of all the results, I saw what I felt like was the answer. The keywords said ProductVersion.
<img width="1211" height="550" alt="Screenshot 2025-10-01 at 6 38 09 PM" src="https://github.com/user-attachments/assets/ebe7e30a-7509-46af-8d1d-8a0f6d529767" />
Answer: IAMAN

3: Numerous SECRET files were accessed from a network drive. What was the IP address?

I decided to search for “SECRET” first since it seems weird how it was capitalized. I ended up with some results with “Secured Network Drive” in their keyword.
<img width="1197" height="217" alt="Screenshot 2025-10-01 at 6 38 16 PM" src="https://github.com/user-attachments/assets/1991de1b-e86a-4560-92df-6f447d584a07" />
I then clicked on the result and then looked at the bottom to see if there was anything I can get from that. It turns out there is an IP Address. I believe it was on our network because of “\\10.11.11.128\Secured_DRIVESecret…..” which made me think it was mapped to the network.
<img width="574" height="228" alt="Screenshot 2025-10-01 at 6 38 22 PM" src="https://github.com/user-attachments/assets/5e56bfd0-6bbd-42f3-8a62-4a0aa647f1f3" />
Answer: 10.11.11.128

4: What web search term has the most entries?

I looked around and saw “Web Search” which may be something we need.
<img width="565" height="705" alt="Screenshot 2025-10-01 at 6 38 30 PM" src="https://github.com/user-attachments/assets/a4bfa1b3-936b-479f-a900-83fb9f1a268c" />
Once you click on Web Search, the right-hand side should show you what text was entered in a search engine. Look for one that shows up the most.
<img width="1189" height="459" alt="Screenshot 2025-10-01 at 6 38 37 PM" src="https://github.com/user-attachments/assets/438b3154-6b65-4e77-8573-5aaa5dcfb5d9" />
Answer: information leakage cases.

5: What was the web search conducted on 3/25/2015 21:46:44?

This time, we need to look at the “Date Accessed” column to help get our answer.
<img width="1198" height="463" alt="Screenshot 2025-10-01 at 6 38 44 PM" src="https://github.com/user-attachments/assets/f69ef5d6-be74-4b52-8907-0bac9ce68c2b" />
Answer: anti-forensic tools

6: What MD5 hash value of the binary is listed as an Interesting File?

Head on over to “Interesting Files” located under “Interesting Items.”
<img width="546" height="672" alt="Screenshot 2025-10-01 at 6 47 33 PM" src="https://github.com/user-attachments/assets/b36cdcb1-df9a-410b-9d87-c72254425ccf" />
There are two files. Click on one of them and then look at the bottom and copy the hash. There’s only two files, so 50% chance to get it right. With my luck, I got it on my second try.
<img width="623" height="277" alt="Screenshot 2025-10-01 at 6 47 39 PM" src="https://github.com/user-attachments/assets/33611a4a-1ae8-4343-b7fd-d55fe1029e00" />
Answer: fe18b02e890f7a789c576be8abccdc99

7: What self-assuring message did the ‘Informant’ write for himself on a Sticky Note? (no spaces)

I had a hard time with this. I searched multiple terms such as “StickyNotes” and “Informant” and had no luck. I also checked Informant’s Desktop and Documents but did not find anything. I resorted to the same video once again. It looks like I was on the right track when trying to find Documents.

It seems like I had to navigate to Sticky Notes folder in the informant folder. So the path will be Data Sources -> sample-case.dd -> vol3 -> Users -> informant -> AppData -> Roaming -> Microsoft -> Sticky Notes.
<img width="370" height="653" alt="Screenshot 2025-10-01 at 6 47 45 PM" src="https://github.com/user-attachments/assets/6588e085-68f5-4ecf-9564-2b77a464e94c" />
Once there, you will see StickyNotes.snt. I’m not sure why me searching “StickyNotes” showed no results though. Once you selected the .snt file, look at the bottom and find the message.
<img width="241" height="192" alt="Screenshot 2025-10-01 at 6 47 52 PM" src="https://github.com/user-attachments/assets/94b3e4ed-4d4a-430a-bd8d-c064afc98f41" />

Answer: Tomorrow… Everything will be OK…

Task 8 Visualisation Tools

1: Using the Timeline, how many results were there on 2015–01–12?

Open the timeline by clicking “Timeline” at the top.
<img width="686" height="76" alt="Screenshot 2025-10-01 at 6 48 00 PM" src="https://github.com/user-attachments/assets/55d20f34-5181-49e3-b36c-a6730d7c0e75" />
I switched my mode to “Details” since I liked how it displayed in the readings more.
<img width="366" height="59" alt="Screenshot 2025-10-01 at 6 48 05 PM" src="https://github.com/user-attachments/assets/3885567c-0d4d-4254-8cf3-f901b8251fa0" />
I clicked on the clock icon to adjust the date I want. It may take a while to set it properly. It took me a few tries.
<img width="307" height="285" alt="Screenshot 2025-10-01 at 6 48 10 PM" src="https://github.com/user-attachments/assets/5a128898-5607-41be-ba5b-422b956df90b" />
After that, I hovered over the number 46 because it looks like there were 46 events that happened on January 15, 2015. I hovered over it until the information box came out to confirm the date.
Answer: 46
<img width="123" height="274" alt="Screenshot 2025-10-01 at 6 48 16 PM" src="https://github.com/user-attachments/assets/3829e30a-21b2-4592-a970-35f602c9ea22" />

2: The majority of file events occurred on what date? (MONTH DD, YYYY)

This took me a bit of playing around. First, I changed the view back to “Counts.”

Next, I changed the scaling of the bar graphs into Linear.

<img width="256" height="54" alt="Screenshot 2025-10-01 at 6 48 23 PM" src="https://github.com/user-attachments/assets/8c0f3eb6-3489-4154-af26-b8f8965ed5b6" />
On the left side, I changed the filters to show only events that deals with File Systems.
<img width="318" height="312" alt="Screenshot 2025-10-01 at 6 48 29 PM" src="https://github.com/user-attachments/assets/d413ed1c-94d9-4424-ad39-7c4203b33f09" />
In the middle, I changed to show the entire timeline.
<img width="226" height="480" alt="Screenshot 2025-10-01 at 6 48 35 PM" src="https://github.com/user-attachments/assets/ba95712d-c5aa-44d1-ac42-4cdcff4a5d08" />

With that, it was just a matter of me choosing which bar was the taller one.
<img width="708" height="360" alt="Screenshot 2025-10-01 at 6 48 43 PM" src="https://github.com/user-attachments/assets/453ed986-dfac-4930-863f-d62a7488265b" />
Right click the bar graph and select “Zoom into Time Range.”
<img width="226" height="387" alt="Screenshot 2025-10-01 at 6 48 48 PM" src="https://github.com/user-attachments/assets/14c38b87-c034-43d7-abe4-2916ba9b15f8" />
Then I just did it again.
<img width="286" height="435" alt="Screenshot 2025-10-01 at 6 48 54 PM" src="https://github.com/user-attachments/assets/a2f5ad0d-0656-4a04-abb3-4c23a6074113" />
I’m not sure if it’s proper but it works!

Answer: March 25, 2015

Thoughts:

Wow that was definitely challenging that I had to use external sources for help in a long time! As mentioned before, I will always post when I looked up for help because I want to show that I’m always learning, even if I am doing write-ups. I do wonder why “StickyNotes” didn’t result in “StickyNotes.snt” popping up when I searched it. I’m really interested in doing the challenge room but I might have to do that in the future. I’m very close to finishing the SOC Level 1 path that I want to just focus on that first! Just a few more rooms!








I struggled with this one. I didn’t know there was a “Recycle Bin” section under “Results.” I was too focused on the one that was located in Data Sources -> sample-case.dd -> vol3 -> $Recycle.Bin. I even used the hint for this and struggled real hard. I had to use external help. I used this to understand where the answer was found.
