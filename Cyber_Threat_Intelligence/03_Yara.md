<img width="1440" height="313" alt="Screenshot 2025-09-06 at 7 33 29 PM" src="https://github.com/user-attachments/assets/1009ff9b-a571-4a8e-8e01-54cc74d2ce6b" />
Task 1 Introduction Introduction
This room will expect you to understand basic Linux familiarity, such as installing software and commands for general navigation of the system. Moreso, this room isn’t designed to test your knowledge or for point-scoring. It is here to encourage you to follow along and experiment with what you have learned here.

As always, I hope you take a few things away from this room, namely, the wonder that Yara (Yet Another Ridiculous Acronym) is and its importance in infosec today. Yara was developed by Victor M. Alvarez (@plusvic) and @VirusTotal. Check the GitHub repo here.

Answer the questions below

Let’s get started

Task 2 What is Yara?
All about Yara
“The pattern matching swiss knife for malware researchers (and everyone else)” (Virustotal., 2020)

With such a fitting quote, Yara can identify information based on both binary and textual patterns, such as hexadecimal and strings contained within a file.

Rules are used to label these patterns. For example, Yara rules are frequently written to determine if a file is malicious or not, based upon the features — or patterns — it presents. Strings are a fundamental component of programming languages. Applications use strings to store data such as text.

For example, the code snippet below prints “Hello World” in Python. The text “Hello World” would be stored as a string.
<img width="671" height="83" alt="Screenshot 2025-09-06 at 7 34 24 PM" src="https://github.com/user-attachments/assets/71734fc8-e130-45e8-a78d-cd714b925c3e" />
We could write a Yara rule to search for “hello world” in every program on our operating system if we would like.

Why does Malware use Strings?
Malware, just like our “Hello World” application, uses strings to store textual data. Here are a few examples of the data that various malware types store within strings:
<img width="699" height="81" alt="Screenshot 2025-09-06 at 7 34 33 PM" src="https://github.com/user-attachments/assets/851ec9ab-acec-4d35-8f13-eecb41209869" />
Caveat: Malware Analysis
Explaining the functionality of malware is vastly out of scope for this room due to the sheer size of the topic. I have covered strings in much more detail in “Task 12 — Strings” of my MAL: Introductory room. In fact, I am creating a whole Learning Path for it. If you’d like to get a taster whilst learning the fundamentals, I’d recommend my room.

Answer the questions below

2.1 What is the name of the base-16 numbering system that Yara can detect? (This is also known as “hex”. An example of this is: ff745c9b137d86e)

Hexadecimal is a numeral system that uses 16 symbols, which are:

0 to 9 (representing values 0 to 9)

A to F (representing values 10 to 15)

In Yara, hexadecimal is frequently used to represent binary data in a more human-readable form. When malware researchers are analyzing files, they often encounter raw binary data that needs to be interpreted. Hexadecimal helps convert large binary numbers into a more compact and understandable format.

If you have a hexadecimal value like ff745c9b137d86e, it represents a sequence of binary data. In this case:

ff = 11111111 in binary

74 = 01110100 in binary

5c = 01011100 in binary

And so on.

Yara uses rules that can detect these patterns (often in the form of hexadecimal) to identify whether a file is malicious.

Example:
Imagine a piece of malware that communicates with a Command and Control server. The malware might store an IP address in hexadecimal format, such as 12.34.56.7, which could be represented as 0C 22 38 47 in hex. Yara rules can be written to detect this hexadecimal pattern to identify potential malicious activity based on known indicators.

Thus, the hexadecimal (or hex) numbering system plays a vital role in malware detection by representing binary data, which Yara can search for using patterns.

Answer: Hexadecimal

2.2 Would the text “Enter your Name” be a string in an application? (Yay/Nay)

The text “Enter your Name” would indeed be considered a string in an application. In programming, a string is simply a sequence of characters, typically used to represent textual data.

String Definition: A string is any sequence of characters, which can include letters, numbers, punctuation, and spaces. The text “Enter your Name” falls under this definition because it is a sequence of characters, specifically intended for display or input by the user.

Example:
If you are developing a user interface (UI) in an application, you might prompt users to enter their name. The text “Enter your Name” would be displayed in a text box or a label, and it would be handled by the application as a string. It could be stored in a variable or used directly to present instructions to the user.

Answer: Yay

Task 3 Deploy
This room deploys an Instance with the tools being showcased already installed for you. Press the “Start Machine” button and wait for an IP address to be displayed and connect in one of two ways:

In-Browser (No VPN required)

Deploy your own instance by pressing the green “Start Machine” button and scroll up to the top of the room and await the timer. The machine will start in a split-screen view. In case the VM is not visible, use the blue “Show Split View” button at the top-right of the page.

<img width="678" height="657" alt="Screenshot 2025-09-06 at 7 34 44 PM" src="https://github.com/user-attachments/assets/28cbf62f-bc34-4aa6-bef2-9012ef69a3fa" />
Using SSH (TryHackMe VPN required).

You must be connected to the TryHackMe VPN if you wish to connect your deployed Instance from your own device. If you are unfamiliar with this process, please visit the TryHackMe OpenVPN room to get started. If you have any issues, please read our support articles.

IP Address: MACHINE_IP

Username: cmnatic

Password: yararules!

