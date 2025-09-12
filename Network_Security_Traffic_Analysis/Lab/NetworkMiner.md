# NetworkMiner Walkthrough - TryHackMe

## Getting VM Started
Go back to Task 1, at the top of the task is a green button labeled **Start Machine**. Click the green button to start the VM.

![Show Split View](https://github.com/user-attachments/assets/476ef3b8-a7ee-4869-a0fa-f9b138669af7)


If the screen doesn’t split in half with the VM on the right and Tasks on the left, scroll to the top of the page. You will see a blue button labeled **Show Split View**, click this button to split the screen.


![Start Machine](https://github.com/user-attachments/assets/84e1aed9-07f0-4bbf-b455-ca709d123b2a)

Time to open **NetworkMiner**, double-click on the `NetworkMiner_2–7–2` folder.

![Open NetworkMiner Folder](https://github.com/user-attachments/assets/6d0bfec6-7842-47c3-bd42-3559908d3acb)

When the directory opens, double-click on `NetworkMiner.exe`, then give it time to open.

![NetworkMiner Executable](https://github.com/user-attachments/assets/336dd852-2960-4e4c-bfee-2a49124a10c8)

NetworkMiner will open. You are now ready to go along with this Task.

![NetworkMiner Open](https://github.com/user-attachments/assets/b0ed3248-c31c-4174-82ea-0003c9aebdb1)

---

## Task 5 Tool Overview 2

### Files
The **Files** menu shows extracted files from investigated pcaps. This section provides information on:

- Frame number  
- Filename  
- Extension  
- Size  
- Source and destination address  
- Source and destination port  
- Protocol  
- Timestamp  
- Reconstructed path  

Some features (OSINT hash lookup and sample submission) are available only in premium mode. The search bar is available here as well. The right-click menu is helpful in this part as well. You can easily open files and folders and view the file details in-depth.

![Files Menu](https://github.com/user-attachments/assets/fffaa2b7-244c-4ad5-b050-21d1dafafae3)

### Images
The **Images** menu shows extracted images from investigated pcaps. The right-click menu is helpful in this part as well. You can open files and zoom in & out easily.

![Images Menu](https://github.com/user-attachments/assets/8320aeb5-1351-4ef2-b718-ed99bde41c36)

Hovering over the image shows detailed information (source & destination address and file path).

![Image Details](https://github.com/user-attachments/assets/c7ddc110-c972-42af-95ce-c87a2c2c01b0)

### Parameters
The **Parameters** menu shows extracted parameters from investigated pcaps. This section provides information on:

- Parameter name  
- Parameter value  
- Frame number  
- Source and destination host  
- Source and destination port  
- Timestamp  

The right-click menu is helpful; you can copy the parameters and values easily.

![Parameters Menu](https://github.com/user-attachments/assets/6e5a08d7-74b2-4118-8c67-fef89645706c)

### Keywords
The **Keywords** menu shows extracted keywords from investigated pcaps. This section provides information on:

- Frame number  
- Timestamp  
- Keyword  
- Context  
- Source and destination host  
- Source and destination port  

**Filtering Keywords**:

- Add keywords  
- Reload case files  

> Note: You must reload the case files after updating the search keywords.

![Keywords Menu](https://github.com/user-attachments/assets/53c02af9-ddb8-411d-9009-60312d01b979)

### Messages
The **Messages** menu shows extracted emails, chats, and messages from investigated pcaps. This section provides information on:

- Frame number  
- Source and destination host  
- Protocol  
- Sender (From)  
- Receiver (To)  
- Timestamp  
- Size  

Filtered traffic may reveal attachments and attributes. Use the built-in viewer to investigate overall information.

### Anomalies
The **Anomalies** menu shows detected anomalies in the processed pcap. NetworkMiner isn’t designated as an IDS but includes detections for EternalBlue exploit and spoofing attempts.

![Anomalies Menu](https://github.com/user-attachments/assets/c4ad3221-85ea-466d-849b-f8421eb49184)

---

## Task 6 Version Differences

### Mac Address Processing
NetworkMiner versions after v2 can process MAC address specific correlation to identify MAC Address conflicts. This feature is not available before version 2.

![MAC Address Processing](https://github.com/user-attachments/assets/1fc7598a-a79f-490f-92db-2da3126f4e52)

### Sent/Received Packet Processing
NetworkMiner up to v1.6 can handle packets in detail. This feature is not available after v1.6.

![Packet Processing](https://github.com/user-attachments/assets/190a7a0c-71ca-48bd-b14d-b525a13130e0)

### Frame Processing
NetworkMiner up to v1.6 can handle frames. Not available after v1.6.

![Frame Processing](https://github.com/user-attachments/assets/b34c278c-db13-4135-b8be-7e93c5bc3c92)

### Parameter Processing
NetworkMiner after v2 can handle parameters more extensively. Version 1.6 catches fewer parameters.

![Parameter Processing](https://github.com/user-attachments/assets/71e38644-1040-480e-be34-879e21ac9aaf)

### Cleartext Processing
NetworkMiner up to v1.6 can handle cleartext data. This feature is not available after v1.6.

![Cleartext Processing](https://github.com/user-attachments/assets/26cc01dc-8e42-43eb-b2c3-fb6433cf90e5)

---

## Task 7: Exercises

### Use case1.pcap
- **OS name of host 131.151.37.122:** Windows – Windows NT 4  
- **Data bytes from 131.151.32.91 to 131.151.37.122 through port 1065:** 192  
- **Data bytes from 131.151.37.122 to 131.151.32.21 through port 143:** 20769  
- **Sequence number of frame 9:** 2AD77400  
- **Number of detected “content types”:** 2  

### Use case2.pcap
- **USB product’s brand name:** www.asix.com.tw  
- **Phone model:** Lumia 535  
- **Source IP of fish image:** 50.22.95.9  
- **Password of homer.pwned.se@gmx.com:** spring2015  
- **DNS Query of frame 62001:** pop.gmx.com  

---

## Task 8: Conclusion
Congratulations! You just finished the NetworkMiner room.  

**Key takeaways:**

- Don’t use NetworkMiner as a primary sniffer.  
- Use it to overview the traffic, then move forward with Wireshark and tcpdump for in-depth investigation.  
- For further study, visit rooms like Wireshark, Snort, and Brim on TryHackMe.  

---

**Congratulations on completing NetworkMiner!!!**  

![Completion](https://github.com/user-attachments/assets/56fe8518-fd34-4005-947d-ba2183ae5290)

