<img width="1426" height="273" alt="Screenshot 2025-09-27 at 1 15 15 AM" src="https://github.com/user-attachments/assets/396d9933-f323-4eb6-bd6d-082139e76682" />

Scenario
An alert has been triggered: "The threat research team discovered a suspicious domain that could be a potential threat to the organisation."

The case was assigned to you. Inspect the provided teamwork.pcap located in ~/Desktop/exercise-files and create artefacts for detection tooling.

Tasks
1. What is the full URL of the malicious/suspicious domain address?

To identify the full URL of the malicious or suspicious domain address, we first navigate to the /desktop/exercise-files directory, where the .pcap file is located. This file contains the captured network traffic data that we need to analyze.

Next, we execute this command in the terminal: 

Copy
tshark -r teamwork.pcap -T fields -e http.host | sort -r | uniq.
This command uses TShark, a network protocol analyzer, to read the teamwork.pcap file. 

The -T fields option specifies that we want to extract specific fields from the packet data, and -e http.host indicates that we are interested in the HTTP host field. The sort -r | uniq part of the command sorts the output in reverse order and removes duplicate entries, providing us with a unique list of HTTP hosts found in the capture file.
<img width="754" height="501" alt="Screenshot 2025-09-27 at 1 16 41 AM" src="https://github.com/user-attachments/assets/c68f111e-7ca9-4e5a-9aad-ed91534be899" />
Upon executing the command, we observe from the image above that the output includes the host https://www.paypal.com4uswebappsresetaccountrecovery.timeseaways.com/. This URL is identified as the suspicious domain address we were looking for. 

It is crucial to note that this URL mimics a legitimate PayPal address but includes additional, suspicious elements that indicate it is likely used for phishing or other malicious activities. Therefore, this URL is the answer to our query.

hxxp[://]www[.]paypal[.]com4uswebappsresetaccountrecovery[.]timeseaways[.]com/

2. When was the URL of the malicious/suspicious domain address first submitted to VirusTotal?

We start by navigating to VirusTotal and entering the suspicious URL we previously identified. 
<img width="562" height="567" alt="Screenshot 2025-09-27 at 1 16 49 AM" src="https://github.com/user-attachments/assets/9b045c6a-0eab-47cd-a986-8ed0717fbb3a" />
Once the search results load, we proceed to the details section. 
<img width="766" height="427" alt="Screenshot 2025-09-27 at 1 16 56 AM" src="https://github.com/user-attachments/assets/d092f7a0-8069-42fc-bd9d-d09c637df218" />
Here, we find the information we need: the URL of the malicious domain was first submitted to VirusTotal on April 17, 2017, at 22:52:53 UTC. 

2017-04-17 22:52:53 UTC

3. Which known service was the domain trying to impersonate?

From the URL, it is clear that the domain is attempting to impersonate PayPal. 

The structure of the URL, particularly the use of “paypal.com” within the subdomain, is designed to deceive users into believing they are accessing a legitimate PayPal service. 

PayPal

4. What is the IP address of the malicious domain?

To determine the IP address of the malicious domain, we start by executing the command:

Copy
tshark -r teamwork.pcap -T fields -e dns.qry.name -e dns.a | sort -u
This command reads the packet capture file teamwork.pcap and extracts DNS query names and their corresponding IP addresses. By using the sort -u option, we ensure that the output is sorted and unique, eliminating any duplicate entries.
<img width="759" height="496" alt="Screenshot 2025-09-27 at 1 17 08 AM" src="https://github.com/user-attachments/assets/f2d9a0d4-d295-4ee5-a481-28bcd3e07865" />
Upon reviewing the output, we identify the IP address associated with the malicious domain as 184.154.127.226. 

184[.]154[.]127[.]226

5. What is the email address that was used?

To determine the email address used in the packet capture file, we execute the command 

Copy
tshark -r teamwork.pcap -V | grep -Eo '[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}' 
This command reads the packet capture file teamwork.pcap and displays detailed information about each packet. The -r option specifies the file to read from, and the -V option provides a verbose output, showing all the details of each packet. We then pipe this output to grep, which uses a regular expression to search for and extract email addresses from the detailed packet information.
<img width="756" height="484" alt="Screenshot 2025-09-27 at 1 17 16 AM" src="https://github.com/user-attachments/assets/7ef0fd2d-f6e7-4eb2-b9bf-9ae361a6278b" />
From the output, we identify the email address johnny5alive@gmail.com.

johnny5alive[at]gmail[.]com
