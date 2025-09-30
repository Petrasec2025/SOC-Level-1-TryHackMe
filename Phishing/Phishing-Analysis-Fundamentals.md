<img width="1419" height="305" alt="Screenshot 2025-09-30 at 4 42 29 PM" src="https://github.com/user-attachments/assets/01c1169a-d975-40c1-9b3f-0c92033670e9" />

Task 1 Introduction
Spam and Phishing are common social engineering attacks. In social engineering, phishing attack vectors can be a phone call, a text message, or an email. As you should have already guessed, our focus is on email as the attack vector.

We all should be somewhat familiar with what spam is. No matter what, these emails somehow find their way into our inboxes.

The first email classified as spam dates back to 1978, and it’s still thriving today.

Phishing is a serious attack vector that you, as a defender, will have to defend against.

An organization can follow all the recommended guidelines when it comes to building a layered defense strategy. Still, all it takes is an inexperienced and unsuspecting user within your corporate environment to click on a link or download and run a malicious attachment which may provide an attacker a foothold into the network.

Many products help combat spam and phishing, but realistically these emails still can get through. When they do, as a Security Analyst, you need to know how to analyze these emails to determine if they’re malicious or benign.

Furthermore, you will need to gather information about the email to update your security products to prevent malicious emails from making their way back into a user’s inbox.

In this room, we’ll look at all the components involved with sending emails across the Internet and how to analyze email headers.

Deploy the machine attached to this task; it will be visible in the split-screen view once it is ready.

If you don’t see a virtual machine load, then click the Show Split View button.
<img width="685" height="63" alt="Screenshot 2025-09-30 at 4 46 45 PM" src="https://github.com/user-attachments/assets/57f5fbcc-b48a-4067-904c-23da6a269c21" />
Answer the questions below

Read the above and launch the attached VM.

Task 2 The Email Address
It’s only appropriate to start this room by mentioning the man who invented the concept of emails and made the @ symbol famous. The person responsible for the contribution to the way we communicate was Ray Tomlinson.

The invention of the email dates back to the 1970s for ARPANET. Yep, probably before you were born. Definitely, before I was born. :)

So, what makes up an email address?

User Mailbox (or Username)
@
Domain
Let’s look at the following email address, billy@johndoe.com.

The user mailbox is billy
@ (thanks Ray)
The domain is johndoe.com
To simplify this even further, think about the street on which you live on.

You can think of your street as the domain.
The recipient’s first/last name, along with the house number in this scenario, represents the user mailbox.
With this information, the postal worker delivering the mail knows into which mailbox to put the letter(s).

Next, let’s look at the network protocols used to send an email from the sender to the recipient.

Answer the questions below

2. Email dates back to what time frame?


Answer: 1970s

Task 3 Email Delivery
A handful of protocols are involved with the “magic” that takes place when you hit SEND in an email client.

By now, you should already know that certain protocols were created to handle specific network-related tasks, such as email.

There are 3 specific protocols involved to facilitate the outgoing and incoming email messages, and they are briefly listed below.

SMTP (Simple Mail Transfer Protocol) — It is utilized to handle the sending of emails.
POP3 (Post Office Protocol) — Is responsible transferring email between a client and a mail server.
IMAP (Internet Message Access Protocol) — Is responsible transferring email between a client and a mail server.
You should have noticed that both POP3 and IMAP have the same definition. But there are differences between the two.

The difference between the two is listed below: (credit AOL — You got mail!)

POP3

Emails are downloaded and stored on a single device.
Sent messages are stored on the single device from which the email was sent.
Emails can only be accessed from the single device the emails were downloaded to.
If you want to keep messages on the server, make sure the setting “Keep email on server” is enabled, or all messages are deleted from the server once downloaded to the single device’s app or software.
IMAP

Emails are stored on the server and can be downloaded to multiple devices.
Sent messages are stored on the server.
Messages can be synced and accessed across multiple devices.
<img width="681" height="459" alt="Screenshot 2025-09-30 at 4 46 58 PM" src="https://github.com/user-attachments/assets/44c03a07-6c2e-4aee-94dd-d0b24ac55f23" />
Below is an explanation of each numbered point from the above diagram:

