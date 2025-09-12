1. Introduction to Network Monitoring Approaches
Network monitoring is a set of management actions to watch/continuously overview and optionally save the network traffic for further investigation. This action aims to detect and reduce network problems, improve performance, and in some cases, increase overall productivity. It is a main part of the daily IT/SOC operations and differs from Network Security Monitoring (NSM) in its purpose.

Network Monitoring
Network monitoring is highly focused on IT assets like uptime (availability), device health and connection quality (performance), and network traffic balance and management (configuration). Monitoring and visualising the network traffic, troubleshooting, and root cause analysis are also part of the Network Monitoring process*.* This model is helpful for network administrators and usually doesn't cover identifying non-asset in-depth vulnerabilities and significant security concerns like internal threats and zero-day vulnerabilities. Usually, Network Monitoring is not within the SOC scope. It is linked to the enterprise IT/Network management team.

Network Security Monitoring
Network Security Monitoring is focused on network anomalies like rogue hosts, encrypted traffic, suspicious service and port usage, and malicious/suspicious traffic patterns in an intrusion/anomaly detection and response approach. Monitoring and visualising the network traffic and investigating suspicious events is a core part of Network Security Monitoring. This model is helpful for security analysts/incident responders, security engineers and threat hunters and covers identifying threats, vulnerabilities and security issues with a set of rules, signatures and patterns. Network Security Monitoring is part of the SOC, and the actions are separated between tier 1-2-3 analyst levels.

What is ZEEK?
Zeek (formerly Bro) is an open-source and commercial passive Network Monitoring tool (traffic analysis framework) developed by Lawrence Berkeley Labs. Today, Zeek is supported by several developers, and Corelight provides an Enterprise-ready fork of Zeek. Therefore this tool is called both open source and commercial. The differences between the open-source version and the commercial version are detailed here.

Zeek differs from known monitoring and IDS/IPS tools by providing a wide range of detailed logs ready to investigate both for forensics and data analysis actions. Currently,** **Zeek provides 50+ logs in 7 categories.

Zeek vs Snort
While both are called IDS/NIDS, it is good to know the cons and pros of each tool and use them in a specific manner. While there are some overlapping functionalities, they have different purposes for usage.

Tool	Zeek	Snort
Capabilities	NSM and IDS framework. It is heavily focused on network analysis. It is more focused on specific threats to trigger alerts. The detection mechanism is focused on events.	An IDS/IPS system. It is heavily focused on signatures to detect vulnerabilities. The detection mechanism is focused on signature patterns and packets.
Cons	Hard to use.
The analysis is done out of Zeek, manually or by automation.
Hard to detect complex threats.	
Pros	It provides in-depth traffic visibility.
Useful for threat hunting.
Ability to detect complex threats.
It has a scripting language and supports event correlation.
Easy to read logs.	Easy to write rules.
Cisco supported rules.
Community support.
Common Use Case	Network monitoring.
In-depth traffic investigation.
Intrusion detecting in chained events.	Intrusion detection and prevention.
Stop known attacks/threats.
Zeek Architecture
Zeek has two primary layers; "Event Engine" and "Policy Script Interpreter". The Event Engine layer is where the packets are processed; it is called the event core and is responsible for describing the event without focusing on event details. It is where the packages are divided into parts such as source and destination addresses, protocol identification, session analysis and file extraction. The Policy Script Interpreter layer is where the semantic analysis is conducted. It is responsible for describing the event correlations by using Zeek scripts.
<img width="704" height="209" alt="Screenshot 2025-09-12 at 7 17 13 PM" src="https://github.com/user-attachments/assets/51a4c1bb-5c36-4552-b103-b5eb293547a4" />
Zeek Frameworks
Zeek has several frameworks to provide extended functionality in the scripting layer. These frameworks enhance Zeek's flexibility and compatibility with other network components. Each framework focuses on the specific use case and easily runs with Zeek installation. For instance, we will be using the "Logging Framework" for all cases. Having ide on each framework's functionality can help users quickly identify an event of interest.

Available Frameworks

Category	Frameworks
Logging	Notice, Input, Configuration, Intelligence
Cluster	Broker Communication, Supervisor, GeoLocation, File Analysis
Signature	Summary, NetControl, Packet Analysis, TLS Decryption
You can read more on frameworks here.

Zeek Outputs
As mentioned before, Zeek provides 50+ log files under seven different categories, which are helpful in various areas such as traffic monitoring, intrusion detection, threat hunting and web analytics. This section is not intended to discuss the logs in-depth. The logs are covered in TASK 3.

