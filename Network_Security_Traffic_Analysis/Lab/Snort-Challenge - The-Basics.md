TryHackMe’s Snort Challenge — The Basics is a medium-level challenge that uses Snort to investigate network traffic and stop malicious activity. This writeup will walk through all the steps required to correctly complete this challenge.
<img width="1060" height="300" alt="Screenshot 2025-09-12 at 5 08 56 PM" src="https://github.com/user-attachments/assets/36023126-3125-48d1-aaef-63fe9185a9ba" />

Task 1: Introduction
1. Read the task above.
All this task does is have us start the machine and state that it’s recommended to complete the Snort room first. The Snort room gives a basic introduction to the tool and will be helpful in completing this challenge.

Task 2: Writing IDS Rules (HTTP)
1. Write a single rule to detect “all TCP port 80 traffic” packets in the given pcap file. What is the number of detected packets?
We’ll start by opening up a terminal and navigating to the task 2 directory on our desktop. We’re given two files: local.rules and mx-3.pcap.
<img width="676" height="107" alt="Screenshot 2025-09-12 at 5 11 52 PM" src="https://github.com/user-attachments/assets/0313cd9f-d1b9-4d4a-9be8-1e1f0e30ba3e" />
We need to create a single rule that will detect any traffic on TCP port 80. I found that the Snort rules structure provided in the Snort room was very helpful in creating the rules for this challenge.
<img width="671" height="120" alt="Screenshot 2025-09-12 at 5 11 57 PM" src="https://github.com/user-attachments/assets/ac4e68c1-6938-4e00-a16d-2b7eaf269576" />
The following rule will detect all traffic on TCP port 80:
<img width="686" height="75" alt="Screenshot 2025-09-12 at 5 12 35 PM" src="https://github.com/user-attachments/assets/a8bf6c3a-d9fe-41e9-81e0-abdc6b9cb672" />
Here’s a breakdown of the rule:

alert - We want the rule to generate an alert and log the packet. We’ll see the number of alerts and logs in the statistics after running the rule.

tcp - We only want this rule to apply to TCP ports, as specified by the question.

any 80 - The rule will apply to all source IP addresses but only for traffic on port 80.

<> - The rule is bidirectional, so we do not care if the traffic is source to destination or destination to source.

any any - The destination is any IP address and any port.

msg:”TCP port 80"; - This is the message that will appear with the alert.

sid:1000001; - The Snort rule ID for our created rule.

rev:1; - The revision number for the rule.

With our rule created, we can run the following command to analyze the pcap with our rule. Note that we’ll also want to create a log file for future questions:

sudo snort -r mx-3.pcap -c local.rules -A full -l .
We can now take a look at the statistics provided in the output to see how many TCP port 80 packets were alerted on. The number is shown under the Action Stats section.
<img width="460" height="208" alt="Screenshot 2025-09-12 at 5 13 12 PM" src="https://github.com/user-attachments/assets/857d529c-6cc5-4607-9486-29d97c125d19" />
2. Investigate the log file. What is the destination address of packet 63?
Since we created the log file in the last question, we can run the following command to only process up through the 63rd packet.
<img width="649" height="56" alt="Screenshot 2025-09-12 at 5 13 19 PM" src="https://github.com/user-attachments/assets/d7d82e49-4f6a-4dc0-b9aa-0fdbb42ee60d" />
Once we run that, we can scroll up to see the destination IP in the last packet that was processed.
3. Investigate the log file. What is the ACK number of packet 64?
Similar to the last question, we can run the following command to only process up through the 64th packet.
<img width="672" height="80" alt="Screenshot 2025-09-12 at 5 14 35 PM" src="https://github.com/user-attachments/assets/53499695-1fec-4b47-9d1c-7635884572b5" />
Scrolling up shows us the Ack number for the packet.
4. Investigate the log file. What is the SEQ number of packet 62?
Again, the command is very similar to the previous one.
<img width="673" height="81" alt="Screenshot 2025-09-12 at 5 15 13 PM" src="https://github.com/user-attachments/assets/dd9561fa-3d10-4a3d-a725-9c16867e57d1" />
Scrolling up shows the Seq number for the packet.
<img width="668" height="239" alt="Screenshot 2025-09-12 at 5 15 19 PM" src="https://github.com/user-attachments/assets/f5ac198c-040b-4986-9434-d7cbd1ddcf8f" />
5. Investigate the log file. What is the TTL of packet 65?
The results from the command will be used for this question along with questions 6 and 7.
<img width="674" height="84" alt="Screenshot 2025-09-12 at 5 15 25 PM" src="https://github.com/user-attachments/assets/013c6a2b-22f1-4709-800f-f23fe8a65cae" />
Scrolling up shows the information related to the packet.

