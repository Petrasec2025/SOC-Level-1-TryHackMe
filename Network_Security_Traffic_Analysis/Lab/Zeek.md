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