Once you run Zeek, it will automatically start investigating the traffic or the given pcap file and generate logs automatically. Once you process a pcap with Zeek, it will create the logs in the working directory.** **If you run the Zeek as a service, your logs will be located in the default log path. The default log path is: /opt/zeek/logs/

Working with Zeek
There are two operation options for Zeek. The first one is running it as a service, and the second option is running the Zeek against a pcap. Before starting working with Zeek, let's check the version of the Zeek instance with the following command: zeek -v

Now we are sure that we have Zeek installed. Let's start the Zeek as a service! To do this, we need to use the "ZeekControl" module, as shown below. The "ZeekControl" module requires superuser permissions to use.** **You can elevate the session privileges and switch to the superuser account to examine the generated log files with the following command: sudo su

Here we can manage the Zeek service and view the status of the service. Primary management of the Zeek service is done with three commands; "status", "start", and "stop".
<img width="707" height="398" alt="Screenshot 2025-09-12 at 7 18 12 PM" src="https://github.com/user-attachments/assets/79dbb053-b09a-463d-b714-348630d22baf" />
You can also use the "ZeekControl" mode with the following commands as well;

zeekctl status
zeekctl start
zeekctl stop
The only way to listen to the live network traffic is using Zeek as a service. Apart from using the Zeek as a network monitoring tool, we can also use it as a packet investigator.** **To do so, we need to process the pcap files with Zeek, as shown below. Once you process a pcap file, Zeek automatically creates log files according to the traffic.

In pcap processing mode, logs are saved in the working directory. You can view the generated logs using the ls -l command.
<img width="713" height="211" alt="Screenshot 2025-09-12 at 7 18 21 PM" src="https://github.com/user-attachments/assets/fba68175-e9cf-4ade-bdee-9bde13ecc1e2" />
Zeek Command Line Parameters
Below are the main Zeek command line parameters and their descriptions:

Parameter	Description
-r	Reading option, read/process a pcap file.
-C	Ignoring checksum errors.
-v	Version information.
zeekctl	ZeekControl module.
Flag 1
What is the installed Zeek instance version number?

Run zeek -v
<img width="711" height="44" alt="Screenshot 2025-09-12 at 7 19 18 PM" src="https://github.com/user-attachments/assets/b6361c88-84dd-4878-991c-c2139279b6d8" />
Flag 2
What is the version of the ZeekControl module?

Run zeekctl
<img width="713" height="195" alt="Screenshot 2025-09-12 at 7 19 27 PM" src="https://github.com/user-attachments/assets/73a65209-c75f-42f5-8abf-c83119ad408d" />
Flag 3
Investigate the "sample.pcap" file. What is the number of generated alert files?

Run zeek -C -r sample.pcap
<img width="709" height="37" alt="Screenshot 2025-09-12 at 7 19 38 PM" src="https://github.com/user-attachments/assets/85a84e01-ed0b-478f-97ce-661a926d2274" />

We can then navigate to the task folder to see how many log files has been generated, in my case we got 8.
<img width="713" height="298" alt="Screenshot 2025-09-12 at 7 19 47 PM" src="https://github.com/user-attachments/assets/092a6f01-3b0f-42be-a81d-6690a4608299" />
2. Zeek Logs
Zeek generates log files according to the traffic data. You will have logs for every connection in the wire, including the application level protocols and fields. Zeek is capable of identifying 50+ logs and categorising them into seven categories. Zeek logs are well structured and tab-separated ASCII files, so reading and processing them is easy but requires effort. You should be familiar with networking and protocols to correlate the logs in an investigation, know where to focus, and find a specific piece of evidence.

Each log output consists of multiple fields, and each field holds a different part of the traffic data. Correlation is done through a unique value called "UID". The "UID" represents the unique identifier assigned to each session.

Zeek logs in a nutshell;

