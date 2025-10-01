<img width="1418" height="300" alt="Screenshot 2025-10-01 at 11 00 57 AM" src="https://github.com/user-attachments/assets/84e53617-091a-4f5c-b6a2-639d0d4dcada" />
Learn how to defend against phishing emails.
Room Link: https://tryhackme.com/room/phishingemails4gkxh
Task 1: Introduction
In this task, we will be discussing various actions that a defender can take to protect users from falling victim to malicious emails. Some of the key actions include:

Email Security (SPF, DKIM, DMARC): Implementing these email authentication protocols can help verify the legitimacy of incoming emails, reducing the risk of phishing attacks.
SPAM Filters: These filters flag or block incoming emails based on their reputation, helping to prevent potentially harmful messages from reaching the inbox.
Email Labels: Alerting users when an incoming email is from an outside source can raise awareness about potential risks associated with external emails.
Email Address/Domain/URL Blocking: By blocking email addresses, domains, or URLs with a poor reputation or those on explicit denylists, defenders can prevent known sources of malicious emails from reaching users.
Attachment Blocking: Blocking email attachments based on their file extensions can prevent the spread of malicious files through email.
Attachment Sandboxing: Detonating email attachments in a sandbox environment helps detect and isolate potentially malicious activities, protecting users from harmful content.
Security Awareness Training: Conducting internal phishing campaigns as part of security awareness training helps educate users about the dangers of phishing and how to recognize phishing attempts.
In this room, our focus will be on the Email Security aspect, specifically covering SPF, DKIM, and DMARC, which are essential components of email authentication and security. These measures aim to enhance the overall security posture against phishing attacks and ensure that legitimate emails can be trusted. For further details and specific mitigation techniques, refer to the MITRE ATT&CK Framework’s Software Configuration section via the provided link.

Questions
Question No 1: After visiting the link in the task, what is the MITRE ID for the “Software Configuration” mitigation technique?

Hint: Visit the link.

Answer: M1054

Press enter or click to view image in full size
<img width="1322" height="103" alt="Screenshot 2025-10-01 at 11 01 48 AM" src="https://github.com/user-attachments/assets/436aa5d0-99e9-4925-b199-01d5b4a697ae" />
Task 2: SPF (Sender Policy Framework)
In this task, we are discussing Sender Policy Framework (SPF), an essential email authentication method used to verify the legitimacy of email senders. SPF enables Internet Service Providers (ISPs) to confirm whether a mail server is authorized to send emails on behalf of a specific domain. SPF records are stored as DNS TXT records and contain a list of permitted IP addresses and domains for sending email on behalf of the domain. A basic SPF record includes elements like

“v=spf1” to initiate the record
“ip4” to specify allowed IPv4 addresses
“include” to reference authorized domains
“-all” to reject unauthorized emails.
Tools like dmarcian’s SPF Surveyor can be used for SPF record analysis, and organizations can create their own SPF records following specific syntax guidelines. The SPF record status, such as “softfail,” can provide insights into the email’s legitimacy. Various companies utilize SPF checks to enhance email security.

Questions
Question No 1: Referencing the dmarcian SPF syntax table, what prefix character can be added to the “all” mechanism to ensure a “softfail” result
Question No 2: What is the meaning of the -all tag?

Hint: Visit the link provided.

Answer: ~
Answer: fail

Press enter or click to view image in full size
<img width="1282" height="217" alt="Screenshot 2025-10-01 at 11 03 35 AM" src="https://github.com/user-attachments/assets/56b43e90-6447-4877-8d86-2ee635acf95b" />
<img width="1032" height="241" alt="Screenshot 2025-10-01 at 11 04 12 AM" src="https://github.com/user-attachments/assets/aa83dfd4-89ce-41bb-a575-aba614f43851" />
Task 3: DKIM (DomainKeys Identified Mail)
In this task, we are discussing DKIM, which stands for DomainKeys Identified Mail. DKIM is an email authentication method used to verify the authenticity of outgoing emails. It is similar to SPF and is part of DMARC alignment. DKIM records are stored in DNS, and they are slightly more complex than SPF records. The advantage of DKIM is its ability to withstand email forwarding, making it superior to SPF and a fundamental component of email security.

A typical DKIM record includes elements such as

“v=DKIM1” for version,
“k=rsa” to specify the key type (usually RSA), and
“p=” to represent the public key matched with the private key generated during DKIM setup.
Questions
Question No 1: Which email header shows the status of whether DKIM passed or failed?

Hint: Look at the last screen shot in the task.

Answer: Authentication-Results

