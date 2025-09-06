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