Press enter or click to view image in full size
<img width="680" height="246" alt="Screenshot 2025-09-12 at 5 15 36 PM" src="https://github.com/user-attachments/assets/12a38e20-9e7c-42da-8fe5-5e838ca0b6ee" />
6. Investigate the log file. What is the source IP of packet 65?
This can be found in the packet screenshot from question 5.

7. Investigate the log file. What is the source port of packet 65?
This can be found in the packet screenshot from question 5.

Task 3: Writing IDS Rules (FTP)
1. Use the given pcap file. Write a single rule to detect “all TCP port 21” traffic in the given pcap. What is the number of detected packets?
This question is very similar to the first question from task 2. Our rule will look nearly identical, just with a different port number. The following rule will detect the correct traffic:
<img width="669" height="70" alt="Screenshot 2025-09-12 at 5 17 33 PM" src="https://github.com/user-attachments/assets/81e3ca52-e3fc-4e38-98a7-e0240c9c3720" />
We can then run the following command to find the correct number of packets. Like Task 2, we’ll also use this to create a log file for further investigation later.
<img width="686" height="87" alt="Screenshot 2025-09-12 at 5 17 48 PM" src="https://github.com/user-attachments/assets/178a3629-ea4f-4165-9699-b070c9a2f362" />
Under the Action Stats section we can see the number of alerts generated.
<img width="671" height="197" alt="Screenshot 2025-09-12 at 5 17 54 PM" src="https://github.com/user-attachments/assets/a744559c-b548-45f8-8c9d-c1ddd1ff98c2" />

2. Investigate the log file. What is the FTP service name?
There are a few ways to complete this question. The least technical is to read the file using Snort and scroll up until you see the name of the service. This is inefficient, but can be completed with the following command:

sudo snort -r snort.log.1723772256 -X
Near the top, you’ll be able to see the name of the service.
A better way to find this is using the strings command. This command simply finds anything that appears to be a string in the file and outputs them. This still displays a lot of information, but it is easier to digest. The following command uses strings to find the correct name:

sudo strings snort.log.1723772256
Near the top of the output, the name of the service is clearly visible.

Press enter or click to view image in full size

Strings output for the log file
Finally, we can also use the grep command to make the output even better. If we assume the FTP service will include the word “FTP” we can grep for it after our strings search. The following command integrates the grep command into our strings search:

sudo strings snort.log.1723772256 | grep "FTP"
This outputs the following, which shows each instance of the FTP service name.

Press enter or click to view image in full size

Output when using strings and grep
3. Deactivate/comment on the old rules. Write a rule to detect failed FTP login attempts in the given pcap. What is the number of detected packets?
You may have noticed in the previous screenshot a code number next to the service. These codes are included in packets included in the pcap for different actions taken on the service. A quick Google search will find an article that lists all of these status codes. These will be very helpful in completing this question and other questions from this task.

Reading through the article will show us that code 530 indicates that the user is not logged in. Closer to the bottom, the code is explained in more detail.


530 status code description
Using this code, we can create a rule that will detect packets that contain this code, indicating a failed FTP login event. We can use the content rule option to identify packets with the code.

alert tcp any 21 <> any any (content:"530";sid:1000001;)
We can then run the following Snort command to use this rule with the pcap:

sudo snort -r ftp-png-gif.pcap -c local.rules
Like question 1, the number of alerts can be found under the Action Stats section.

Press enter or click to view image in full size

Number of failed login alerts
4. Write a rule to detect successful FTP logins in the given pcap. What is the number of detected packets?
Just like the last question, we can refer to the list of codes to find the one relating to successful login events. The code is 230.


Status code for a successful login event
We can simply edit our rule to look for status code 230 in the packets.

alert tcp any 21 <> any any (content:"230";sid:1000001;)
We can then run the same command with Snort to use our rule.

sudo snort -r ftp-png-gif.pcap -c local.rules
This gives us the number of alerts under the Action Stats section.

