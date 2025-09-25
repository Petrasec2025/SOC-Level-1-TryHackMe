# 🖥️ Wireshark Traffic Analysis Write-up

![Wireshark](https://img.shields.io/badge/Tool-Wireshark-blue?style=flat-square) ![Traffic Analysis](https://img.shields.io/badge/Topic-Traffic_Analysis-green?style=flat-square) ![TryHackMe](https://img.shields.io/badge/Platform-TryHackMe-orange?style=flat-square) ![Packet Analysis](https://img.shields.io/badge/Skill-Packet_Analysis-red?style=flat-square) ![Network Security](https://img.shields.io/badge/Focus-Network_Security-purple?style=flat-square)

Learn the basics of traffic analysis with Wireshark and how to find anomalies on your network!

**Link:** [TryHackMe Wireshark Traffic Analysis](https://tryhackme.com/room/wiresharktrafficanalysis)

> “In this room, we will cover the techniques and key points of traffic analysis with Wireshark and detect suspicious activities. Note that this is the third and last room of the Wireshark room trio, and it is suggested to visit the first two rooms stated below to practice and refresh your Wireshark skills before starting this one.”

> “In the first two rooms, we have covered how to use Wireshark and do packet-level searches. Now, it is time to investigate and correlate the packet-level information to see the big picture in the network traffic, like detecting anomalies and malicious activities. For a security analyst, it is vital to stop and understand pieces of information spread in packets by applying the analyst’s knowledge and tool functionality. This room will cover investigating packet-level details by synthesising the analyst knowledge and Wireshark functionality for detecting anomalies and odd situations for a given case.”

---

## Task 2: Nmap Scans

**File:** `Desktop/exercise-pcaps/nmap/Exercise.pcapng`

- **Total number of “TCP Connect” scans:** 1000  
  ![TCP Connect](https://github.com/user-attachments/assets/e3616045-c771-4ae3-a33b-422c6f2cf4d8)

- **Scan type used to scan TCP port 80:** TCP Connect  
  ![TCP Port 80](https://github.com/user-attachments/assets/012e3948-a94d-41ab-95e6-9f5ba8f19d94)

- **Number of “UDP close port” messages:** 1083  
  ![UDP Close](https://github.com/user-attachments/assets/5a66f9c5-1979-413a-ae94-db4949ba01d6)

- **Which UDP port in the 55–70 port range is open:** 68  
  ![UDP Port 68](https://github.com/user-attachments/assets/a2d05911-f351-4abf-881f-05552b6ff472)

---

## Task 3: ARP Poisoning & Man In The Middle

**File:** `Desktop/exercise-pcaps/arp/Exercise.pcapng`

- **Number of ARP requests crafted by the attacker:** 284  
  ![ARP Requests](https://github.com/user-attachments/assets/c96dbbf4-4012-4352-ad93-ae27402647df)

- **Attacker MAC address:** 00:0c:29:e2:18:b4  
  ![Attacker MAC](https://github.com/user-attachments/assets/d1ef7f6b-411c-4f71-9742-97c8e5042e19)

- **Number of HTTP packets received by the attacker:** 90  
  ![HTTP Packets](https://github.com/user-attachments/assets/ebb1389c-345f-4aa5-9cc9-dd8326840c11)

- **Number of sniffed username & password entries:** 6  
  ![Sniffed Credentials](https://github.com/user-attachments/assets/7f1a9eed-aacb-46b7-9644-8ae8acb04971)

- **Password of “Client986”:** clientnothere!  
  ![Client986 Password](https://github.com/user-attachments/assets/da243267-7222-42ed-b042-bd418f93c585)

- **Comment provided by “Client354”:** Nice work!  
  ![Client354 Comment](https://github.com/user-attachments/assets/89cb8358-6ffb-4aa8-8a95-c6d80b211db6)

---

## Task 4: Identifying Hosts: DHCP, NetBIOS and Kerberos

**Files:**  
- `Desktop/exercise-pcaps/dhcp-netbios-kerberos/dhcp-netbios.pcap`  
- `Desktop/exercise-pcaps/dhcp-netbios-kerberos/kerberos.pcap`

- **MAC address of host “Galaxy A30”:** 9a:81:41:cb:96:6c  
  ![Galaxy A30 MAC](https://github.com/user-attachments/assets/297c1077-0832-425c-bed6-d93058e343e7)

- **NetBIOS registration requests for “LIVALJM”:** 16  
  ![NBNS Requests](https://github.com/user-attachments/assets/28d44810-60bc-4e5a-858c-9ec0bb26ebdd)

- **Host requested IP 172.16.13.85:** Galaxy-A12  
  ![Requested IP](https://github.com/user-attachments/assets/e8502dc7-f81f-4bd4-a53c-0905c67d4b41)

- **IP address of user “u5” (defanged):** 10[.]1[.]12[.]2  
  ![u5 IP](https://github.com/user-attachments/assets/41b6f74e-812e-47da-9a97-bf65bee06da4)

- **Hostname of available host in Kerberos packets:** xp1$  
  ![Kerberos Host](https://github.com/user-attachments/assets/227722ca-7886-4a55-89ce-9dd105f49792)

---

## Task 5: Tunneling Traffic: DNS and ICMP

**Files:**  
- `Desktop/exercise-pcaps/dns-icmp/icmp-tunnel.pcap`  
- `Desktop/exercise-pcaps/dns-icmp/dns.pcap`

- **Protocol used in ICMP tunnelling:** SSH  
  ![ICMP Tunnel](https://github.com/user-attachments/assets/a5317845-cbd9-41f8-9c01-ac877c6db515)

- **Suspicious main domain address (defanged):** dataexfil[.]com  
  ![Suspicious DNS](https://github.com/user-attachments/assets/a8e8da55-6c6c-412f-97ba-62f6fc763ff0)

---

## Task 6: Cleartext Protocol Analysis: FTP

**File:** `Desktop/exercise-pcaps/ftp/ftp.pcap`

- **Incorrect login attempts:** 737  
  ![FTP Login Attempts](https://github.com/user-attachments/assets/280d2afe-4b01-4ca0-b98a-c4d4f1796d92)

- **Size of file accessed by “ftp” account:** 39424  
  ![FTP File Size](https://github.com/user-attachments/assets/f9a0a4e7-cf95-4eb9-9a8a-969d686804a2)

- **Filename uploaded:** resume.doc  
  ![Uploaded File](https://github.com/user-attachments/assets/116f2529-bfa4-420a-a052-780dcac80225)

- **Command used to change permissions:** CHMOD 777  
  ![CHMOD Command](https://github.com/user-attachments/assets/d255273f-c846-4ea5-8057-3231fb5f7a4f)

---

## Task 7: Cleartext Protocol Analysis: HTTP

**Files:**  
- `Desktop/exercise-pcaps/http/user-agent.cap`  
- `Desktop/exercise-pcaps/http/http.pcapng`

- **Number of anomalous “user-agent” types:** 6  
  ![Anomalous UA](https://github.com/user-attachments/assets/bcd73573-724b-4678-9521-bea9bed44478)

- **Packet number with subtle spelling difference in user-agent:** 52  
  ![User-Agent Packet](https://github.com/user-attachments/assets/8e1f6f8e-b9d1-4ec3-96d4-1873b9e0ddd3)

- **Log4j attack starting phase packet number:** 444  
  ![Log4j Attack](https://github.com/user-attachments/assets/ddf437b0-30ae-4e56-bea3-21b95d0af289)

- **IP contacted by adversary (defanged):** 62[.]210[.]130[.]250  
  ![Log4j IP](https://github.com/user-attachments/assets/22d78678-2f8c-4731-b2fa-ad8bcb675220)

---

## Task 8: Encrypted Protocol Analysis: Decrypting HTTPS

**File:** `Desktop/exercise-pcaps/https/Exercise.pcap`

- **Frame number of “Client Hello” message sent to accounts.google.com:** 16  
  ![Client Hello](https://github.com/user-attachments/assets/44afc8d4-c62f-419a-8141-0100209f2f6f)

- **Number of HTTP2 packets (decrypted):** 115  
  ![HTTP2 Packets](https://github.com/user-attachments/assets/0867f59d-7baf-4238-8b8c-69baf2eda557)

- **Authority header (defanged):** safebrowsing[.]googleapis[.]com  
  ![Authority Header](https://github.com/user-attachments/assets/ac55a0f2-46fc-4c2b-9bda-f896e0f92f2e)

- **Flag:** FLAG{THM-PACKETMASTER}  
  ![Flag](https://github.com/user-attachments/assets/d83af7ca-251c-4ace-9d7f-ce5593d1b8f9)

---

## Task 9 Bonus: Hunt Cleartext Credentials

**File:** `Desktop/exercise-pcaps/bonus/Bonus-exercise.pcap`

- **Packet number using HTTP Basic Auth:** 237  
  ![HTTP Basic Auth](https://github.com/user-attachments/assets/06ae9b80-123f-439a-b441-cc206a5c9745)

- **Packet number where “empty password” submitted:** 170  
  ![Empty Password](https://github.com/user-attachments/assets/be18e269-0bc5-43cc-9258-7888bb84d597)

---

## Task 10 Bonus: Actionable Results

**File:** `Desktop/exercise-pcaps/bonus/Bonus-exercise.pcap`

- **Deny source IPv4 address (packet 99):** `add deny ip from 10.121.70.151 to any in`  
  ![IP Deny](https://github.com/user-attachments/assets/098e1aed-f2b7-45d5-85d1-e1326f98dc9b)

- **Allow destination MAC address (packet 231):** `add allow MAC 00:d0:59:aa:af:80 any in`  
  ![MAC Allow](https://github.com/user-attachments/assets/1e2d02bc-b87a-4651-b0cd-fb49aada29fc)

---

## Conclusion

This room teaches **packet-level traffic analysis**, **anomaly detection**, **cleartext protocol investigation**, **encrypted traffic decryption**, and **network attack identification**. It highlights the importance of combining analyst knowledge with Wireshark functionality to detect malicious behavior, exfiltration attempts, and suspicious network activity.  

The exercises cover TCP/UDP scanning, ARP poisoning, Man-in-the-Middle attacks, DHCP/NetBIOS/Kerberos host identification, tunneling traffic, FTP/HTTP/HTTPS analysis, and practical firewall rules implementation.