Category	Description	Log Files
Network	Network protocol logs.	conn.log, dce_rpc.log, dhcp.log, dnp3.log, dns.log, ftp.log, http.log, irc.log, kerberos.log, modbus.log, modbus_register_change.log, mysql.log, ntlm.log, ntp.log, radius.log, rdp.log, rfb.log, sip.log, smb_cmd.log, smb_files.log, smb_mapping.log, smtp.log, snmp.log, socks.log, ssh.log, ssl.log, syslog.log, tunnel.log
Files	File analysis result logs.	files.log, ocsp.log, pe.log, x509.log
NetControl	Network control and flow logs.	netcontrol.log, netcontrol_drop.log, netcontrol_shunt.log, netcontrol_catch_release.log, openflow.log
Detection	Detection and possible indicator logs.	intel.log, notice.log, notice_alarm.log, signatures.log, traceroute.log
Network Observations	Network flow logs.	known_certs.log, known_hosts.log, known_modbus.log, known_services.log, software.log
Miscellaneous	Additional logs covering external alerts, inputs, and failures.	barnyard2.log, dpd.log, unified2.log, unknown_protocols.log, weird.log, weird_stats.log
Zeek Diagnostic	Zeek diagnostic logs covering system messages, actions, and some statistics.	broker.log, capture_loss.log, cluster.log, config.log, loaded_scripts.log, packet_filter.log, print.log, prof.log, reporter.log, stats.log, stderr.log, stdout.log
Please refer to Zeek's official documentation and Corelight log cheat sheet for more information. Although there are multiple log files, some log files are updated daily, and some are updated in each session. Some of the most commonly used logs are explained in the given table.

Update Frequency	Log Name	Description
Daily	known_hosts.log	List of hosts that completed TCP handshakes.
Daily	known_services.log	List of services used by hosts.
Daily	known_certs.log	List of SSL certificates.
Daily	software.log	List of software used on the network.
Per Session	notice.log	Anomalies detected by Zeek.
Per Session	intel.log	Traffic contains malicious patterns/indicators.
Per Session	signatures.log	List of triggered signatures.
This is too much protocol and log information! Yes, it is true; a difficulty of working with Zeek is having the required network knowledge and investigation mindset. Don't worry; you can have both of these and even more knowledge by working through TryHackMe paths. Just keep the streak!

Brief log usage primer table;

Overall Info	Protocol-Based	Detection	Observation
conn.log	http.log	notice.log	known_host.log
files.log	dns.log	signatures.log	known_services.log
intel.log	ftp.log	pe.log	software.log
loaded_scripts.log	ssh.log	traceroute.log	weird.log
You can categorise the logs before starting an investigation. Thus, finding the evidence/anomaly you are looking for will be easier. The given table is a brief example of using multiple log files. You can create your working model or customise the given one. Make sure you read each log description and understand the purpose to know what to expect from the corresponding log file. Note that these are not the only ones to focus on. Investigated logs are highly associated with the investigation case type and hypothesis, so do not just rely only on the logs given in the example table!

The table shows us how to use multiple logs to identify anomalies and run an investigation by correlating across the available logs.

**Overall Info: **The aim is to review the overall connections, shared files, loaded scripts and indicators at once. This is the first step of the investigation.
**Protocol Based: **Once you review the overall traffic and find suspicious indicators or want to conduct a more in-depth investigation, you focus on a specific protocol.
**Detection: **Use the prebuild or custom scripts and signature outcomes to support your findings by having additional indicators or linked actions.
**Observation: **The summary of the hosts, services, software, and unexpected activity statistics will help you discover possible missing points and conclude the investigation.
Remember, we mention the pros and cons of the Zeek logs at the beginning of this task. Now let's demonstrate the log viewing and identify the differences between them.

Recall 1: Zeek logs are well structured and tab-separated ASCII files, so reading and processing them is easy but requires effort.

Recall 2: Investigating the generated logs will require command-line tools (cat, cut, grep sort, and uniq) and additional tools (zeek-cut).

Opening a Zeek log with a text editor and built-in commands;
<img width="467" height="552" alt="Screenshot 2025-09-12 at 7 20 02 PM" src="https://github.com/user-attachments/assets/3af0ea1e-868e-438f-9252-530f43e4b50f" />
The above image shows that reading the logs with tools is not enough to spot an anomaly quickly. Logs provide a vast amount of data to investigate and correlate. You will need to have technical knowledge and event correlation ability to carry out an investigation. It is possible to use external visualisation and correlation tools such as ELK and Splunk. We will focus on using and processing the logs with a hands-on approach in this room.

In addition to Linux command-line tools, one auxiliary program called zeek-cut** **reduces the effort of extracting specific columns from log files. Each log file provides "field names" in the beginning. This information will help you while using zeek-cut. Make sure that you use the "fields" and not the "types".

Tool/Auxilary Name	Purpose
Zeek-cut	Cut specific columns from zeek logs.
Let's see the "zeek-cut" in action. Let's extract the uid, protocol, source and destination hosts, and source and destination ports from the conn.log. We will first read the logs with the cat command and then extract the event of interest fields with zeek-cut auxiliary to compare the difference.
<img width="706" height="278" alt="Screenshot 2025-09-12 at 7 20 09 PM" src="https://github.com/user-attachments/assets/aa0f07cc-a45d-4710-a828-f567f1fd07af" />