Press enter or click to view image in full size

Number of alerts for successful login events
5. Write a rule to detect FTP login attempts with a valid username but no password entered yet. What is the number of detected packets?
We’ll find that status code 331 is for “User name okay, need password.” We’ll edit our rule to look for this code. According to the documentation, this code appears regardless of whether the account is valid. However, it is the code required to get the correct answer.


What status code 331 means
We’ll use the following rule:

alert tcp any 21 <> any any (content:"331";sid:1000001;)
We’ll use the same Snort command to analyze the pcap.

sudo snort -r ftp-png-gif.pcap -c local.rules
This then gives us the number of alerts under the Action Stats section.

Press enter or click to view image in full size

Number of alerts for valid usernames but no password
6. Write a rule to detect FTP login attempts with the “Administrator” username but no password entered yet. What is the number of detected packets?
We can modify our prior rule to also include the word “Administrator”, which would be shown in the packet when attempting to log in as an administrator. We still need to include the 331 status code to ensure it only alerts for unsuccessful login attempts. Our rule will look like the following:

alert tcp any 21 <> any any (content:"Administrator";content:"331";sid:1000001;)
We’ll use the same Snort command to analyze the pcap.

sudo snort -r ftp-png-gif.pcap -c local.rules
This then gives us the number of alerts under the Action Stats section.

Press enter or click to view image in full size

Number of alerts for “Administrator” but no password
Task 4: Writing IDS Rules (PNG)
1. Write a rule to detect the PNG file in the given pcap. Investigate the logs and identify the software name embedded in the packet.
We’ll continue to use the content detection rule to identify which packet contains the PNG file. The header of the file should contain “PNG”, and should also contain the software used to create the image. We’ll use the following rule to identify the PNG file:

alert tcp any any <> any any  (content:"PNG";sid:1000001;)
We’ll then use the following command to run Snort on the pcap and also create a log file:

sudo snort -r ftp-png-gif.pcap -c local.rules -l .
With the log file created, we can use the following command to inspect the log file and see the packet details:

sudo snort -r snort.log.1723777434 -X
Then, we can scroll to the only packet and see the software name.

Press enter or click to view image in full size

The software name for the PNG in the packet
2. Write a rule to detect the GIF file in the given pcap. Investigate the logs and identify the image format embedded in the packet.
We can modify our rule to search for “GIF” instead of “PNG”. This will alert on any packets that include “GIF” in them. The following is what our new rule will look like:

alert tcp any any <> any any  (content:"GIF";sid:1000001;)
We’ll then use the following command to run Snort on the pcap and also create a log file:

sudo snort -r ftp-png-gif.pcap -c local.rules -l .
With the log file created, we can use the following command to inspect the log file and see the packet details:

sudo snort -r snort.log.1723778324 -X
Like the last question, we’ll scroll up to the packet details which shows the image format embedded in the packet.

Press enter or click to view image in full size

Image format embedded in the packet
Task 5: Writing IDS Rules (Torrent Metafile)
1. Write a rule to detect the torrent metafile in the given pcap. What is the number of detected packets?
Every torrent file that I have seen has had the extension .torrent. I confirmed this through a Google search before creating the rule, which seemed to back up my experience.

Press enter or click to view image in full size

Extension for torrent files
We can use this to create a rule that looks for “.torrent” in the content of the packets, which should give us the correct number of packets containing the metafile. The following rule will look for the extension:

alert tcp any any <> any any (content:".torrent";sid:1000001;)
We’ll then use the following command to analyze the pcap using our rule and create a log file:

sudo snort -r torrent.pcap -c local.rules -l .
This provides the number of alerts under the Action Stats page.

Press enter or click to view image in full size

Number of torrent metafiles detected in the pcap
2. Investigate the log/alarm files. What is the name of the torrent application?
Using the strings command for the log file seems to be the easiest way to analyze it. The following command will use strings to analyze the log file:

sudo strings snort.log.1723779435
The output can be used for answering the rest of the questions in this task.

Press enter or click to view image in full size

Output from using strings on the log file
The name of the torrent application can be found by looking into the string after “Accept:”. If it’s not obvious from the string, a quick Google search of the term should show the answer.

3. Investigate the log/alarm files. What is the MIME (Multipurpose Internet Mail Extensions) type of the torrent metafile?
The MIME type is the string after “Accept:” and can be found from the output in question 2.

