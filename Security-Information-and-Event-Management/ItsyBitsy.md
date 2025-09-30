<img width="1433" height="273" alt="Screenshot 2025-09-30 at 3 13 52 PM" src="https://github.com/user-attachments/assets/ae854cb0-9925-46fa-b2f2-9913e8715883" />
Hey all, this is the thirty-fourth installment in my walkthrough series on TryHackMe’s SOC Level 1 path which covers the third room in this module on Security Information and Event Management, where we will come to understand how SIEM works and get comfortable creating simple and advanced search queries to look for specific answers from the ingested logs.

In this room, we get to put your ELK knowledge together and investigate an incident.

Link: https://tryhackme.com/room/itsybitsy

Hold my hand for deer life, because here we go!

Task 1: Introduction
In this challenge room, we will take a simple challenge to investigate an alert by IDS regarding a potential C2 communication.

Room Machine
Before moving forward, deploy the machine. When you deploy the machine, it will be assigned an IP Machine IP: MACHINE_IP. The machine will take up to 3-5 minutes to start. Use the following credentials to log in and access the logs in the Discover tab.

Username: Admin

Password: elastic123

Answer the questions below:

1.1 Connect with the lab

For this room, I’lll be connecting through OpenVPN, you can do it this way or by using the provided AttackBox;

Answer: No answer needed

Task 2: Scenario — Investigate a potential C2 communication alert
Scenario
During normal SOC monitoring, Analyst John observed an alert on an IDS solution indicating a potential C2 communication from a user Browne from the HR department. A suspicious file was accessed containing a malicious pattern THM:{ ________ }. A week-long HTTP connection logs have been pulled to investigate. Due to limited resources, only the connection logs could be pulled out and are ingested into the connection_logs index in Kibana.

Our task in this room will be to examine the network connection logs of this user, find the link and the content of the file, and answer the questions.

Answer the questions below:

2.1 How many events were returned for the month of March 2022?

If you followed along with us in the previous ELK room, this will be a piece of cake:

Launch the site provided in Task 1, go to the Discover tab, establish the date range:
<img width="683" height="169" alt="Screenshot 2025-09-30 at 3 15 11 PM" src="https://github.com/user-attachments/assets/732d60b4-8cd5-4145-9de1-443d4cec0ab9" />
Answer: 1482

2.2 What is the IP associated with the suspected user in the logs?

Well, if we filter by “source_ip” we will see exactly 2 IP addresses and one of them is accountable for 99.6% of the traffic. Surely it’s this one right? Nope. They got me on it for sure. This makes the answer pretty obvious as it must therefore be the other one.

Press enter or click to view image in full size
<img width="685" height="177" alt="Screenshot 2025-09-30 at 3 15 20 PM" src="https://github.com/user-attachments/assets/6ee4c099-47fe-49ca-ab86-cd568849f1f3" />
If you want to actually analyze it deeper however, as in the real world, it’s not going to be as easy as having a 50/50 shot, we need to see what the traffic is doing and investigate that.

If we click the “user_agent”, we’ll see again that 99.6% to 0.4% ratio represented here, this time by Mozilla and an agent called “bitsadmin”. Further digging into “bitsadmin” reveals that it’s used by Microsoft for Windows update purposes, but according to a Mandiant article, it can also used by attackers to download and execute payloads.

So is this legitimate traffic to Microsoft servers for updating? Let’s find out.
<img width="679" height="606" alt="Screenshot 2025-09-30 at 3 15 29 PM" src="https://github.com/user-attachments/assets/31f7f689-bfc6-4435-9939-d594bdeb6c44" />
Gasp! That doesn’t look like Microsoft to me!
<img width="703" height="170" alt="Screenshot 2025-09-30 at 3 15 46 PM" src="https://github.com/user-attachments/assets/05d5652d-d381-4880-ba82-5df5b93970b1" />

Let’s take that domain and tack on the URI to see what’s up with it:
<img width="672" height="346" alt="Screenshot 2025-09-30 at 3 15 59 PM" src="https://github.com/user-attachments/assets/773e18de-395c-4f9a-b270-16d2d2924382" />
So this is a very long winded response to the question that we easily solved above, but I feel it’s important to figure out how we can realize the answer to this question instead of just taking a 50/50 shot. Again, it won’t always be that easy.

Answer: 192.166.65.54

2.3 The user’s machine used a legit windows binary to download a file from the C2 server. What is the name of the binary?

We covered this in the explanation of question 2.2:
<img width="696" height="183" alt="Screenshot 2025-09-30 at 3 16 07 PM" src="https://github.com/user-attachments/assets/aed437c4-eddb-4818-a38b-d45f8e2bdee3" />
Answer: bitsadmin

2.4 The infected machine connected with a famous filesharing site in this period, which also acts as a C2 server used by the malware authors to communicate. What is the name of the filesharing site?

We covered this in the explanation of question 2.2:
<img width="691" height="325" alt="Screenshot 2025-09-30 at 3 16 13 PM" src="https://github.com/user-attachments/assets/4d33db6d-d04c-4b95-bc12-28502a3d4548" />
Answer: pastebin.com

2.5 What is the full URL of the C2 to which the infected host is connected?

We covered this in the explanation of question 2.2:

Answer: pastebin.com/yTg0Ah6a

2.6 A file was accessed on the filesharing site. What is the name of the file accessed?

We covered this in the explanation of question 2.2:
<img width="679" height="274" alt="Screenshot 2025-09-30 at 3 16 20 PM" src="https://github.com/user-attachments/assets/93d5e5c8-900f-44ca-9f97-bdb59e5ad365" />
Answer: secret.txt

2.7 The file contains a secret code with the format THM{_____}.

We covered this in the explanation of question 2.2:
<img width="578" height="542" alt="Screenshot 2025-09-30 at 3 16 29 PM" src="https://github.com/user-attachments/assets/ec009f96-4682-49b6-bf6f-68da0b430dce" />
Answer: THM{SECRET__CODE}

This concludes the ItsyBitsy room on TryHackMe. This was a pretty short but good case that we got to investigate. I’d have preferred it if the author had made many more source IPs so that you are kind of forced to learn how to find what we’re looking for instead of just plugging in IP’s but it was a cool example nonetheless.

Thanks for joining me on this walkthrough and I’ll see you in the next one where we will start learning the BIG DOG in the SIEM industry, Splunk, with Splunk: Basics