Press enter or click to view image in full size
<img width="1278" height="333" alt="Screenshot 2025-10-01 at 11 05 29 AM" src="https://github.com/user-attachments/assets/801c3cda-dbe5-4b28-a240-1be3e804e563" />
Task 4: DMARC (Domain-Based Message Authentication, Reporting, and Conformance)
In this task, we are discussing DMARC, which stands for Domain-based Message Authentication Reporting and Conformance. DMARC is an open-source standard that leverages a concept called alignment to combine the results of two other open-source standards, SPF (which defines authorized email servers for a domain) and DKIM (which provides a tamper-evident domain seal for email), with the content of an email. Implementing a DMARC record for your domain, if not already deployed, offers valuable feedback for troubleshooting SPF and DKIM configurations, if necessary.

A basic DMARC record typically looks like this:
v=DMARC1; p=quarantine; rua=postmaster@website.com

Explanation of the record:
- `v=DMARC1`: This tag is mandatory and must be in all caps.
- `p=quarantine`: Specifies the DMARC policy; if a check fails, the email will be sent to the spam folder.
- `rua=postmaster@website.com`: Aggregate reports will be sent to this email address for monitoring.

Additionally, DMARC alignment plays a crucial role in email security.

To check the DMARC status of a domain, tools like the Domain Health Checker from dmarcian.com can be used. In the example provided, Microsoft.com passed all DMARC checks, and it’s possible to delve deeper into DMARC, SPF, or DKIM to obtain more detailed information. In this case, the DMARC configuration is set to reject emails that fail the DMARC check.

Questions:
Question No 1: Which DMARC policy would you use not to accept an email if the message fails the DMARC check?

Hint: add p=

Answer: p=reject
<img width="1263" height="104" alt="Screenshot 2025-10-01 at 11 09 11 AM" src="https://github.com/user-attachments/assets/03776020-3207-436a-be4e-dec57d85dc89" />
Task 5: S/MIME (Secure/Multipurpose Internet Mail Extensions)
In this task, we are discussing S/MIME, which stands for Secure/Multipurpose Internet Mail Extensions. S/MIME is a widely accepted protocol used for sending digitally signed and encrypted messages, ensuring both data integrity and nonrepudiation.

S/MIME primarily relies on two key components:
1. Digital Signatures
2. Encryption

Through Public Key Cryptography, S/MIME operates by utilizing a digital certificate that contains an individual’s public key. Here’s how it works:
- Bob, for instance, obtains a digital certificate containing his public key.
- Bob signs an email message using his private key.
- Mary, the recipient, can decrypt Bob’s message using Bob’s public key.
- When Mary replies to Bob, she sends her certificate to him, allowing Bob to complete the same process on his end.
- Both parties now possess each other’s certificates for future correspondence.

This process ensures the security and authenticity of email communication.

Questions
Question No 1: What is nonrepudiation? (The answer is a full sentence, including the “.”)

Hint: View the provided link.

Answer: The uniqueness of a signature prevents the owner of the signature from disowning the signature.
<img width="1267" height="119" alt="Screenshot 2025-10-01 at 11 11 01 AM" src="https://github.com/user-attachments/assets/a180194c-f38c-4cff-8b63-e15d2c84a62e" />
<img width="670" height="153" alt="Screenshot 2025-10-01 at 11 11 50 AM" src="https://github.com/user-attachments/assets/622ff78c-d13e-4347-9074-5ed5cf84f1ec" />
Task 6: SMTP Status Codes
In this task you are given pcap file with SMTP traffic, you have to analyze that file to answer the questions.

Questions
Question No 1: What Wireshark filter can you use to narrow down the packet output using SMTP status codes?
Question No 2: Per the network traffic, what was the message for status code 220? (Do not include the status code (220) in the answer)
Question No 3: One packet shows a response that an email was blocked using spamhaus.org. What were the packet number and status code? (no spaces in your answer)
Question No 4: Based on the packet from the previous question, what was the message regarding the mailbox?
Question No 5: What is the status code that will typically precede a SMTP DATA command?

Answers: smtp.response.code
Answers: <domain> Service ready
Answers: 156,553
Answers: mailbox name not allowed
Answers: 354

Procedure: For the first question you can do internet serach or read wireshark manual.
For second filter the traffic using “smtp.response.code==220” and check the Simple Mail Transfer protocol heading in the panel below you will get the answer there.
For third question search by string spamhuas.org and smtp packet. You can easily see the frame/packet no and response code
For fourth question expand the response and you can easily find the message.
For fifth question you can simply search it on browser.
<img width="1297" height="543" alt="Screenshot 2025-10-01 at 11 13 08 AM" src="https://github.com/user-attachments/assets/775086bd-5a61-435f-9a36-51b2fb61b98c" />
<img width="676" height="341" alt="Screenshot 2025-10-01 at 11 13 33 AM" src="https://github.com/user-attachments/assets/9fd867a1-4a9d-4725-b19a-a3fd9c689d3e" />
<img width="678" height="213" alt="Screenshot 2025-10-01 at 11 13 41 AM" src="https://github.com/user-attachments/assets/c0ada878-0b63-469c-91fd-a60e110b57b5" />
<img width="684" height="232" alt="Screenshot 2025-10-01 at 11 13 48 AM" src="https://github.com/user-attachments/assets/1386091f-6ccd-4620-8020-1979b31a2ba7" />
Task 7: SMTP Traffic Analysis
In this task is further analysis.