Alexa composes an email to Billy (billy@johndoe.com) in her favorite email client. After she's done, she hits the send button.
The SMTP server needs to determine where to send Alexa’s email. It queries DNS for information associated with johndoe.com.
The DNS server obtains the information johndoe.com and sends that information to the SMTP server.
The SMTP server sends Alexa’s email across the Internet to Billy’s mailbox at johndoe.com.
In this stage, Alexa’s email passes through various SMTP servers and is finally relayed to the destination SMTP server.
Alexa’s email finally reached the destination SMTP server.
Alexa’s email is forwarded and is now sitting in the local POP3/IMAP server waiting for Billy.
Billy logs into his email client, which queries the local POP3/IMAP server for new emails in his mailbox.
Alexa’s email is copied (IMAP) or downloaded (POP3) to Billy’s email client.
Lastly, each protocol has its associated default ports and recommended ports. For example, SMTP is port 25.

Read the following article to understand the difference between each here.

Answer the questions below

3.1 What port is classified as Secure Transport for SMTP?

Port 465 is the designated port for Secure SMTP (Simple Mail Transfer Protocol) using SSL/TLS encryption.

SMTP handles the sending of emails, and port 465 ensures secure communication between email clients and servers using SSL/TLS.

Answer: 465

3.2 What port is classified as Secure Transport for IMAP?

Port 993 is the designated port for Secure IMAP (Internet Message Access Protocol) over SSL/TLS.

IMAP is used for retrieving and managing emails stored on a server. Port 993 provides encrypted access to the email server, ensuring confidentiality.

Answer: 993

3.3 What port is classified as Secure Transport for POP3?

Port 995 is the designated port for Secure POP3 (Post Office Protocol) using SSL/TLS.

POP3 is used for downloading emails from a server to a client. Port 995 ensures the connection is secure and encrypted.

Answer: 995

Task 4 Email Headers
Great! We know how an email travels from point A to point B and all the protocols involved in the process.

This task is to understand the components of what makes up an email message when it arrives in an inbox.

This understanding is necessary if you wish to analyze potentially malicious emails manually.

Before we begin, we need to understand that there are two parts to an email:

the email header (information about the email, such as the email servers that relayed the email)
the email body (text and/or HTML formatted text)
The syntax for email messages is known as the Internet Message Format (IMF).

Let’s look at email headers first.

What do you look for when analyzing a potentially malicious email?

Let’s start with the following email header fields:

From — the sender’s email address
Subject — the email’s subject line
Date — the date when the email was sent
To — the recipient’s email address
This is usually clearly visible in any email client. Let’s look at an example of these fields in the below image.

Warning: This is a snippet from an actual email. The email in the below image is from a honeypot Yahoo email address. Don’t engage/interact with the email addresses or IP addresses revealed in this room.

Press enter or click to view image in full size
<img width="679" height="92" alt="Screenshot 2025-09-30 at 4 47 12 PM" src="https://github.com/user-attachments/assets/997f2088-c847-4f98-96e3-a68b96dd454d" />
Note: The numbers in the above image correspond to the email header fields bullet list above.

Another method to obtain the same email header information, and more, is by viewing the ‘raw’ email details.

When looking at an email header in detail, it can be intimidating at first, but it’s not so bad if you know what to look for.

Note: Depending on your email client, whether a web client or a desktop app, the steps to view these email header fields will vary, but the concept is the same.

Review this Knowledge Base (KB) article from Media Temple on viewing the raw/full email headers in various email clients here.

In the below image, you can see how to view this information within Yahoo.

<img width="565" height="260" alt="Screenshot 2025-09-30 at 4 47 20 PM" src="https://github.com/user-attachments/assets/445ebaf5-217d-4722-a2d3-961c763d4039" />
Below is a snippet of the raw message for the email sample.
<img width="685" height="568" alt="Screenshot 2025-09-30 at 4 47 30 PM" src="https://github.com/user-attachments/assets/4089dec8-ba65-4687-b428-4e11d580615c" />

Note: The above image shows some, not all, of the information within an email’s header.

You can review this email in the Email Samples directory on the Desktop within the attached virtual machine. The email is titled email1.eml.

From the above image, there are other email header fields of interest.

X-Originating-IP — The IP address of the email was sent from (this is known as an X-header)
Smtp.mailfrom/header.from — The domain the email was sent from (these headers are within Authentication-Results)
Reply-To — This is the email address a reply email will be sent to instead of the From email address
To clarify, in the email in the sample above, the Sender is newsletters@ant.anki-tech.com, but if a recipient replies to the email, the response will go to reply@ant.anki-tech.com, which is the Reply-To, and NOT to newsletters@ant.anki-tech.com.