4. Investigate the log/alarm files. What is the hostname of the torrent metafile?
The hostname is shown after “Host:” in the output from question 2.

Task 6: Troubleshooting Rule Syntax Errors
I will discuss the errors in each rule. After fixing each rule, you can run the following command to determine the number of detected packets:

 sudo snort -c local-X.rules -r mx-1.pcap
1. Fix the syntax error in local-1.rules file and make it work smoothly.
There is no space between the last “any” and the beginning of the general rule options.

2. Fix the syntax error in local-2.rules file and make it work smoothly.
An “any” is missing from the source and needs to be added.

3. Fix the syntax error in local-3.rules file and make it work smoothly.
The SID for each rule is the same.

4. Fix the syntax error in local-4.rules file and make it work smoothly.
In the second rule, the msg option ends with a colon (:) but should end with a semicolon (;).
The SID for each rule is the same.
5. Fix the syntax error in local-5.rules file and make it work smoothly.
The second rule contains an illegal direction (<-). It should be changed to ->.
The SID rule option in the second rule has a semicolon (;) before the SID number. It should be a colon (:)
In the third rule, the msg option ends with a colon (:) but should end with a semicolon (;).
6. Fix the logical error in local-6.rules file and make it work smoothly to create alerts.
The content detection rule is using HEX to try to find packets that contain “GET”. However, the rule is looking for “get”. There are two ways to remedy this, we can include the nocase rule option after the content detection rule or we can simply switch the HEX to be in caps (47 45 54).

7. Fix the logical error in local-7.rules file and make it work smoothly to create alerts.
A general rule is missing from the rule options which is used to summarize the event in the log.

Task 7: Using External Rules (MS17–010)
1. Use the given pcap file. Use the given rule file (local.rules) to investigate the ms1710 exploitation. What is the number of detected packets?
MS17–010 is also known as EternalBlue, which was developed by the NSA. The rules list was created to alert when this exploit is being used. Like with the previous questions, we just need to analyze the pcap with the provided rule. The following command will use the rule with Snort:

sudo snort -r ms-17-010.pcap -c local.rules
Now we can look under the Action Stats section to see how many alerts were triggered.

Press enter or click to view image in full size

Number of alerts triggered from the rule
2. Use local-1.rules empty file to write a new rule to detect payloads containing the “\IPC$” keyword. What is the number of detected packets?
We can utilize the content detection rule to alert us to packets containing “\IPC$”. One thing to remember is that backslash (\) is an escape character so our rule will be misinterpreted as containing an escape sequence. We can eliminate this misinterpretation by including a second backslash when creating our content rule. If we do not include this second backslash, we’ll receive a fatal error when analyzing the pcap.

Press enter or click to view image in full size

Error when using the incorrect rule
The rule we’ll use will search the content for the given string.

alert tcp any any <> any any (msg:"\\IPC$ detected";content:"\\IPC$";sid:1000001;rev:1)
You may notice that our msg general rule also contains a second backslash. We can run the rule without the second backslash in the msg, however, the backslash will not show up in our alert file. Here is the difference between the two.


Alert with only one backslash in our msg

Alert with both backslashes in our msg
This is fairly minor, and doesn’t matter much in the long term. However, when creating rules we should be as detailed and accurate as possible.

With our correct rule created, we can run the following command to analyze the pcap with our rule file. We’ll also want to create a log file to use for the next question.

sudo snort -r ms-17-010.pcap -c local-1.rules -l .
Press enter or click to view image in full size

Number of alerts generated with our rule
3. Investigate the log/alarm files. What is the requested path?
We can use snort or strings to investigate the log file. I found strings to be easier, but I’ll include the command and screenshots for both.

Command to investigate the log using Snort:

sudo snort -r snort.log.1723872066 -X
We can then scroll up to one of the packets to see the path that was requested.

Press enter or click to view image in full size

Packet that shows the requested path
Command to investigate the log using strings:

sudo strings snort.log.1723872066
This will pull out anything that looks like a string, which includes the path.

Press enter or click to view image in full size

Strings output showing the requested path
4. What is the CVSS v2 score of the MS17–010 vulnerability?
This can be found using a simple Google search. I used the NIST NVD entry which provides a wealth of information on the vulnerability.