Questions
Question No 1: What port is the SMTP traffic using?
Question No 2: How many packets are specifically SMTP?
Question No 3: What is the source IP address for all the SMTP traffic?
Question No 4: What is the filename of the third file attachment?
Question No 5: How about the last file attachment?

Answer: 25
Answer: 512
Answer: 10.12.19.101
Answer: attachment.scr
Answer: .zip

Procedure: For first question click on any of the SMTP packet and open Transmission Control Protocol drop down menu you can see the port no there.
For second question search the SMTP in filter bar and you can see the stat in bottom right corner it will show how many packet are being displayed.
For third you can search for smtp.response.code it will display to which ip address they are reponding to in other terms there orignal source ip.
For fourth question they have given link in the task for help you can use that.
“The Internet Message Format is format in which text messages are transferred over the Internet. Where SMTP is equivalent to the message envelope, IMF is equivalent to the letter within the envelope. It contains the originator, recipients, subject and dates. Whilst IMF only handles text messages, it can be augmented with MIME_multipart to support multi-media messages.”
So filter packets for imf and select third packet expand expand internet message format in it expand MIME multipart media encapsulation. In it expand encapsulated multi part: application and there you will find the name of the file.
For fifth question follow same steps as fourth.

<img width="687" height="372" alt="Screenshot 2025-10-01 at 11 16 32 AM" src="https://github.com/user-attachments/assets/5c4ce493-2531-4b97-b18b-3930a15c224b" />
<img width="688" height="222" alt="Screenshot 2025-10-01 at 11 16 43 AM" src="https://github.com/user-attachments/assets/e27f3ebe-c288-4106-bfb1-54de6700a8ac" />
<img width="681" height="246" alt="Screenshot 2025-10-01 at 11 16 51 AM" src="https://github.com/user-attachments/assets/b970e5ae-89fa-46a6-8ad8-7fe2d50491a9" />
<img width="681" height="243" alt="Screenshot 2025-10-01 at 11 17 01 AM" src="https://github.com/user-attachments/assets/6f1415e5-d0f0-4c7e-b235-91f4157df4a4" />
<img width="679" height="419" alt="Screenshot 2025-10-01 at 11 17 12 AM" src="https://github.com/user-attachments/assets/df2219cc-6614-4681-a6c7-302c78ad4bc7" />
<img width="680" height="453" alt="Screenshot 2025-10-01 at 11 17 28 AM" src="https://github.com/user-attachments/assets/27fdbc39-4dd6-4fed-8aba-cb215475e7de" />
Task 8: SMTP and C&C Communication
In this task, we are discussing that SMTP can be used by adversaries as C2.
Also add recommended mitigation and detection opportunity.

Questions
Question No 1: Per MITRE ATT&CK, which software is associated with using SMTP and POP3 for C2 communications?

Hint: Visit the provided link.

Answer: Zebrocy
<img width="1258" height="97" alt="Screenshot 2025-10-01 at 11 19 09 AM" src="https://github.com/user-attachments/assets/abab1106-4bdf-4f8b-b208-3e52785b1388" />
<img width="618" height="42" alt="Screenshot 2025-10-01 at 11 19 36 AM" src="https://github.com/user-attachments/assets/c4db7c95-50f3-46ac-8fba-d3fb5db1e9a0" />
Task 9: Conclusion
This task wrapped up the room by giving us playbook that defines what to do in different scenario.

Questions
Question No 1: Per the playbook, what framework was used for the IR process?

Hint: Visit the link provided.

Answer: NIST
<img width="675" height="347" alt="Screenshot 2025-10-01 at 11 21 35 AM" src="https://github.com/user-attachments/assets/c98ff264-7d12-4421-b0ad-ad5cc3f26cdc" />

We'll wrap up this room by sharing a phishing incident response playbook. This playbook will give you an idea of what steps should be considered and executed given this scenario. 

A playbook is a defined process that should be followed in a specific situation, in this case, a phishing incident. 

Phishing IR Playbook:

https://github.com/counteractive/incident-response-plan-template/blob/master/playbooks/playbook-phishing.md  
Lastly, the PCAP file used in this room was from Malware Traffic Analysis. You can explore more details about this PCAP or other samples.

SMTP PCAP Credit: 

https://www.malware-traffic-analysis.net/2018/12/19/index.html