Below is an additional resource from Media Template on how to analyze email headers:

https://web.archive.org/web/20221219232959/https://mediatemple.net/community/products/all/204643950/understanding-an-email-header
Note: The questions below are based on the Media Template article.

Answer the questions below

4.1 What email header is the same as “Reply-to”?

The email header that corresponds to “Reply-To” is Return-Path.
<img width="666" height="441" alt="Screenshot 2025-09-30 at 4 47 45 PM" src="https://github.com/user-attachments/assets/89ace6d3-ef5f-4ea9-af51-78bd96a58dfe" />


Now let’s talk about how email travels from the sender to the recipient.

To best illustrate this, see the oversimplified image below:
The Return-Path header indicates where non-delivery notifications (bounces) or replies should be sent, and it often serves the same function as the Reply-To field in certain scenarios.

Answer: Return-Path

4.2 Once you find the email sender’s IP address, where can you retrieve more information about the IP?
<img width="613" height="173" alt="Screenshot 2025-09-30 at 4 47 55 PM" src="https://github.com/user-attachments/assets/56a8632d-ab76-47d3-bbfd-a54da1138779" />
The American Registry for Internet Numbers (ARIN) is a trusted source for retrieving detailed information about IP addresses, such as ownership, geographical region, and associated organization.

In addition to ARIN, the following tools can also be used for further analysis of the IP address:

Whois Lookup Services: Provides ownership details, geolocation, and ISP information.

Example: https://whois.domaintools.com

IP Geolocation Tools: Determines the physical location associated with the IP address.

Example: https://iplocation.net

Blacklist Checkers: Checks if the IP is listed in spam or malicious activity databases.

Example: https://mxtoolbox.com/blacklists.aspx

Online Abuse Reporting Databases: Verifies if the IP has been reported for malicious or suspicious activity.

Example: https://abuseipdb.com

Answer: http://www.arin.net

Task 5 Email Body
The email body is the part of the email which contains the text (plain or HTML formatted) the sender wants you to view.

Below is an example of a text-only email.
<img width="613" height="173" alt="Screenshot 2025-09-30 at 4 47 55 PM" src="https://github.com/user-attachments/assets/bd441897-53e6-47bc-8284-2838fd3efd4a" />

Below is an example of the HTML formatted email.
<img width="680" height="283" alt="Screenshot 2025-09-30 at 4 48 01 PM" src="https://github.com/user-attachments/assets/578b1373-0605-4920-a2ba-b386677b76af" />

The above email contains an image (which was blocked by the email client) and embedded hyperlinks.

HTML is what makes it possible to add these elements to an email.

To view an email’s HTML code is the same approach shown below, but it may vary depending on the webmail client.

In the example below, the screenshot is from Protonmail.
<img width="388" height="319" alt="Screenshot 2025-09-30 at 4 48 07 PM" src="https://github.com/user-attachments/assets/1a81eb8f-bfa9-464f-b9e5-a72b780c01a0" />
A snippet of the HTML code is shown below.
<img width="676" height="444" alt="Screenshot 2025-09-30 at 4 48 13 PM" src="https://github.com/user-attachments/assets/bfed9316-df7d-49a3-8b7b-7c549ba8537d" />
In this specific email web client, Protonmail, the option to switch back to HTML is called “View rendered HTML”.
<img width="585" height="268" alt="Screenshot 2025-09-30 at 4 48 18 PM" src="https://github.com/user-attachments/assets/30439ae3-2255-47d0-85f3-dd93722bedf5" />
Again, it will be different for other webmail clients.

Lastly, emails may contain attachments. The same premise applies; you can view an email’s attachment from an email’s HTML format or by viewing the source code.

Let’s look at a few examples below.

The following example is an HTML formatted email from “Netflix” with an attachment. The web client is Yahoo!
<img width="685" height="325" alt="Screenshot 2025-09-30 at 4 48 26 PM" src="https://github.com/user-attachments/assets/57241a84-7ead-43e9-be84-47a5b4f28845" />
The email body has an image.
The email attachment is a PDF document.
Now let’s view this attachment within the source code.
<img width="579" height="257" alt="Screenshot 2025-09-30 at 4 48 33 PM" src="https://github.com/user-attachments/assets/edf413ce-afa3-428c-85d3-eba5516a9e7f" />
From the above example, we can see the headers associated with this attachment:

Content-Type is application/pdf.
Content-Disposition specifies it’s an attachment.
Content-Transfer-Encoding tells us it’s base64 encoded.
With the base64 encoded data, you can decode it and save it to your machine.

Warning: When interacting with attachments, proceed with caution and make sure you don’t double-click an email’s attachment by accident.

Note: Headers specific to ‘content’ can be found in various locations within an email message source code, and they’re not only associated with attachments. For example, Content-Type can be text/html, and Content-Transfer-Encoding can have other values, such as 8bit.

Answer the questions below

5.1 In the above screenshots, what is the URI of the blocked image?

This can be seen in the src attribute of the <img> tag in the provided HTML source code.
<img width="679" height="449" alt="Screenshot 2025-09-30 at 4 48 41 PM" src="https://github.com/user-attachments/assets/588a1e4c-63fa-4667-8960-3d27107b1db3" />
Answer:https://i.imgur.com/LSWdDTi.png

5.2 In the above screenshots, what is the name of the PDF attachment?

We can see it in the Content-Disposition header as filename=”Payment-updateid.pdf.
<img width="572" height="261" alt="Screenshot 2025-09-30 at 4 48 49 PM" src="https://github.com/user-attachments/assets/98bb41c2-c0c8-493e-af0b-f79bea4a88c7" />
Answer: Payment-updateid.pdf

5.3 In the attached virtual machine, view the information in email2.txt and reconstruct the PDF using the base64 data. What is the text within the PDF? (Question Hint This can be done using the Terminal or CyberChef)
<img width="631" height="705" alt="Screenshot 2025-09-30 at 4 48 59 PM" src="https://github.com/user-attachments/assets/5a87adac-7948-48b9-a202-6434d1cef352" />
<img width="675" height="713" alt="Screenshot 2025-09-30 at 4 49 15 PM" src="https://github.com/user-attachments/assets/6290c559-4452-469f-8cc7-01df5d95aef0" />
First Listed the contents of the home directory using the ls command.

Navigated into the Desktop directory using the cd (change directory) command.

Listed the contents of the Desktop directory using the ls command again.

Navigated into the Email Samples directory using the cd command, escaping the space in the directory name with a backslash (\).

Listed the contents of the Email Samples directory, where files like email1.eml, email2.txt, and email3.eml are present.
<img width="679" height="141" alt="Screenshot 2025-09-30 at 4 49 29 PM" src="https://github.com/user-attachments/assets/8b1c92ab-d9c0-48e6-aca8-f23a01a658fa" />
<img width="685" height="159" alt="Screenshot 2025-09-30 at 4 49 36 PM" src="https://github.com/user-attachments/assets/0dbb5458-d3e6-46b6-88a2-32dbb498fda4" />
Crate new file testemail.txt and Save only the Base64 content.
<img width="687" height="330" alt="Screenshot 2025-09-30 at 4 49 47 PM" src="https://github.com/user-attachments/assets/566a6fe8-df5b-43e2-b469-110c3dd58d30" />
Go back to the terminal and Listethe files in the directory
<img width="807" height="357" alt="Screenshot 2025-09-30 at 4 50 18 PM" src="https://github.com/user-attachments/assets/fe738129-f41d-428c-8680-d45f34291c85" />
cat email2.txt: Reads the content of the email2.txt file.

| base64 -d: Decodes the Base64-encoded content of email2.txt.

testemail.txt > testemail.pdf: The decoded content is saved as a file named testemail.pdf.
<img width="683" height="340" alt="Screenshot 2025-09-30 at 4 50 36 PM" src="https://github.com/user-attachments/assets/da0a16e5-6a2b-4b1b-9393-ba2013d758ad" />

Go Back to the Email Samples Folder and open testemail.pdf
<img width="642" height="519" alt="Screenshot 2025-09-30 at 4 50 43 PM" src="https://github.com/user-attachments/assets/869c9e72-a314-41d4-a86c-213b5e6177aa" />

We can see the flag
<img width="679" height="219" alt="Screenshot 2025-09-30 at 4 50 52 PM" src="https://github.com/user-attachments/assets/f890961b-1b92-490f-95fc-623774e135a4" />
Answer: THM{BENIGN_PDF_ATTACHMENT}

