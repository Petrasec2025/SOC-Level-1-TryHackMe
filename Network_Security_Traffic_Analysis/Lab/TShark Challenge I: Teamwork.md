# TShark Challenge I: Teamwork | TryHackMe Walkthrough

![TryHackMe](https://img.shields.io/badge/TryHackMe-TShark%20Challenge%20I%3A%20Teamwork-red) 
![Difficulty](https://img.shields.io/badge/Difficulty-Easy-green) 
![Category](https://img.shields.io/badge/Category-Forensics-blue) 
![Time](https://img.shields.io/badge/Time-30%20minutes-orange)

## Scenario
An alert has been triggered: "The threat research team discovered a suspicious domain that could be a potential threat to the organisation."

The case was assigned to you. Inspect the provided teamwork.pcap located in `~/Desktop/exercise-files` and create artefacts for detection tooling.

## Tasks

### Task 1: What is the full URL of the malicious/suspicious domain address?

To identify the full URL of the malicious or suspicious domain address, we first navigate to the `/desktop/exercise-files` directory, where the .pcap file is located. This file contains the captured network traffic data that we need to analyze.

Next, we execute this command in the terminal:

```bash
tshark -r teamwork.pcap -T fields -e http.host | sort -r | uniq
```

This command uses TShark, a network protocol analyzer, to read the teamwork.pcap file. The `-T fields` option specifies that we want to extract specific fields from the packet data, and `-e http.host` indicates that we are interested in the HTTP host field. The `sort -r | uniq` part of the command sorts the output in reverse order and removes duplicate entries, providing us with a unique list of HTTP hosts found in the capture file.

![HTTP Host Extraction](https://github.com/user-attachments/assets/c68f111e-7ca9-4e5a-9aad-ed91534be899)

Upon executing the command, we observe from the image above that the output includes the host `https://www.paypal.com4uswebappsresetaccountrecovery.timeseaways.com/`. This URL is identified as the suspicious domain address we were looking for. It is crucial to note that this URL mimics a legitimate PayPal address but includes additional, suspicious elements that indicate it is likely used for phishing or other malicious activities. Therefore, this URL is the answer to our query.

**Answer:** `hxxp[://]www[.]paypal[.]com4uswebappsresetaccountrecovery[.]timeseaways[.]com/`

### Task 2: When was the URL of the malicious/suspicious domain address first submitted to VirusTotal?

We start by navigating to VirusTotal and entering the suspicious URL we previously identified.

![VirusTotal Search](https://github.com/user-attachments/assets/9b045c6a-0eab-47cd-a986-8ed0717fbb3a)

Once the search results load, we proceed to the details section.

![VirusTotal Details](https://github.com/user-attachments/assets/d092f7a0-8069-42fc-bd9d-d09c637df218)

Here, we find the information we need: the URL of the malicious domain was first submitted to VirusTotal on April 17, 2017, at 22:52:53 UTC.

**Answer:** `2017-04-17 22:52:53 UTC`

### Task 3: Which known service was the domain trying to impersonate?

From the URL, it is clear that the domain is attempting to impersonate PayPal. The structure of the URL, particularly the use of "paypal.com" within the subdomain, is designed to deceive users into believing they are accessing a legitimate PayPal service.

**Answer:** `PayPal`

### Task 4: What is the IP address of the malicious domain?

To determine the IP address of the malicious domain, we start by executing the command:

```bash
tshark -r teamwork.pcap -T fields -e dns.qry.name -e dns.a | sort -u
```

This command reads the packet capture file teamwork.pcap and extracts DNS query names and their corresponding IP addresses. By using the `sort -u` option, we ensure that the output is sorted and unique, eliminating any duplicate entries.

![DNS Query Extraction](https://github.com/user-attachments/assets/f2d9a0d4-d295-4ee5-a481-28bcd3e07865)

Upon reviewing the output, we identify the IP address associated with the malicious domain as 184.154.127.226.

**Answer:** `184[.]154[.]127[.]226`

### Task 5: What is the email address that was used?

To determine the email address used in the packet capture file, we execute the command:

```bash
tshark -r teamwork.pcap -V | grep -Eo '[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}'
```

This command reads the packet capture file teamwork.pcap and displays detailed information about each packet. The `-r` option specifies the file to read from, and the `-V` option provides a verbose output, showing all the details of each packet. We then pipe this output to grep, which uses a regular expression to search for and extract email addresses from the detailed packet information.

![Email Extraction](https://github.com/user-attachments/assets/7ef0fd2d-f6e7-4eb2-b9bf-9ae361a6278b)

From the output, we identify the email address johnny5alive@gmail.com.

**Answer:** `johnny5alive[at]gmail[.]com`

## Conclusion

This challenge demonstrated practical forensic analysis skills using TShark to investigate a potential phishing campaign. Key findings included:

- Identification of a suspicious domain impersonating PayPal
- Extraction of the malicious IP address (184.154.127.226)
- Discovery of an associated email address (johnny5alive@gmail.com)
- Verification of the domain's submission history on VirusTotal

The analysis revealed a classic phishing attempt where attackers used a deceptive URL structure to mimic a legitimate PayPal service, potentially aiming to steal user credentials. The techniques used in this investigation are essential for security analysts to quickly identify and respond to potential threats in network traffic.

![Completion Badge](https://img.shields.io/badge/Challenge-Completed-brightgreen) 
![Skills](https://img.shields.io/badge/Skills-Forensics%2C%20Network%20Analysis%2C%20Threat%20Hunting-success)