As shown in the above output, the "zeek-cut" auxiliary provides massive help to extract specific fields with minimal effort. Now take time to read log formats, practice the log reading/extracting operations and answer the questions.

Flag 1
Investigate the sample.pcap file. Investigate the dhcp.log file. What is the available hostname?

We run a Zeek scan against sample.pcap using zeek -C -r sample.pcap and read dhcp.log by running cat dhcp.log.
<img width="716" height="76" alt="Screenshot 2025-09-12 at 7 23 29 PM" src="https://github.com/user-attachments/assets/6854e21d-652c-4c84-828c-7aba4ac783e5" />
As we can see, the parameter hostname is represented as host_name.

With this in mind, we use zeek-cut by executing cat dhcp.log | zeek-cut host_name to retrieve our flag.
<img width="712" height="47" alt="Screenshot 2025-09-12 at 7 23 36 PM" src="https://github.com/user-attachments/assets/c2183aba-f631-498e-abd4-1d4ad6152b7e" />
Flag 2
Investigate the dns.log file. What is the number of unique DNS queries?

As we run cat dns.log, we see that the parameter query stores all DNS requested in each request.
<img width="709" height="141" alt="Screenshot 2025-09-12 at 7 23 46 PM" src="https://github.com/user-attachments/assets/20b1fe26-f165-458f-9c22-349ac76ddc78" />
With this in mind, we can execute cat dns.log | zeek-cut query | sort | uniq | wc -l

zeek-cut query to get all query parameters
| sort | uniq to get only unique output
wc -l to count all lines of output
And we get the flag as follows.
<img width="705" height="27" alt="Screenshot 2025-09-12 at 7 23 55 PM" src="https://github.com/user-attachments/assets/21caf3af-b802-4362-a89c-4816c632ad17" />
Flag 3
Investigate the conn.log file. What is the longest connection duration?

As we run cat conn.log, we see the parameter duration.
<img width="704" height="108" alt="Screenshot 2025-09-12 at 7 24 03 PM" src="https://github.com/user-attachments/assets/d05127e0-f02d-4027-8ff1-18a599aee43c" />
To verify that duration parameter outputs what we are looking for, we run cat conn.log | zeek-cut duration and sure enough it outputs exactly what we want, the connection duration.
<img width="720" height="421" alt="Screenshot 2025-09-12 at 7 24 13 PM" src="https://github.com/user-attachments/assets/d86164b6-cbdd-42ca-9a4c-7933142cf9f6" />
We can run cat conn.log | zeek-cut duration | sort -n | tail -1

sort -n sorts output numerically
tail -1 gets the last output
<img width="712" height="29" alt="Screenshot 2025-09-12 at 7 24 24 PM" src="https://github.com/user-attachments/assets/9ba01665-e43f-4e89-8ae9-6613a66aa41e" />


3. CLI Kung-Fu Recall: Processing Zeek Logs
Graphical User Interfaces (GUI) are handy and good for accomplishing tasks and processing information quickly. There are multiple advantages of GUIs, especially when processing the information visually. However, when processing massive amounts of data, GUIs are not stable and as effective as the CLI (Command Line Interface) tools.

The critical point is: What if there is no "function/button/feature" for what you want to find/view/extract?

Having the power to manipulate the data at the command line is a crucial skill for analysts. Not only in this room but each time you deal with packets, you will need to use command-line tools, Berkeley Packet Filters (BPF) and regular expressions to find/view/extract the data you are looking for. This task provides quick cheat-sheet like information to help you write CLI queries for your event of interest.

