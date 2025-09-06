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