SSH Port: 22
<img width="884" height="618" alt="Screenshot 2025-09-06 at 7 34 54 PM" src="https://github.com/user-attachments/assets/950f68d9-610b-4d96-ab88-001e4d502435" />

Enter the password when asked
<img width="675" height="84" alt="Screenshot 2025-09-06 at 7 36 38 PM" src="https://github.com/user-attachments/assets/8cda0021-f162-4b24-82e4-b28f44c5dc01" />
Answer the questions below

I’ve connected to my instance!

Task 4 Introduction to Yara Rules
Your First Yara Rule
The proprietary language that Yara uses for rules is fairly trivial to pick up, but hard to master. This is because your rule is only as effective as your understanding of the patterns you want to search for.

Using a Yara rule is simple. Every yara command requires two arguments to be valid, these are:
1) The rule file we create
2) Name of file, directory, or process ID to use the rule for.

Every rule must have a name and condition.

For example, if we wanted to use "myrule.yar" on directory "some directory", we would use the following command:
<img width="674" height="78" alt="Screenshot 2025-09-06 at 7 37 47 PM" src="https://github.com/user-attachments/assets/c5970f6b-f4ce-4f97-9df9-cf6d70134c7f" />
Note that .yar is the standard file extension for all Yara rules.

We'll make one of the most basic rules you can make below.

1. Make a file named "somefile" via touch somefile
2. Create a new file and name it "myfirstrule.yar" like below:

Creating a file named somefile
<img width="805" height="245" alt="Screenshot 2025-09-06 at 7 37 54 PM" src="https://github.com/user-attachments/assets/ae3d0adc-f6c1-45ed-84b3-24392d4d15e0" />
Creating a file named myfirstrule.yar
<img width="868" height="270" alt="Screenshot 2025-09-06 at 7 38 02 PM" src="https://github.com/user-attachments/assets/45a59f4c-1fa0-4d58-83ec-6bf16f076274" />

3. Open the “myfirstrule.yar” using a text editor such as nano and input the snippet below and save the file:
   <img width="848" height="492" alt="Screenshot 2025-09-06 at 7 38 16 PM" src="https://github.com/user-attachments/assets/ad2629ef-c061-4dd1-9068-3ca604685ee4" />
Write a valid YARA rule inside the file
<img width="830" height="539" alt="Screenshot 2025-09-06 at 7 38 26 PM" src="https://github.com/user-attachments/assets/a29ac89e-46ea-4cd7-ad99-36cce8195513" />
Save the file: Press CTRL + X
Press Y to confirm saving
Press Enter to save and exit

Inputting our first snippet into “myfirstrule.yar” using nano
<img width="676" height="141" alt="Screenshot 2025-09-06 at 7 43 12 PM" src="https://github.com/user-attachments/assets/501bdd2c-caa1-4758-84df-9ac403b7d0ee" />
The name of the rule in this snippet is examplerule, where we have one condition - in this case, the condition is condition. As previously discussed, every rule requires both a name and a condition to be valid. This rule has satisfied those two requirements.

Simply, the rule we have made checks to see if the file/directory/PID that we specify exists via condition: true. If the file does exist, we are given the output of examplerule

Let's give this a try on the file "somefile" that we made in step one:
yara myfirstrule.yar somefile

If "somefile" exists, Yara will say examplerule because the pattern has been met - as we can see below:

Verifying our the examplerule is correct
<img width="786" height="245" alt="Screenshot 2025-09-06 at 7 43 23 PM" src="https://github.com/user-attachments/assets/82525061-77d5-4042-97d8-5aef7bae21ce" />
YARA scanned somefile using your rule from myfirstrule.yar.
Since examplerule somefile appeared in the output, this confirms that the rule conditions were met for somefile.
The rule l has the condition true, which means it always matches any file.
If the file does not exist, Yara will output an error such as that below:

Yara complaining that the file does not exist
<img width="693" height="110" alt="Screenshot 2025-09-06 at 7 43 42 PM" src="https://github.com/user-attachments/assets/aae274b3-e451-426f-baec-3d8d02a66a77" />
Congrats! I made my first rule.

Answer the questions below

One rule to — well — rule them all.
Task 5 Expanding on Yara Rules
Yara Conditions Continued…
Checking whether or not a file exists isn’t all that helpful. After all, we can figure that out for ourselves…Using much better tools for the job.

Yara has a few conditions, which I encourage you to read here at your own leisure.

The following keywords are reserved and cannot be used as an identifier:
<img width="678" height="288" alt="Screenshot 2025-09-06 at 7 47 29 PM" src="https://github.com/user-attachments/assets/57ad7bee-c89d-43fc-aee7-89a27b6ca507" />
However, I’ll detail a few below and explain their purpose.

Keyword
Desc
Meta
Strings
Conditions
Weight

Meta
This section of a Yara rule is reserved for descriptive information by the author of the rule. For example, you can use desc, short for description, to summarise what your rule checks for. Anything within this section does not influence the rule itself. Similar to commenting code, it is useful to summarise your rule.