Task 6 Types of Phishing
Now that we covered the general concepts regarding emails and how they travel from sender to recipient, we can now talk about how this method of communication is used for nefarious purposes.

Different types of malicious emails can be classified as one of the following:

Spam — unsolicited junk emails sent out in bulk to a large number of recipients. The more malicious variant of Spam is known as MalSpam.
Phishing — emails sent to a target(s) purporting to be from a trusted entity to lure individuals into providing sensitive information.
Spear phishing — takes phishing a step further by targeting a specific individual(s) or organization seeking sensitive information.
Whaling — is similar to spear phishing, but it’s targeted specifically to C-Level high-position individuals (CEO, CFO, etc.), and the objective is the same.
Smishing — takes phishing to mobile devices by targeting mobile users with specially crafted text messages.
Vishing — is similar to smishing, but instead of using text messages for the social engineering attack, the attacks are based on voice calls.
When it comes to phishing, the modus operandi is usually the same depending on the objective of the email.

For example, the objective can be to harvest credentials, and another is to gain access to the computer.

Below are typical characteristics phishing emails have in common:

The sender email name/address will masquerade as a trusted entity (email spoofing)
The email subject line and/or body (text) is written with a sense of urgency or uses certain keywords such as Invoice, Suspended, etc.
The email body (HTML) is designed to match a trusting entity (such as Amazon)
The email body (HTML) is poorly formatted or written (contrary from the previous point)
The email body uses generic content, such as Dear Sir/Madam.
Hyperlinks (oftentimes uses URL shortening services to hide its true origin)
A malicious attachment posing as a legitimate document
We’ll look at each of these techniques (characteristics) in greater detail in the next room within the Phishing module.

Reminder: When dealing with hyperlinks and attachments, you need to be careful not to accidentally click on the hyperlink or the attachment.

Hyperlinks and IP addresses should be ‘defanged’. Defanging is a way of making the URL/domain or email address unclickable to avoid accidental clicks, which may result in a serious security breach. It replaces special characters, like “@” in the email or “.” in the URL, with different characters. For example, a highly suspicious domain, http://www.suspiciousdomain.com, will be changed to hxxp[://]www[.]suspiciousdomain[.]com before forwarding it to the SOC team for detection.

Analyze the email titled email3.eml within the virtual machine and answer the questions below.
<img width="667" height="715" alt="Screenshot 2025-09-30 at 4 51 02 PM" src="https://github.com/user-attachments/assets/c581af35-3e7d-4a1d-8c0e-a48075fc5e28" />

Note: Alexa is the victim, and Billy is the analyst assigned to the case. Alexa forwarded the email to Billy for analysis.

Answer the questions below

6.1 What trusted entity is this email masquerading as?

The From: field in the email header is:
<img width="690" height="467" alt="Screenshot 2025-09-30 at 4 51 13 PM" src="https://github.com/user-attachments/assets/4dd22bb9-5196-49f2-84e0-11ae6fe6464d" />
<img width="685" height="82" alt="Screenshot 2025-09-30 at 4 51 21 PM" src="https://github.com/user-attachments/assets/c6325f86-c869-4c41-b838-31d651f12125" />
The part between =?UTF-8?B? and ?= is the Base64 encoded text
<img width="666" height="70" alt="Screenshot 2025-09-30 at 4 51 28 PM" src="https://github.com/user-attachments/assets/65c4019b-cb54-4df4-b123-53d7519b2f84" />
Using CyberChef to encode from Base64
<img width="683" height="327" alt="Screenshot 2025-09-30 at 4 51 34 PM" src="https://github.com/user-attachments/assets/dd4996b8-89f4-4093-98f5-956b222cdc1e" />
Or Use thunderbird

Thunderbird is a free, open-source, cross-platform email client . It is widely used for managing emails, news feeds (RSS), and other forms of communication in a secure and user-friendly environment.
<img width="685" height="293" alt="Screenshot 2025-09-30 at 4 51 43 PM" src="https://github.com/user-attachments/assets/b305f8c9-9a89-4391-83c1-bba57013516f" />
Thunderbird we’ll open the the email and we can analyze it
<img width="684" height="295" alt="Screenshot 2025-09-30 at 4 51 51 PM" src="https://github.com/user-attachments/assets/e9e4c066-7883-46e0-a35f-de3ee60d2855" />
Or
<img width="687" height="221" alt="Screenshot 2025-09-30 at 4 52 01 PM" src="https://github.com/user-attachments/assets/b9a01e2b-1364-42dc-af92-0f849b58cab0" />
Answer: Home Depot