Press enter or click to view image in full size

NIST NVD entry for MS17–010 (CVE-2017–0144)
Task 8: Using External Rules (Log4j)
1. Use the given pcap file. Use the given rule file (local.rules) to investigate the log4j exploitation. What is the number of detected packets?
Like the last task, we just need to run Snort with our rule. We’ll also want to create a log to use for the next questions.

sudo snort -r log4j.pcap -c local.rules -l .
We can then look at the Action Stats section to see the number of generated alerts.

Press enter or click to view image in full size

Generated alerts for the provided rule
2. Investigate the log/alarm files. How many rules were triggered?.
If we investigate the generated alert file, we can manually look through each and see which SID is triggered, which will tell us the rule triggered. This would be pretty time consuming and error prone, so let’s make it a bit easier.

If we simply use cat to read the alert, we’ll notice that the shown SID follows a consistent pattern.

Press enter or click to view image in full size

Alert file in snort
Here is a breakdown of what this is for [1:21003728:1]:

Generator ID (GID) : 1 — This is the first 1 that we see and identifies which component of Snort generated the alert.

Snort ID (SID): 21003728 — This is the unique identifier for the Snort rule.

Revision Number: 1 — This is the version of the rule.

We have brackets surrounding the entire string and colons between each section. Let’s use grep to isolate this string. Here is the command I used along with a breakdown of each section. If you don’t have much experience in grep or regular expressions (regex) this may seem a bit complicated, but it’s definitely worth learning. Here is the command:

grep -o '\[[0-9]*:[0-9]*:[0-9]*\]' alert
And here is a breakdown of each part:

grep - This is used for searching text using patterns that we can define

-o - This is an option that tells grep to only output the matching parts of the line. This means we’ll only see the part that matches the pattern we define.

‘\[[0–9]*:[0–9]*:[0–9]*\]’ - This is our regex that we are using to match text. Let’s break this one down a bit more:

\[ and \] - These are just the brackets that appear in the string we want to isolate. We need to escape the brackets with backslashes (\) because grep treats brackets specially.

[0–9]* - This matches zero or more digits. [0–9] will match any digit from 0–9, and the * will further match zero or more of the preceding string. This means that, for the first [0–9]*, the GID could be any combination of numbers 0–9 and the pattern would match. We’ve only seen the number 1 for the GID, but it could be different, so we should account for that.

: - This is the colon that breaks up the GID, SID, and revision number

We can look at [0–9]*:[0–9]*:[0–9]* as matching the pattern “zero or more digits, followed by a colon, zero or more digits, followed by a colon, and zero or more digits.” This means that our pattern accounts for any GID number, any SID number, and any revision number.

alert - This is the name of our file that grep is searching through.

We can use this command to get the following output:

Press enter or click to view image in full size

Output for our command
This is really good, and makes it easy to look through each SID. We can do better, though. We can use the cut command to isolate only the SID portion of the string. The following command will use our grep command and cut to only show the SID:

grep -o '\[[0-9]*:[0-9]*:[0-9]*\]' alert | cut -d: -f2
I’ll break down the addition of our new command:

| - The pipe will take the output from the grep command and uses it as input for the cut command (takes from the left and feeds it to the right).

cut - This command extracts sections from input data.

-d: - This specifies the delimiter used for splitting the input. The delimiter we want to use is a colon, which splits the string into separate sections.

-f2 - This tells cut to extract and print the second field of input, which has been split by the delimiter. Our input has been split into three sections due to our delimiter. So, if we used -f1, our output would be [1 and if we used -f3 the output would be 1]. This means -f2 will isolate just the SID.

With the addition of cut, our output will just tell us the SID.

Press enter or click to view image in full size

Isolating just the SID using cut
Finally, we can use another command to only output the unique SID numbers, which will show us the rules triggered. Using the sort command can output only the unique SIDs.

grep -o '\[[0-9]*:[0-9]*:[0-9]*\]' alert | cut -d: -f2 | sort -u
Here’s a quick breakdown:

| - Again, this will take the output from the right (our SIDs) and use it as input for the left (the sort command).

sort - This command is used to sort lines of input

-u - This option is used with sort to only output unique lines. Any duplicates are removed from the sorted list.

When we run the full command, we get the output of the unique SIDs (rules) that were triggered.

Press enter or click to view image in full size