Command Categories and Usage
Basics
Command	Purpose
history	View the command history.
!10	Execute the 10th command in history.
!!	Execute the previous command.
Read File
Command	Purpose
cat sample.txt	Read the sample.txt file.
head sample.txt	Read the first 10 lines of the file.
tail sample.txt	Read the last 10 lines of the file.
Find & Filter
Command	Purpose
`cat test.txt \	cut -f 1`
`cat test.txt \	cut -c1`
`cat test.txt \	grep 'keywords'`
`cat test.txt \	sort`
`cat test.txt \	sort -n`
`cat test.txt \	uniq`
`cat test.txt \	wc -l`
`cat test.txt \	nl`
Advanced
Command	Purpose
`cat test.txt \	sed -n '11p'`
`cat test.txt \	sed -n '10,15p'`
`cat test.txt \	awk 'NR < 11 {print $0}'`
`cat test.txt \	awk 'NR == 11 {print $0}'`
Special
Command	Purpose
`cat signatures.log \	zeek-cut uid src_addr dst_addr`
Common Use Cases
Use Case	Description
`sort \	uniq`
`sort \	uniq -c`
sort -nr	Sort values numerically and recursively.
rev	Reverse string characters.
cut -f 1	Cut field 1.
cut -d '.' -f 1-2	Split the string on every dot and keep the first two fields.
grep -v 'test'	Display lines that don't match "test".
grep -v -e 'test1' -e 'test2'	Display lines that don't match "test1" or "test2".
file	View file information.
`grep -rin Testvalue1 \	column -t \
This Markdown table makes it easier to read and use. Let me know if you need any refinements! 🚀

4. Zeek Signatures
Zeek supports signatures to have rules and event correlations to find noteworthy activities on the network. Zeek signatures use low-level pattern matching and cover conditions similar to Snort rules. Unlike Snort rules, Zeek rules are not the primary event detection point. Zeek has a scripting language and can chain multiple events to find an event of interest. We focus on the signatures in this task, and then we will focus on Zeek scripting in the following tasks.

Zeek signatures are composed of three logical paths; signature id, conditions and action. The signature breakdown is shown in the table below;

Signature id	Unique signature name.
Conditions	Header: Filtering the packet headers for specific source and destination addresses, protocol and port numbers.
Content: Filtering the packet payload for specific value/pattern.
Action	Default action: Create the "signatures.log" file in case of a signature match.

Additional action: Trigger a Zeek script.
Now let's dig more into the Zeek signatures. The below table provides the most common conditions and filters for the Zeek signatures.

Condition Field	Available Filters
Header	src-ip: Source IP.

dst-ip: Destination IP.

src-port: Source port.

dst-port: Destination port.

ip-proto: Target protocol. Supported protocols; TCP, UDP, ICMP, ICMP6, IP, IP6
Content	payload: Packet payload.
http-request: Decoded HTTP requests.
http-request-header: Client-side HTTP headers.
http-request-body: Client-side HTTP request bodys.
http-reply-header: Server-side HTTP headers.
http-reply-body: Server-side HTTP request bodys.
ftp: Command line input of FTP sessions.
Context	same-ip: Filtering the source and destination addresses for duplication.
Action	**event: **Signature match message.
Comparison Operators	==, !=, <, <=, >, >=
NOTE!	Filters accept string, numeric and regex values.
Run Zeek with signature file

{% raw %}ubuntu@ubuntu$ zeek -C -r sample.pcap -s sample.sig

Example | Cleartext Submission of Password
Let's create a simple signature to detect HTTP cleartext passwords.

Sample Signature
<img width="709" height="333" alt="Screenshot 2025-09-12 at 7 24 39 PM" src="https://github.com/user-attachments/assets/658b399f-c4cc-4459-8c37-594f2b9ad385" />

Remember, Zeek signatures support regex. Regex ".*" matches any character zero or more times. The rule will match when a "password" phrase is detected in the packet payload. Once the match occurs, Zeek will generate an alert and create additional log files (signatures.log and notice.log).

Signature Usage and Log Analysis

<img width="713" height="299" alt="Screenshot 2025-09-12 at 7 28 41 PM" src="https://github.com/user-attachments/assets/748fcf58-2eb2-4803-a768-27c725a199a1" />
As shown in the above terminal output, the signatures.log and notice.log provide basic details and the signature message. Both of the logs also have the application banner field. So it is possible to know where the signature match occurs. Let's look at the application banner!

Log Analysis
<img width="708" height="161" alt="Screenshot 2025-09-12 at 7 28 49 PM" src="https://github.com/user-attachments/assets/262f17a4-efe8-431d-8966-275c77232932" />
We will demonstrate only one log file output to avoid duplication after this point. You can practice discovering the event of interest by analysing notice.log and signatures.log.

Let's create another rule to filter FTP traffic. This time, we will use the FTP content filter to investigate command-line inputs of the FTP traffic. The aim is to detect FTP "admin" login attempts. This basic signature will help us identify the admin login attempts and have an idea of possible admin account abuse or compromise events.

Sample Signature
<img width="710" height="165" alt="Screenshot 2025-09-12 at 7 29 07 PM" src="https://github.com/user-attachments/assets/6a33057a-87dd-4a45-9b9e-493fea5b291d" />
Let's run the Zeek with the signature and investigate the signatures.log and notice.log
<img width="705" height="140" alt="Screenshot 2025-09-12 at 7 29 15 PM" src="https://github.com/user-attachments/assets/a5b4229f-7c64-4ca1-8829-1156700b5fdf" />

Our rule shows us that there are multiple logging attempts with account names containing the "admin" phrase. The output gives us great information to notice if there is a brute-force attempt for an admin account.

This signature can be considered a case signature. While it is accurate and works fine, we need global signatures to detect the "known threats/anomalies". We will need those case-based signatures for significant and sophistical anomalies like zero-days and insider attacks in the real-life environment. Having individual rules for each case will create dozens of logs and alerts and cause missing the real anomaly. The critical point is logging logically, not logging everything.

We can improve our signature by not limiting the focus only to an admin account. In that case, we need to know how the FTP protocol works and the default response codes. If you don't know these details, please refer to RFC documentation.

Let's optimise our rule and make it detect all possible FTP brute-force attempts.

This signature will create logs for each event containing "FTP 530 response", which allows us to track the login failure events regardless of username.

<img width="710" height="168" alt="Screenshot 2025-09-12 at 7 29 29 PM" src="https://github.com/user-attachments/assets/74894ab1-d64a-48d2-b48b-301886908200" />
Zeek signature files can consist of multiple signatures. Therefore we can have one file for each protocol/situation/threat type. Let's demonstrate this feature in our global rule.
<img width="714" height="314" alt="Screenshot 2025-09-12 at 7 29 40 PM" src="https://github.com/user-attachments/assets/87d2764f-b33a-4b0f-a302-490571f18b9a" />
Let's merge both of the signatures in a single file. We will have two different signatures, and they will generate alerts according to match status. The result will show us how we benefit from this action. Again, we will need the "CLI Kung-Fu" skills to extract the event of interest.

This rule should show us two types of alerts and help us to correlate the events by having "FTP Username Input" and "FTP Brute-force Attempt" event messages. Let's investigate the logs. We're grepping the logs in range 1001-1004 to demonstrate that the first rule matches two different accounts (admin and administrator).
<img width="714" height="194" alt="Screenshot 2025-09-12 at 7 29 49 PM" src="https://github.com/user-attachments/assets/7027082b-6e6c-4636-be1c-e6dca9b53311" />
Snort Rules in Zeek?

While Zeek was known as Bro, it supported Snort rules with a script called snort2bro, which converted Snort rules to Bro signatures. However, after the rebranding, workflows between the two platforms have changed. The official Zeek document mentions that the script is no longer supported and is not a part of the Zeek distribution.

Flag 1
Investigate the http.pcap file. Create the HTTP signature shown in the task and investigate the pcap. What is the source IP of the first event?

Use the signature created in the task by replacing the content of the http-password.sig with this.
<img width="712" height="193" alt="Screenshot 2025-09-12 at 7 29 59 PM" src="https://github.com/user-attachments/assets/0c394d14-9211-441c-918f-773b7ef9304d" />
Then we run Zeek against the pcap file using this signature by executing zeek -C -r http.pcap -s http-password.sig.

We then just run cat notice.log | zeek-cut uid id.orig_h

uid to view the list of output
id.orig_h to view the source IPs
We can retrieve the flag just like that.
<img width="722" height="46" alt="Screenshot 2025-09-12 at 7 30 08 PM" src="https://github.com/user-attachments/assets/049549fc-cfed-4143-b45c-1a4fdc3cb002" />
Flag 2
Run cat notice.log | zeek-cut uid id.orig_p.

uid to identify the list of output
id.orig_p to view the source ports
What is the source port of the second event?
<img width="711" height="50" alt="Screenshot 2025-09-12 at 7 30 30 PM" src="https://github.com/user-attachments/assets/b480ca2b-3edd-484c-b223-654f1832bd18" />
Flag 3
Investigate the conn.log.
What is the total number of the sent and received packets from source port 38706?

Run cat conn.log | zeek-cut uid id.orig_p orig_pkts resp_pkts | grep 38706.

uid to identify the list of output
id.orig_p to view the source ports
orig_pkts to view sent packets count
resp_pkts to view received packets count
grep 38706 to get the line that matches 38706 as port number
<img width="712" height="27" alt="Screenshot 2025-09-12 at 7 30 37 PM" src="https://github.com/user-attachments/assets/f2fe61fb-a1be-476b-95f7-404a96b6054b" />



