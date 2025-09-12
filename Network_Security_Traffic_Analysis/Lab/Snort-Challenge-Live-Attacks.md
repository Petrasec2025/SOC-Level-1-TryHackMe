<img width="732" height="228" alt="Screenshot 2025-09-12 at 5 35 40 PM" src="https://github.com/user-attachments/assets/0fd6bd60-d0b1-4b0b-88ce-3f8949a0cff3" />
This room is part of the SOC Level 1 Path.

I am making these walkthroughs to keep myself motivated to learn cyber security, and ensure that I remember the knowledge gained by these challenges on HTB and THM. Join me on learning cyber security. I will try and explain concepts as I go, to differentiate myself from other walkthroughs.

Now, let’s move on!
Task 1: Introduction
The room invites you to a challenge where you will investigate a series of traffic data and stop malicious activity under two different scenarios. Let’s start working with Snort to analyse live and captured traffic.
<img width="1278" height="521" alt="Screenshot 2025-09-12 at 5 35 53 PM" src="https://github.com/user-attachments/assets/ac863803-0ebc-41e3-a3eb-03ea5e6cc2ff" />
Questions
Read the task above.
Answer: No answer needed

Task 2: Scenario 1 | Brute-Force
Use the attached VM to finish this task.
<img width="299" height="295" alt="Screenshot 2025-09-12 at 5 41 39 PM" src="https://github.com/user-attachments/assets/7dce2d3f-dc6f-4fe7-982a-9fdf781f9803" />


[+] THE NARRATOR

J&Y Enterprise is one of the top coffee retails in the world. They are known as tech-coffee shops and serve millions of coffee lover tech geeks and IT specialists every day. 

They are famous for specific coffee recipes for the IT community and unique names for these products. Their top five recipe names are;

WannaWhite, ZeroSleep, MacDown, BerryKeep and CryptoY.

J&Y’s latest recipe, “Shot4J“, attracted great attention at the global coffee festival. J&Y officials promised that the product will hit the stores in the coming months. 

The super-secret of this recipe is hidden in a digital safe. Attackers are after this recipe, and J&Y enterprises are having difficulties protecting their digital assets.

Last week, they received multiple attacks and decided to work with you to help them improve their security level and protect their recipe secrets.  

This is your assistant J.A.V.A. (Just Another Virtual Assistant). She is an AI-driven virtual assistant and will help you notice possible anomalies. Hey, wait, something is happening…

[+] J.A.V.A.

Welcome, sir. I am sorry for the interruption. It is an emergency. Somebody is knocking on the door!

[+] YOU

Knocking on the door? What do you mean by “knocking on the door”?

[+] J.A.V.A.

We have a brute-force attack, sir.

[+] THE NARRATOR

This is not a comic book! Would you mind going and checking what’s going on! Please… 

[+] J.A.V.A.

Sir, you need to observe the traffic with Snort and identify the anomaly first. Then you can create a rule to stop the brute-force attack. GOOD LUCK!

Questions
First of all, start Snort in sniffer mode and try to figure out the attack source, service and port.

Then, write an IPS rule and run Snort in IPS mode to stop the brute-force attack. Once you stop the attack properly, you will have the flag on the desktop!

Here are a few points to remember:

Create the rule and test it with “-A console” mode. 
Use “-A full” mode and the default log path to stop the attack.
Write the correct rule and run the Snort in IPS “-A full” mode.
Block the traffic at least for a minute and then the flag file will appear on your desktop.
Stop the attack and get the flag (which will appear on your Desktop
Stop the attack and get the flag (which will appear on your Desktop)
Alright, let’s stop this attack!

As suggested by the room creator, we have to start by running Snort in sniffer mode.

To remind you, the Snort flags of interest are:

-v	Verbose. Display the TCP/IP output in the console.
-d	Display the packet data (payload).
-e	Display the link-layer (TCP/IP/UDP/ICMP) headers.
–X	Display the full packet details in HEX.
–i	This parameter helps to define a specific network interface to listen/sniff. Once you have multiple interfaces, you can choose a specific interface to sniff.
Let’s run the following command:
<img width="900" height="73" alt="Screenshot 2025-09-12 at 5 42 36 PM" src="https://github.com/user-attachments/assets/0ebdd17b-f2c3-418f-920f-555091c672d2" />
This gives us as much as possible data to look at, and display the details in HEX format as well.

I will keep it running for a 10-15 seconds and that should give us enough data to look at. Since the task mentions that we are experiencing a brute-force attack we should be looking for large number of packets reaching the same destination.

In total I ended up analyzing 1934 packets within 12 seconds.
<img width="492" height="366" alt="Screenshot 2025-09-12 at 5 42 47 PM" src="https://github.com/user-attachments/assets/94175620-084b-450a-b4b0-412200a5b27d" />
I started scrolling through the packets, and noticed a lot of packets running from port 22 on 10.10.140.29 to port 46634 on 10.10.245.36.
<img width="816" height="518" alt="Screenshot 2025-09-12 at 5 43 01 PM" src="https://github.com/user-attachments/assets/acf1d077-ca9a-4b50-9439-cdb91289fbe2" />
Traffic from port 22
The traffic in the capture is originating from port 22, which is typically associated with SSH (Secure Shell). It seems like the traffic is part of an SSH handshake or key exchange, and the packet you’re seeing is likely the initial SSH negotiation from a client to a server. The key exchange part includes different cryptographic algorithms that the client supports for establishing a secure SSH session, like ecdsa-sha2-nistp256 and ssh-ed25519.

There are more examples of this:
<img width="803" height="198" alt="Screenshot 2025-09-12 at 5 43 12 PM" src="https://github.com/user-attachments/assets/1b5833fe-4ace-4aa6-a333-c6127772a24c" />
Traffic from port 22 once more
But traffic should be moving towards port 22, and the last two packets are merely responses from the server. Scroll a bit up and you will see traffic going the other way, likely the attacker trying to connect to the SSH server:
<img width="800" height="426" alt="Screenshot 2025-09-12 at 5 43 21 PM" src="https://github.com/user-attachments/assets/e992da36-19f5-42fa-84a6-a6122b3d34a5" />
Traffic both ways
Notice the flags, seen on line 4 of each package. They have the following meaning:

***A**S* = ACK and SYN (typically part of the TCP handshake)
***A**** = ACK (acknowledging the receipt of data)
What we see here is the last 2 parts of the TCP handshake:

SYN/ACK response (SYN/ACK from server to client): The server responds with a SYN/ACK packet, indicating that it has received the SYN from the client and is acknowledging the request. This is the second step in the TCP handshake. The SYN flag is used to confirm the desire to establish the connection, while the ACK flag acknowledges the client’s request.

Final ACK (ACK from client to server): After receiving the SYN/ACK response from the server, the client sends an ACK packet. This is the final step in the TCP handshake, where the client acknowledges the server’s response. This packet typically has the ACK flag set and indicates that the connection is now established.

Note, there are also other IP addresses connecting to the SSH. It’s very common for brute-force attacks to originate from different IPs, due to the use of Botnets, proxies and VPNs.

So it seems like something suspicious is definitely going on. Let’s try logging some traffic in a pcap file so we can analyze it a bit more.

We can either log in packet logger mode with ASCII mode:
<img width="903" height="80" alt="Screenshot 2025-09-12 at 5 45 58 PM" src="https://github.com/user-attachments/assets/08aaf52a-9424-4427-bb95-e37f35ac4407" />
I
A directory structure will get formed, and here we can see that there exists a folder named 10.10.245.36 (the attacker machine). In it you will find many log files for all the differents ports it used to attack our SSH service:
<img width="909" height="552" alt="Screenshot 2025-09-12 at 5 46 10 PM" src="https://github.com/user-attachments/assets/156a4039-28b1-44b1-a703-ee9fe950eefe" />
Alternatively you can log regularly by running:
<img width="899" height="83" alt="Screenshot 2025-09-12 at 5 47 08 PM" src="https://github.com/user-attachments/assets/7dfa69e8-c21e-4a3d-b3b8-527090df8141" />
This creates a snort.log.<number> file which you can read like this:
<img width="898" height="68" alt="Screenshot 2025-09-12 at 5 47 26 PM" src="https://github.com/user-attachments/assets/d6cb2462-a46f-4250-a6cf-88c3da8557fb" />
This time, I captured 4516 packets.

A primer on BPF (Berkeley Packet Filter)
We can filter the packages we read in Snort by using a language called BPF.
One of the possibilities is to filter on port and tcp by running:

sudo snort -r snort.log.1738782688 'tcp and port 22'
This returns 619 packets, which is quite a relatively large chunk of the total traffic.

Alternatively you can use:

sudo snort -r snort.log.1738782688 'host 10.10.245.36'
This shows that a total of 619 packets are involved with the attacker machine, and we can probably conclude that all of these are connecting to the SSH service:
<img width="411" height="658" alt="Screenshot 2025-09-12 at 5 48 50 PM" src="https://github.com/user-attachments/assets/80ac2851-bde9-4468-88ab-9a5ae1583932" />
<img width="424" height="97" alt="Screenshot 2025-09-12 at 5 48 57 PM" src="https://github.com/user-attachments/assets/c3958357-23a0-4e46-b77e-1e799e57356f" />

Stopping the attack
We did a little bit of extra work to proof that 10.10.245.36 is the machine attacking us with a brute-force attack. Now all we need to do is create a rule, and start up Snort in IPS mode. What to put in the rule? I guess we could block the SSH, but that could cause problems. The easiest method is by blocking the malicious IP address.

The local.rules file is located here:

/etc/snort/rules/local.rules
You can edit it like so:

sudo gedit /etc/snort/rules/local.rules
I propose we add the following rule:

alert tcp 10.10.245.36 any -> any 22 (msg:"Traffic originating from suspicious host"; sid:100001; rev:1;)
We can now test the rule by running:

sudo snort -c /etc/snort/rules/local.rules -A console
And sure enough, you should see alert messages popping up:
<img width="878" height="597" alt="Screenshot 2025-09-12 at 5 49 59 PM" src="https://github.com/user-attachments/assets/20dcf05b-5cf3-4879-a38b-6f721b76249d" />

Now we can run snort with the -A full option, which adds the printing of full alert information, as suggested in the task.

sudo snort -c /etc/snort/rules/local.rules -A full
Keep it running for a minute.

A flag should be created on your Desktop:

<img width="907" height="521" alt="Screenshot 2025-09-12 at 5 51 53 PM" src="https://github.com/user-attachments/assets/ad21ea40-458d-4760-af1c-ee5ce125db9c" />
AWESOME! That was really fun!

Answer:THM{81b7fef657f8aaa6e4e200d616738254}

What is the name of the service under attack?
We discussed this above. The service is SSH.

Answer: SSH
What is the used protocol/port in the attack?
The SSH service is running on TCP port 22.

Answer: TCP/22

Task 3: Scenario 2 | Reverse-Shell
[+] THE NARRATOR

Good Job! Glad to have you in the team!

[+] J.A.V.A.

Congratulations sir. It is inspiring watching you work.

[+] You

Thanks team. J.A.V.A. can you do a quick scan for me? We haven’t investigated the outbound traffic yet. 

[+] J.A.V.A.

Yes, sir. Outbound traffic investigation has begun. 

[+] THE NARRATOR

The outbound traffic? Why?

[+] YOU

We have stopped some inbound access attempts, so we didn’t let the bad guys get in. How about the bad guys who are already inside? Also, no need to mention the insider risks, huh? The dwell time is still around 1-3 months, and I am quite new here, so it is worth checking the outgoing traffic as well.

[+] J.A.V.A.

Sir, persistent outbound traffic is detected. Possibly a reverse shell…

[+] YOU

You got it!

[+] J.A.V.A.

Sir, you need to observe the traffic with Snort and identify the anomaly first. Then you can create a rule to stop the reverse shell. GOOD LUCK!

Questions
First of all, start Snort in sniffer mode and try to figure out the attack source, service and port.

Then, write an IPS rule and run Snort in IPS mode to stop the brute-force attack. Once you stop the attack properly, you will have the flag on the desktop!

Here are a few points to remember:

Create the rule and test it with “-A console” mode. 
Use “-A full” mode and the default log path to stop the attack.
Write the correct rule and run the Snort in IPS “-A full” mode.
Block the traffic at least for a minute and then the flag file will appear on your desktop.
Stop the attack and get the flag (which will appear on your Desktop)
Well, we know the drill. The process will be very much like the previous task. We need to investigate the current traffic, and block is afterwards,
Make sure you started up the machine attached to this task.

Let’s again run the following command:

sudo snort -devX
This gives us as much as possible data to look at, and display the details in HEX format as well.

I will keep it running again for 10-15 seconds so we have enough data to look at. This time we should be looking for a reverse shell so we should be looking out for traffic that originates from the hsot and towards the attacker.

This time I ended up analyzing 3987 packets within around 16 seconds.

Now proceed as before. Let’s simply scroll around through the traffic to get a feeling for the data and to see if we see something suspicious.

It didn’t took long for me to find something VERY suspicious:

<img width="831" height="328" alt="Screenshot 2025-09-12 at 5 53 42 PM" src="https://github.com/user-attachments/assets/bdd68b68-85a1-4376-aa22-929c22f1790a" />
There are actually 3 interesting findings here:

The payload includes shell prompt information, likely from an interactive shell session.
What is even more suspicious is the fact that it being sent to port 4444. If you have some experience with penetration testing, you will know that port 4444 is often used to setup reverse shells. It is especially commonly used by Metasploit.
The combination of ACK + PUSH (AP) flags indicates that this is active data transfer rather than just a handshake.
There is more suspicious activity from the same host and with the same destination:
<img width="709" height="297" alt="Screenshot 2025-09-12 at 5 54 26 PM" src="https://github.com/user-attachments/assets/b6b6d19d-f28e-4f3c-a737-464835aa4410" />
Again, more evidence. The file paths in the payload may indicate that the attacker is gathering information or attempting to exfiltrate files.

I feel like we have enough evidence. Let’s stop the attack ASAP.

Stopping the attack
Once again, we have to write a rule and start up Snort in IPS mode. I think we should block the source IP address we found to make sure the attacker will get stopped from that IP. In addition, I think we could block port 4444.

The local.rules file is located here:

/etc/snort/rules/local.rules
You can edit it like so:

sudo gedit /etc/snort/rules/local.rules
I propose we add the following rule to stop traffic from the host:

alert tcp 10.10.196.55 any -> any any (msg:"Traffic from malicious host"; sid:100001; rev:1;)
And all traffic towards port 4444 in case the attacker uses different IPs.

alert tcp any any -> any any (msg:"Potential Reverse Shell on Port 4444"; sid:100002; rev:1;)
They should look like this:
<img width="912" height="228" alt="Screenshot 2025-09-12 at 5 54 38 PM" src="https://github.com/user-attachments/assets/a7e2662c-14ff-4bd1-974c-6d01aba1e9d1" />
We can now test the rules by running:

sudo snort -c /etc/snort/rules/local.rules -A console
And yet again, alerts are popping up:
<img width="907" height="381" alt="Screenshot 2025-09-12 at 5 54 48 PM" src="https://github.com/user-attachments/assets/4ac70aeb-8427-474a-8dcf-46ba2bbd72f1" />
Now we can run snort with the -A full option as suggested in the task.

sudo snort -c /etc/snort/rules/local.rules -A full
Keep it running for a minute.

A flag should again be created on your Desktop
<img width="911" height="452" alt="Screenshot 2025-09-12 at 5 55 01 PM" src="https://github.com/user-attachments/assets/b1c46e7b-6ea6-4270-aad8-c49fda0a4409" />
What is the used protocol/port in the attack?
We saw in the packets that all traffic used to TCP protocol. In addition, we noted connections aiming at port 4444.

Answer: tcp/4444

Which tool is highly associated with this specific port number?
The tool commonly associated with port 4444 is Metasploit. A ton of exploits running through Metasploit use port 4444 as default. As you know, people are lazy so many often run this default port 🙂

Answer: Metasploit

Congratulations on completing Snort Challenge – Live Attacks!!!