Finding the number of unique rules triggered
Now, this has already been fairly complicated just to find the number of rules triggered, but we may want to go a step further. The number of rules triggered for this question is very small and easy to count. However, if dozens or hundreds of rules were triggered in a single alert file, it would be much harder to get the number. We can add one final command to get the exact number of rules triggered. Using the wc command will provide us just the number as output.

grep -o '\[[0-9]*:[0-9]*:[0-9]*\]' alert | cut -d: -f2 | sort -u | wc -l
Breakdown:

| - Again, this will take the output from the right (our SIDs) and use it as input for the left (the sort command).

wc - This stands for “word count” and is used to count lines, words, or characters from input data

-l - This option tells wc to only count and print the number of lines from the input.

In summary, our entire command searches through the entire alert file and outputs a specific pattern, we then isolate the SID from the string, sort it by unique SIDs, and then output a final number of unique SIDs that were triggered.

Press enter or click to view image in full size

Output of our final command
3. Investigate the log/alarm files. What are the first six digits of the triggered rule sids?
This can be found while looking through the SIDs of the previous question.

4. Use local-1.rules empty file to write a new rule to detect packet payloads between 770 and 855 bytes. What is the number of detected packets?
We can use the dsize detection rule to filter by packet payload size. The following rule will search all TCP traffic for packets between 770 and 855 bytes:

alert tcp any any <> any any (msg:"Packet between 770 and 855";dsize:770<>855;sid:1000001;rev:1;)
We can then use Snort with the rule to analyze the pcap and find the number of packets between this size. We’ll also want to create a log file for the questions after.

sudo snort -r log4j.pcap -c local-1.rules -l .
Looking under Action Stats will tell us the number of alerts for packets between the given size.

Press enter or click to view image in full size

Alerts generated for the packet size
5. Investigate the log/alarm files. What is the name of the used encoding algorithm?
We can use Snort to analyze the log file we created in the previous question using the following command:

sudo snort -r snort.log.1723880111 -X
Scrolling through the packets will show an encoding algorithm.

Press enter or click to view image in full size

Finding the encoding algorithm
6. Investigate the log/alarm files. What is the IP ID of the corresponding packet?
We can see the ID in the packet found in the previous question.

7. Investigate the log/alarm files. Decode the encoded command. What is the attacker’s command?
We need to isolate the encoded command we saw in the packet. I found the easiest way to grab the encoded command was to use strings on the log file. The following command will output every string in the file:

sudo strings snort.log.1723880111
This outputs the the entire encoded command.

Press enter or click to view image in full size

Using strings to find the command
We can then copy the command and paste it into CyberChef to find the decoded command. We’ll need to use the correct recipe to with the algorithm found from question 5.

Press enter or click to view image in full size

Using CyberChef to decode the command
8. What is the CVSS v2 score of the Log4j vulnerability?
Like the last task, I used a Google search to find the NIST NVD entry for the vulnerability.

Press enter or click to view image in full size

CVSS 2.0 score for the vulnerability
Task 9: Conclusion
1. Read the task above.
We just need to click the button.

We’ve completed the room! We used Snort and other tools to investigate network traffic and create rules. If you’re struggling with the room or have questions, please leave a comment or message me on LinkedIn and I will try my best to assist!

Lessons Learned:
Using other terminal commands with Snort output can make investigating traffic much easier than just using Snort.
Snort rules are fairly strict with how they must be constructed. Small errors can break a rule and stop Snort from working properly.
Things I struggled with:
I struggled a bit with remembering how to construct rules and the commands for Snort. I ended up having to review and refer to my notes quite a bit to remember everything. The regex portion of task 8 took me a long time to get right. I don’t have a ton of experience with constructing and using regex, so I struggled more than I should have with fully understanding everything. I kept getting an error when using Snort with the rule to detect packet payloads (ERROR: Can’t initialize DAQ pcap (-1) — unknown file format). I messed around with everything for a long time before just restarting the machine and redoing it. I’m not sure if I did anything different, but the rule and Snort worked the first time after.

Conclusion:
This room is fantastic. It really pushed me to fully understand the concepts taught in the Snort introduction room. Some of the questions were a bit repetitive, so I think a little more variety with the questions would be good. However, the repetition helped me use the commands without having to check my notes. Overall, this room is perfect for anyone trying to get better at Snort or test their skills.