Strings
Remember our discussion about strings in Task 2? Well, here we go. You can use strings to search for specific text or hexadecimal in files or programs. For example, say we wanted to search a directory for all files containing “Hello World!”, we would create a rule such as below:
<img width="680" height="142" alt="Screenshot 2025-09-06 at 7 47 41 PM" src="https://github.com/user-attachments/assets/d76ec73a-2427-4fb2-b06f-2a7de2ea020d" />
We define the keyword Strings where the string that we want to search, i.e., "Hello World!" is stored within the variable $hello_world

Of course, we need a condition here to make the rule valid. In this example, to make this string the condition, we need to use the variable's name. In this case, $hello_world:
<img width="683" height="232" alt="Screenshot 2025-09-06 at 7 47 56 PM" src="https://github.com/user-attachments/assets/77959050-fe9c-4d92-b7fc-712e32a06267" />
Essentially, if any file has the string “Hello World!” then the rule will match. However, this is literally saying that it will only match if “Hello World!” is found and will not match if “hello world” or “HELLO WORLD.”

To solve this, the condition any of them allows multiple strings to be searched for, like below:
<img width="677" height="271" alt="Screenshot 2025-09-06 at 7 48 07 PM" src="https://github.com/user-attachments/assets/80962eeb-8590-4b78-991e-b2d36ef44668" />
Now, any file with the strings of:

1. Hello World!

2. hello world

3. HELLO WORLD

Will now trigger the rule.

Conditions
We have already used the true and any of them condition. Much like regular programming, you can use operators such as:

<= less than or equal to
>= more than or equal to
!= not equal to
For example, the rule below would do the following:
><img width="682" height="230" alt="Screenshot 2025-09-06 at 7 48 18 PM" src="https://github.com/user-attachments/assets/e76a8820-dce1-4ea1-9af5-824f0c02d0f1" />

The rule will now:
1. Look for the “Hello World!” string
2. Only say the rule matches if there are less than or equal to ten occurrences of the “Hello World!” string

Combining keywords
Moreover, you can use keywords such as:

and
not
or
To combine multiple conditions. Say if you wanted to check if a file has a string and is of a certain size (in this example, the sample file we are checking is less than <10 kb and has “Hello World!” you can use a rule like below:
<img width="675" height="199" alt="Screenshot 2025-09-06 at 7 48 31 PM" src="https://github.com/user-attachments/assets/410c5deb-52e1-4731-ae30-1c5deff4f0ec" />
The rule will only match if both conditions are true. To illustrate: below, the rule we created, in this case, did not match because although the file has “Hello World!”, it has a file size larger than 10KB:
Yara failing to match the file mytextfile because it is larger than 10kb
<img width="679" height="88" alt="Screenshot 2025-09-06 at 7 48 40 PM" src="https://github.com/user-attachments/assets/6b8d750d-0f18-427c-9e91-4e44cbcc4fba" />
However, the rule matched this time because the file has both “Hello World!” and a file size of less than 10KB.

Yara successfully matching the file mytextfile because it has “Hello World” and a file size of less than 10KB
<img width="679" height="102" alt="Screenshot 2025-09-06 at 7 48 50 PM" src="https://github.com/user-attachments/assets/1c1e158d-c590-4a32-ac3d-41059c193b76" />
Remembering that the text within the red box is the name of our rule, and the text within the green is the matched file.

Anatomy of a Yara Rule


<img width="619" height="666" alt="Screenshot 2025-09-06 at 7 54 57 PM" src="https://github.com/user-attachments/assets/71838c1d-a305-4e26-88a2-112fe9b7b68b" />

<img width="611" height="267" alt="Screenshot 2025-09-06 at 7 55 06 PM" src="https://github.com/user-attachments/assets/34030e5f-c86d-43fb-aa26-1715db18dfc7" />
Information security researcher “fr0gger_” has recently created a handy cheatsheet that breaks down and visualises the elements of a YARA rule (shown above, all image credits go to him). It’s a great reference point for getting started!

Answer the questions below

Upwards and onwards…

Task 6 Yara Modules
Integrating With Other Libraries
Frameworks such as the Cuckoo Sandbox or Python’s PE Module allow you to improve the technicality of your Yara rules ten-fold.

Cuckoo
Cuckoo Sandbox is an automated malware analysis environment. This module allows you to generate Yara rules based upon the behaviours discovered from Cuckoo Sandbox. As this environment executes malware, you can create rules on specific behaviours such as runtime strings and the like.

Python PE
Python’s PE module allows you to create Yara rules from the various sections and elements of the Windows Portable Executable (PE) structure.

Explaining this structure is out of scope as it is covered in my malware introductory room. However, this structure is the standard formatting of all executables and DLL files on windows. Including the programming libraries that are used.

Examining a PE file’s contents is an essential technique in malware analysis; this is because behaviours such as cryptography or worming can be largely identified without reverse engineering or execution of the sample.

Answer the questions below

Sounds pretty cool!

Task 7 Other tools and Yara
Yara Tools
Knowing how to create custom Yara rules is useful, but luckily you don’t have to create many rules from scratch to begin using Yara to search for evil. There are plenty of GitHub resources and open-source tools (along with commercial products) that can be utilized to leverage Yara in hunt operations and/or incident response engagements.

LOKI (What, not who, is Loki?)
LOKI is a free open-source IOC (Indicator of Compromise) scanner created/written by Florian Roth.

Based on the GitHub page, detection is based on 4 methods:

File Name IOC Check
Yara Rule Check (we are here)
Hash Check
C2 Back Connect Check
There are additional checks that LOKI can be used for. For a full rundown, please reference the GitHub readme.

LOKI can be used on both Windows and Linux systems and can be downloaded here.

Please note that you are not expected to use this tool in this room.

Displaying Loki’s help menu


<img width="673" height="400" alt="Screenshot 2025-09-06 at 7 57 37 PM" src="https://github.com/user-attachments/assets/f7ba577e-3b56-4704-b0cb-b9ed8ee3ba7d" />
THOR (superhero named programs for a superhero blue teamer)
THOR Lite is Florian’s newest multi-platform IOC AND YARA scanner. There are precompiled versions for Windows, Linux, and macOS. A nice feature with THOR Lite is its scan throttling to limit exhausting CPU resources. For more information and/or to download the binary, start here. You need to subscribe to their mailing list to obtain a copy of the binary. Note that THOR is geared towards corporate customers. THOR Lite is the free version.

Please note that you are not expected to use this tool in this room.

Displaying Thor Lite’s help menu

<img width="679" height="585" alt="Screenshot 2025-09-06 at 7 57 46 PM" src="https://github.com/user-attachments/assets/46d74f76-1b9d-4042-88fa-4fc237e325af" />
FENRIR (naming convention still mythical themed)
This is the 3rd tool created by Neo23x0 (Florian Roth). You guessed it; the previous 2 are named above. The updated version was created to address the issue from its predecessors, where requirements must be met for them to function. Fenrir is a bash script; it will run on any system capable of running bash (nowadays even Windows).

Please note that you are not expected to use this tool in this room.

Running Fenrir

<img width="678" height="312" alt="Screenshot 2025-09-06 at 7 57 55 PM" src="https://github.com/user-attachments/assets/95395a72-bc80-43b5-964d-b4977e08f39a" />
YAYA (Yet Another Yara Automaton)
YAYA was created by the EFF (Electronic Frontier Foundation) and released in September 2020. Based on their website, “YAYA is a new open-source tool to help researchers manage multiple YARA rule repositories. YAYA starts by importing a set of high-quality YARA rules and then lets researchers add their own rules, disable specific rulesets, and run scans of files.”

Note: Currently, YAYA will only run on Linux systems.

Running YAYA

<img width="691" height="254" alt="Screenshot 2025-09-06 at 7 58 04 PM" src="https://github.com/user-attachments/assets/5dfd3583-0d7b-4cfc-9867-0538ab0f0f15" />
In the next section, we will examine LOKI further…

Answer the questions below

Cool tools. I’m ready to use one of them.

Task 8 Using LOKI and its Yara rule set
Using LOKI
As a security analyst, you may need to research various threat intelligence reports, blog postings, etc. and gather information on the latest tactics and techniques used in the wild, past or present. Typically in these readings, IOCs (hashes, IP addresses, domain names, etc.) will be shared so rules can be created to detect these threats in your environment, along with Yara rules. On the flip side, you might find yourself in a situation where you’ve encountered something unknown, that your security stack of tools can’t/didn’t detect. Using tools such as Loki, you will need to add your own rules based on your threat intelligence gathers or findings from an incident response engagement (forensics).

As mentioned before, Loki already has a set of Yara rules that we can benefit from and start scanning for evil on the endpoint straightaway.

Loki is located in the tools.

Listing the tools directory

<img width="722" height="291" alt="Screenshot 2025-09-06 at 8 00 14 PM" src="https://github.com/user-attachments/assets/af69e306-ac3c-41d2-bb12-174b93cffe32" />
Navigate to the Loki directory.

<img width="715" height="293" alt="Screenshot 2025-09-06 at 8 00 21 PM" src="https://github.com/user-attachments/assets/4c26fcbd-4c95-4343-b93f-0078a572f1ac" />
Run python loki.py -h to see what options are available.

<img width="960" height="710" alt="Screenshot 2025-09-06 at 8 00 31 PM" src="https://github.com/user-attachments/assets/970ed8c4-2c52-4c5d-b88e-32debe383360" />
If you are running Loki on your own system, the first command you should run is --update. This will add the signature-base directory, which Loki uses to scan for known evil. This command was already executed within the attached VM.

Listing Loki signature-base directory

<img width="793" height="388" alt="Screenshot 2025-09-06 at 8 07 31 PM" src="https://github.com/user-attachments/assets/af305ffa-9515-43dd-939f-52a31415a9c3" />
Navigate to the yara directory.

<img width="758" height="248" alt="Screenshot 2025-09-06 at 8 07 39 PM" src="https://github.com/user-attachments/assets/24e1bd13-08e7-4b13-b9e6-2b422a530ca1" />
Feel free to inspect the different Yara files used by Loki to get an idea of what these rules will hunt for.

To run Loki, you can use the following command (note that I am calling Loki from within the file 1 directory)

Instructing Loki to scan the suspicious file

<img width="683" height="81" alt="Screenshot 2025-09-06 at 8 07 48 PM" src="https://github.com/user-attachments/assets/70e4410e-7085-477b-9a06-62d19028b542" />
Scenario: You are the security analyst for a mid-size law firm. A co-worker discovered suspicious files on a web server within your organization. These files were discovered while performing updates to the corporate website. The files have been copied to your machine for analysis. The files are located in the suspicious-files directory. Use Loki to answer the questions below.

Answer the questions below

8.1 Scan file 1. Does Loki detect this file as suspicious/malicious or benign?

Listed the contents of the home directory

Navigate to suspicious-files and listed the Contents

Navigate to file1 and run the loki.py Script

<img width="705" height="479" alt="Screenshot 2025-09-06 at 8 07 58 PM" src="https://github.com/user-attachments/assets/78d202aa-7e28-4a47-aae9-d59da3dae5cd" />

<img width="675" height="513" alt="Screenshot 2025-09-06 at 8 08 06 PM" src="https://github.com/user-attachments/assets/6836fa11-02f0-4f35-8a47-54d85ac8c11c" />

Answer: Suspicious

8.2 What Yara rule did it match on?

<img width="679" height="510" alt="Screenshot 2025-09-06 at 8 08 15 PM" src="https://github.com/user-attachments/assets/979bd7f4-e86b-495b-948f-2efd1b923392" />
Answer: webshell_metaslsoft

8.3 What does Loki classify this file as? (Question Hint Check description)

Press enter or click to view image in full size

<img width="670" height="514" alt="Screenshot 2025-09-06 at 8 08 27 PM" src="https://github.com/user-attachments/assets/ea9848ba-533f-47c8-af5f-0aed76480c91" />
Answer: Web shell

8.4 Based on the output, what string within the Yara rule did it match on?

<img width="680" height="506" alt="Screenshot 2025-09-06 at 8 08 36 PM" src="https://github.com/user-attachments/assets/16d9b690-c496-4a0f-adfb-3740119d1e56" />
Answer: str1

8.5 What is the name and version of this hack tool?

The first bytes show that the file starts with a PHP tag (<?php), followed by the string /*b374k 2.2, which reveals that the file contains a b374k web shell tool, version 2.2.


<img width="679" height="504" alt="Screenshot 2025-09-06 at 8 08 48 PM" src="https://github.com/user-attachments/assets/b5c20c99-f859-4f30-8b77-d2af7b3b6fe4" />

Answer: b374k 2.2

8.6 Inspect the actual Yara file that flagged file 1. Within this rule, how many strings are there to flag this file? (Question Hint yara/thor-webshells.yar)

Navigate to the signature-base/yara directory

Navigating to signature-basels

<img width="712" height="189" alt="Screenshot 2025-09-06 at 8 08 56 PM" src="https://github.com/user-attachments/assets/18c20b93-794f-46b9-87d2-cb5d71497eff" />
List the Yara files in the directory

<img width="695" height="180" alt="Screenshot 2025-09-06 at 8 09 04 PM" src="https://github.com/user-attachments/assets/ea24a360-0c34-4d06-bc72-b02a1e4e179c" />
Inspect Yara rule thor-webshells.yar using nano text editor to see how many strings are used for flagging files

<img width="740" height="197" alt="Screenshot 2025-09-06 at 8 15 03 PM" src="https://github.com/user-attachments/assets/0883fcf8-9367-45c8-8c84-9752cb90826c" />

<img width="674" height="582" alt="Screenshot 2025-09-06 at 8 15 09 PM" src="https://github.com/user-attachments/assets/d7e8aed3-3f92-417d-adc2-5b6191948c34" />

Any one of the strings that match a part of the file will trigger the rule. This means if LOKI finds just one of the patterns (“eval(base64_decode(“), it will flag the file.

The Yara rule you are inspecting has multiple strings, but only one string needs to match in the file for it to be flagged as suspicious or malicious.

Answer: 1

8.7 Scan file 2. Does Loki detect this file as suspicious/malicious or benign?

Navigate to file 2 and Run LOKI to Scan

<img width="716" height="561" alt="Screenshot 2025-09-06 at 8 15 18 PM" src="https://github.com/user-attachments/assets/a1b72041-8778-48ba-9e71-616b5315b9ef" />
The scan results indicate that LOKI did not detect anything suspicious in file 2.

<img width="676" height="424" alt="Screenshot 2025-09-06 at 8 15 27 PM" src="https://github.com/user-attachments/assets/b5126412-28eb-4958-8d59-6d167b15774b" />
This suggests that file 2 is benign and does not pose any security threat based on the scan.

Answer: Benign

8.8 Inspect file 2. What is the name and version of this web shell? (Question Hint Read the comments in the file)

Display the contents of 1ndex.php

<img width="688" height="209" alt="Screenshot 2025-09-06 at 8 15 37 PM" src="https://github.com/user-attachments/assets/21c19a83-261f-44ed-9f3c-34c43180a0dc" />

<img width="679" height="592" alt="Screenshot 2025-09-06 at 8 15 45 PM" src="https://github.com/user-attachments/assets/d7d68215-a977-49ce-a9b3-e9b3fde38687" />
b374k is a web shell that allows attackers to control a compromised web server. It is a popular web shell used in penetration testing and web attacks.

The version of this b374k shell is 3.2.3.

Answer: b374k 3.2.3

Task 9 Creating Yara rules with yarGen
Creating Yara rules with yarGen
From the previous section, we realized that we have a file that Loki didn’t flag on. At this point, we are unable to run Loki on other web servers because if file 2 exists in any of the webs servers, it will go undetected.

We need to create a Yara rule to detect this specific web shell in our environment. Typically this is what is done in the case of an incident, which is an event that affects/impacts the organization in a negative fashion.

We can manually open the file and attempt to sift through lines upon lines of code to find possible strings that can be used in our newly created Yara rule.

Let’s check how many lines this particular file has. You can run the following: strings <file name> | wc -l.

Using wc to count the amount of lines in the file

<img width="687" height="216" alt="Screenshot 2025-09-06 at 8 15 56 PM" src="https://github.com/user-attachments/assets/39d0a278-d79b-4cca-8133-39e5783077aa" />
If you try to go through each string, line by line manually, you should quickly realize that this can be a daunting task.

Catting the output of 1ndex.php

<img width="634" height="720" alt="Screenshot 2025-09-06 at 8 16 12 PM" src="https://github.com/user-attachments/assets/b976c461-47ed-46e2-aae4-81de7854eb2f" />
Luckily, we can use yarGen (yes, another tool created by Florian Roth) to aid us with this task.

What is yarGen? yarGen is a generator for YARA rules.

From the README — “The main principle is the creation of yara rules from strings found in malware files while removing all strings that also appear in goodware files. Therefore yarGen includes a big goodware strings and opcode database as ZIP archives that have to be extracted before the first use.”

Navigate to the yarGen directory, which is within tools.

<img width="682" height="310" alt="Screenshot 2025-09-06 at 8 16 21 PM" src="https://github.com/user-attachments/assets/af2ab008-c381-4eff-a425-c1b3e9288334" />

If you are running yarGen on your own system, you need to update it first by running the following command: python3 yarGen.py --update.

This will update the good-opcodes and good-strings DB’s from the online repository. This update will take a few minutes.

Once it has been updated successfully, you’ll see the following message at the end of the output.

Updating yarGen

<img width="638" height="397" alt="Screenshot 2025-09-06 at 8 16 33 PM" src="https://github.com/user-attachments/assets/f3d24c47-ab75-401b-b86a-2499fb8088a2" />

To use yarGen to generate a Yara rule for file 2, you can run the following command:

<img width="688" height="292" alt="Screenshot 2025-09-06 at 8 16 42 PM" src="https://github.com/user-attachments/assets/bc8bce07-8a2d-4a48-a19e-437f8efc7904" />
A brief explanation of the parameters above:

-m is the path to the files you want to generate rules for
--excludegood force to exclude all goodware strings (these are strings found in legitimate software and can increase false positives)
-o location & name you want to output the Yara rule
If all is well, you should see the following output.

Using yarGen to generate a rule for file2

<img width="683" height="258" alt="Screenshot 2025-09-06 at 8 16 51 PM" src="https://github.com/user-attachments/assets/aa3013c0-b320-4911-bd71-041c1b612583" />


Check if the YARA rule was created

If file2.yar appears, the rule was successfully generated.
<img width="790" height="240" alt="Screenshot 2025-09-06 at 8 22 53 PM" src="https://github.com/user-attachments/assets/dcd37120-8e35-4b9d-8129-0ecd58ffede5" />
Generally, you would examine the Yara rule and remove any strings that you feel might generate false positives. For this exercise, we will leave the generated Yara rule as is and test to see if Yara will flag file 2 or no.

Note: Another tool created to assist with this is called yarAnalyzer (you guessed it — created by Florian Roth). We will not examine that tool in this room, but you should read up on it, especially if you decide to start creating your own Yara rules.

Further Reading on creating Yara rules and using yarGen:

https://www.bsk-consulting.de/2015/02/16/write-simple-sound-yara-rules/
https://www.bsk-consulting.de/2015/10/17/how-to-write-simple-but-sound-yara-rules-part-2/
https://www.bsk-consulting.de/2016/04/15/how-to-write-simple-but-sound-yara-rules-part-3/
Answer the questions below

9.1 From within the root of the suspicious files directory, what command would you run to test Yara and your Yara rule against file 2? (Question Hint Use the same name I called the Yara file to answer this question)

<img width="703" height="214" alt="Screenshot 2025-09-06 at 8 23 56 PM" src="https://github.com/user-attachments/assets/0487c5b0-f489-412d-8815-126696e74d3e" />

We are inside the suspicious-files directory, so we do not need the full path (~/suspicious-files/).
file2.yar > This is the YARA rule generated earlier.
file2/1ndex.php > This is the actual suspicious web shell file inside the file2 directory.
Running this command applies the YARA rule to 1ndex.php, checking for any matches.

Answer: yara file2.yar file2/1ndex.php

9.2 Did Yara rule flag file 2? (Yay/Nay)

YARA flagged 1ndex.php as suspicious.
The rule worked, and the file matches the patterns in file2.yar.

Answer: Yay

9.3 Copy the Yara rule you created into the Loki signatures directory.

<img width="710" height="180" alt="Screenshot 2025-09-06 at 8 24 04 PM" src="https://github.com/user-attachments/assets/f5c2107b-4dc4-492a-b05c-2dc4fe327d7c" />
Verify that the file was copied successfully

<img width="678" height="210" alt="Screenshot 2025-09-06 at 8 24 14 PM" src="https://github.com/user-attachments/assets/e86aff76-69bd-4095-95b7-c5ec8016999c" />
Answer: No answer nedeed

9.4 Test the Yara rule with Loki, does it flag file 2? (Yay/Nay)

Answer: Yay

9.5 What is the name of the variable for the string that it matched on? (Question Hint Look at $x1)

Checked the contents of file2.yar to identify the specific string that was flagged by your YARA rule.

<img width="679" height="244" alt="Screenshot 2025-09-06 at 8 24 32 PM" src="https://github.com/user-attachments/assets/6216a0fe-df7d-4ea4-8c04-abb8455dbbd4" />
The actual content of $x1 is the string that YARA matched.

<img width="681" height="582" alt="Screenshot 2025-09-06 at 8 24 43 PM" src="https://github.com/user-attachments/assets/7f80c136-eae9-44d8-8648-104b454d2ae2" />
This means the rule flagged file2 because it detected the presence of the Zepto.js function, which is often associated with certain web shell scripts or JavaScript-based exploits.

Answer: Zepto

9.6 Inspect the Yara rule, how many strings were generated?

<img width="672" height="575" alt="Screenshot 2025-09-06 at 8 24 56 PM" src="https://github.com/user-attachments/assets/67531f29-6190-4939-8319-cdfb922cf628" />
Number of strings in the Yara rule are 20

Answer: 20

9.7 One of the conditions to match on the Yara rule specifies file size. The file has to be less than what amount?

<img width="686" height="564" alt="Screenshot 2025-09-06 at 8 25 08 PM" src="https://github.com/user-attachments/assets/3eaa71e6-f84b-4eef-bc03-4ab6966296ea" />
The condition states that the file must be smaller than 700KB for the rule to trigger.

Answer: 700KB

Task 10 Valhalla
Valhalla
Valhalla is an online Yara feed created and hosted by Nextron-Systems (erm, Florian Roth). By now, you should be aware of the ridiculous amount of time and energy Florian has dedicated to creating these tools for the community. Maybe we should have just called this the Florian Roth room. (lol)

Per the website, “Valhalla boosts your detection capabilities with the power of thousands of hand-crafted high-quality YARA rules.”

<img width="673" height="301" alt="Screenshot 2025-09-06 at 8 25 20 PM" src="https://github.com/user-attachments/assets/4054cb77-c138-4829-b76a-76a791417cdc" />
From the image above, we should denote that we can conduct searches based on a keyword, tag, ATT&CK technique, sha256, or rule name.

Note: For more information on ATT&CK, please visit the MITRE room.

<img width="684" height="166" alt="Screenshot 2025-09-06 at 8 25 28 PM" src="https://github.com/user-attachments/assets/11360c96-f2ab-40f4-a6c4-1ede8873b3a3" />
Taking a look at the data provided to us, let’s examine the rule in the screenshot below:

<img width="674" height="132" alt="Screenshot 2025-09-06 at 8 25 38 PM" src="https://github.com/user-attachments/assets/86d195c4-6a04-4cc9-9e2b-15e57e0f14a8" />
We are provided with the name of the rule, a brief description, a reference link for more information about the rule, along with the rule date.

Feel free to look at some rules to become familiar with the usefulness of Valhalla. The best way to learn the product is by just jumping right in.

Picking up from our scenario, at this point, you know that the 2 files are related. Even though Loki classified the files are suspicious, you know in your gut that they are malicious. Hence the reason you created a Yara rule using yarGen to detect it on other web servers. But let’s further pretend that you are not code-savvy (FYI — not all security professionals know how to code/script or read it). You need to conduct further research regarding these files to receive approval to eradicate these files from the network.

Time to use Valhalla for some threat intelligence gathering…

Answer the questions below

10.1 Enter the SHA256 hash of file 1 into Valhalla. Is this file attributed to an APT group? (Yay/Nay)


<img width="685" height="233" alt="Screenshot 2025-09-06 at 8 25 46 PM" src="https://github.com/user-attachments/assets/c2ad19d9-4e23-4b28-a68d-7d0d73de7826" />
Go to https://valhalla.nextron-systems.com/ and paste the hash

<img width="688" height="638" alt="Screenshot 2025-09-06 at 8 25 56 PM" src="https://github.com/user-attachments/assets/c453c1c3-1fff-41c9-b31e-3e5a4288c388" />

<img width="821" height="692" alt="Screenshot 2025-09-06 at 10 16 25 PM" src="https://github.com/user-attachments/assets/0d397a15-1e0d-4a5a-a144-e8c59cd1f6d3" />


Results

The file was detected by several YARA rules.

One rule, “Webshell_b374k_Jan18_1”, has a description that says:

“Detects hacktool / webshell I found in disclosed toolset of Chinese APT group.”

This means the file was found in a hacking toolset used by a Chinese APT group.

Answer: Yay

10.2 Do the same for file 2. What is the name of the first Yara rule to detect file 2?

<img width="730" height="282" alt="Screenshot 2025-09-06 at 10 16 33 PM" src="https://github.com/user-attachments/assets/72955f82-5dcd-4ebd-8167-b8ee9fd970a7" />
Go to https://valhalla.nextron-systems.com/ and paste the hash

<img width="705" height="707" alt="Screenshot 2025-09-06 at 10 16 41 PM" src="https://github.com/user-attachments/assets/4c349022-42ae-4bc6-9588-98a05d3befe4" />

<img width="694" height="399" alt="Screenshot 2025-09-06 at 10 16 48 PM" src="https://github.com/user-attachments/assets/d41c8a9d-e8ba-490e-a62b-6e0dd9d61c95" />
Results

The file was detected 4 YARA rules.

The first YARA rule that detected File 2, based on the oldest date (2015–10–16) in the results.

Answer: Webshell_b374k_rule1

10.3 Examine the information for file 2 from Virus Total (VT). The Yara Signature Match is from what scanner? (Question Hint This information is on the Community tab of the VirusTotal page, and not on the Detection tab)

<img width="681" height="314" alt="Screenshot 2025-09-06 at 10 16 57 PM" src="https://github.com/user-attachments/assets/fb5735fe-b60e-4df3-bad1-79416467e933" />

From the Community tab in VirusTotal, the YARA Signature Match is attributed to:

This means the THOR APT Scanner identified the file as suspicious based on its YARA rules.

Answer: THOR APT Scanner

10.4 Enter the SHA256 hash of file 2 into Virus Total. Did every AV detect this as malicious? (Yay/Nay)

<img width="677" height="373" alt="Screenshot 2025-09-06 at 10 17 04 PM" src="https://github.com/user-attachments/assets/8dc433df-1f6c-41c2-900f-fae725ec5368" />

Answer: Nay

10.5 Besides .PHP, what other extension is recorded for this file? (Question Hint Look under the “details” tab in Virustotal to find out the extensions for this submission)


<img width="626" height="717" alt="Screenshot 2025-09-06 at 10 17 15 PM" src="https://github.com/user-attachments/assets/0326fd4c-f1c1-457f-a5a8-3fc2ebb09878" />

The file list shows multiple extensions, including .PHP, .APK, .TXT, .CSV, .SYS, .HTML, and .EXE.

.APK (Android application) — Android application package
.CSV (Comma-separated values file) — A data storage format
.SYS (System file) — A system file used by Windows
.TXT (Text file) — A plain text file
.HTML (Web page file) — A web page file
.EXE (Executable file) — A Windows executable

.EXE is important because it indicates that the same malware might also be distributed as an executable for Windows systems.
This means the threat isn’t just limited to web-based attacks (PHP files on web servers) but could also be used for Windows-based infections.

Answer: .EXE

10.6 What JavaScript library is used by file 2? (Question Hint Go to the Github page and search inside the index.php file)

Go to the Github pag: https://github.com/b374k/b374k

<img width="678" height="140" alt="Screenshot 2025-09-06 at 10 17 23 PM" src="https://github.com/user-attachments/assets/a72fab98-a792-44bf-b8c6-3201d564826f" />
The requirements section clearly states that zepto.js v1.1.2 is needed for the b374k shell to function properly.
It also mentions that a modern browser is required to support Zepto.js.
The link to the official Zepto.js website further confirms its usage in the script.
Also

Inside the index.php file

<img width="681" height="232" alt="Screenshot 2025-09-06 at 10 17 30 PM" src="https://github.com/user-attachments/assets/8b14191e-f3a5-4b6c-ac13-e7ebe816aab5" />

Line 27: The script loads zepto.js using:

$zepto_code = packer_read_file($GLOBALS[‘packer’][‘base_dir’].”zepto.js”);

This means that zepto.js is being read and used in the script.

Line 34–35: The script dynamically sets a theme using cookies, which suggests that Zepto.js is likely involved in UI interactions.

Line 30–31: Other JavaScript files (sortable.js, base.js, main.js) are also included, but Zepto.js is explicitly mentioned.

It confirms that Zepto.js is being used in file 2

Answer: Zepto

10.7 Is this Yara rule in the default Yara file Loki uses to detect these type of hack tools? (Yay/Nay) (Question Hint Examine thor-webshell.yar and search for the rule name)

The default Loki rules are stored in /home/cmnatic/tools/Loki/signature-base/yara/

We need to search for the rule in Loki’s YARA rule repository

<img width="711" height="163" alt="Screenshot 2025-09-06 at 10 17 38 PM" src="https://github.com/user-attachments/assets/c3a1a2bb-64fa-4366-bf36-a8724d00d1d7" />

Since the command returned no output, this means that the rule is not present in Loki’s default YARA rules.

Answer: Nay

Task 11 Conclusion
In this room, we explored Yara, how to use Yara, and manually created basic Yara rules. We also explored various open-source tools to hit the ground running that utilizes Yara rules to detect evil on endpoints.

By going through the room scenario, you should understand the need (as a blue teamer) to know how to create Yara rules effectively if we rely on such tools. Commercial products, even though not perfect, will have a much richer Yara ruleset than an open-source product. Both commercial and open-source will allow you to add Yara rules to expand its capabilities further to detect threats.

If it is not clear, the reason why file 2 was not detected is that the Yara rule was not in the Yara file used by Loki to detect the hack tool (web shell) even though its the hack tool has been around for years and has even been attributed to at least 1 nation-state. The Yara rule is present in the commercial variant of Loki, which is Thor.

There is more that can be done with Yara and Yara rules. We encourage you to explore this tool further at your own leisure.

Answer the questions below

No answer needed.