6.2 What is the sender’s email?
<img width="684" height="570" alt="Screenshot 2025-09-30 at 4 52 10 PM" src="https://github.com/user-attachments/assets/13f5e9f5-964f-4f63-9288-67ee439ed5d6" />
Answer: support@teckbe.com

6.3 What is the subject line?

Press enter or click to view image in full size
<img width="668" height="532" alt="Screenshot 2025-09-30 at 4 52 20 PM" src="https://github.com/user-attachments/assets/f6d5a813-120f-4765-b06d-69c86e4cecad" />
<img width="671" height="72" alt="Screenshot 2025-09-30 at 4 52 26 PM" src="https://github.com/user-attachments/assets/738d0635-4f0a-4a41-aa70-60a3af628536" />

=?UTF-8?B?…?=:

UTF-8 indicates the encoding format.

B (Base64) indicates the text is Base64 encoded.
<img width="726" height="218" alt="Screenshot 2025-09-30 at 4 52 33 PM" src="https://github.com/user-attachments/assets/cf31de37-5473-4dc5-b724-a5f06a196c67" />
Or Using CyberChef
<img width="686" height="341" alt="Screenshot 2025-09-30 at 4 52 40 PM" src="https://github.com/user-attachments/assets/8b7a7e23-c419-4344-a80b-1805378112ac" />
Answer: Order Placed: Your Order ID OD2321657089291 Placed Successfully

6.4 What is the URL link for — CLICK HERE? (Enter the defanged URL) (Question Hint There are repeat characters that you can remove from the URL. CyberChef can help you with this, along with defanging)

Press enter or click to view image in full size
<img width="688" height="520" alt="Screenshot 2025-09-30 at 4 52 49 PM" src="https://github.com/user-attachments/assets/54b7ffd6-575e-425c-8f9a-6ac04f721bfa" />
<img width="672" height="78" alt="Screenshot 2025-09-30 at 4 52 56 PM" src="https://github.com/user-attachments/assets/b9e84d9f-1756-4149-9cd2-b3bdbf5e3793" />

Clean up and remove duplicate/invalid characters: URLs can contain repeated or extra characters added by encoding processes (== at the end or unnecessary line breaks)

Use CyberChef

Press enter or click to view image in full size
<img width="697" height="417" alt="Screenshot 2025-09-30 at 4 53 03 PM" src="https://github.com/user-attachments/assets/ed7a5cef-d16d-4cb1-a03e-0a247fb6b28a" />
<img width="668" height="67" alt="Screenshot 2025-09-30 at 5 11 59 PM" src="https://github.com/user-attachments/assets/4bff22da-4469-4b5f-86dd-7f8df20cc686" />
Answer: hxxp[://]t[.]teckbe[.]com/p/?j3=EOowFcEwFHl6EOAyFcoUFVTVEchwFHlUFOo6lVTTDcATE7oUE7AUET

Task 7 Conclusion
Before ending this room, you should know what BEC (Business Email Compromise) means.

A BEC is when an adversary gains control of an internal employee’s account and then uses the compromised email account to convince other internal employees to perform unauthorized or fraudulent actions.

Tip: You should be familiar with this term. I have heard this question asked before in a job interview.

Within this room, we covered the following:

What makes up an email address?
How an email travels from sender to recipient.
How to view the source code of an email header.
How to view the source code of an email body.
Understand the pertinent information we should obtain from an email we’re analyzing.
Some common techniques attackers use in spam and phishing email campaigns.
In the upcoming Phishing Analysis series, we’ll look at samples of various common techniques used in phishing email campaigns, along with tools to assist us with analyzing an email header and email body.

Next room in this module: Phishing Emails 2

7. Answer the questions below

What is BEC?

Answer: Business Email Compromise
<img width="681" height="415" alt="Screenshot 2025-09-30 at 4 53 11 PM" src="https://github.com/user-attachments/assets/f4850261-fdaf-43d9-bad5-788abcbf21ad" />


