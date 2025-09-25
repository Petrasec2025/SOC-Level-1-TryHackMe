“In this room, we will cover the fundamentals of packet analysis with Wireshark and investigate the event of interest at the packet-level. Note that this is the second room of the Wireshark room trio, and it is suggested to visit the first room (Wireshark: The Basics) to practice and refresh your Wireshark skills before starting this one.”

My tryhackme for the Wireshark: The Basics is found here
https://tryhackme.com/p/Petras20/https://tryhackme.com/room/wiresharkpacketoperations/
Task 2: Statistics | Summary
Investigate the resolved addresses. What is the IP address of the hostname starts with “bbc”?

Ans: 199.232.24.81

Go to Statistic then Resolved Addresses. Filter by typing the strings of the host name that we are after.

<img width="686" height="409" alt="Screenshot 2025-09-25 at 4 03 43 PM" src="https://github.com/user-attachments/assets/3cb9f6c9-ab64-4d75-b386-17292c29a323" />

What is the number of IPv4 conversations?

Ans: 435

Go to Statistics then Conversations. IPv4 column contains all IPv4 conversations.

<img width="687" height="369" alt="Screenshot 2025-09-25 at 4 05 56 PM" src="https://github.com/user-attachments/assets/1da1cb6e-a945-4bad-97ad-ae68e50a8f66" />

How many bytes (k) were transferred from the “Micro-St” MAC address?

Ans: 7474

Go to Statistics then Endpoint.
<img width="689" height="178" alt="Screenshot 2025-09-25 at 4 06 37 PM" src="https://github.com/user-attachments/assets/26351b05-ba03-41b2-b6d5-5a4326a33dc3" />
Click the Name resolution to resolve host names of the endpoints.
<img width="675" height="357" alt="Screenshot 2025-09-25 at 4 09 47 PM" src="https://github.com/user-attachments/assets/c8653cff-824f-42f9-9c90-cf8a5bde0f18" />
What is the number of IP addresses linked with “Kansas City”?

Ans: 4

Still on Endpoints, go to IPv4 tab then “City” column
<img width="683" height="192" alt="Screenshot 2025-09-25 at 4 10 01 PM" src="https://github.com/user-attachments/assets/8332d58c-b119-4f46-94d0-683dbe7e5862" />
Which IP address is linked with “Blicnet” AS Organisation?

Ans: 188.246.82.7

Still on Endpoint, go to “As Organization” Column

Press enter or click to view image in full size
<img width="683" height="127" alt="Screenshot 2025-09-25 at 4 10 09 PM" src="https://github.com/user-attachments/assets/ade5d1cf-9f44-44f8-a972-aeab5f23a000" />
Task 3: Statistics | Protocol Details
What is the most used IPv4 destination address?

Ans:10.100.1.33

Go to Statistics then IPV4 Statistics then All Addresses. Sort it by Count.
<img width="680" height="536" alt="Screenshot 2025-09-25 at 4 10 19 PM" src="https://github.com/user-attachments/assets/4132fc31-49dd-43aa-bde9-e2013ea4ca95" />
<img width="643" height="89" alt="Screenshot 2025-09-25 at 4 10 27 PM" src="https://github.com/user-attachments/assets/9034c3d3-c67a-4a44-b71c-53103c8c334c" />
What is the max service request-response time of the DNS packets?

Ans: 0.467897

Go to Statistics then DNS.
<img width="674" height="471" alt="Screenshot 2025-09-25 at 4 10 35 PM" src="https://github.com/user-attachments/assets/31354883-f7cd-48d5-9fab-95c73cf1e27c" />
<img width="679" height="145" alt="Screenshot 2025-09-25 at 4 10 45 PM" src="https://github.com/user-attachments/assets/d43d8b3c-3af2-4ce2-9ab0-60f037606a03" />
What is the number of HTTP Requests accomplished by “rad[.]msn[.]com?

Ans: 39

Go to Statistics then HTTP then Requests.
<img width="676" height="470" alt="Screenshot 2025-09-25 at 4 10 54 PM" src="https://github.com/user-attachments/assets/583cda2a-0069-4a1b-94d0-a5ca429b09a0" />
Look for the domain name and scroll all the way to the right.
<img width="559" height="218" alt="Screenshot 2025-09-25 at 4 11 03 PM" src="https://github.com/user-attachments/assets/567d1188-23cf-4941-b449-ac7620ef7fc8" />
<img width="587" height="235" alt="Screenshot 2025-09-25 at 4 11 10 PM" src="https://github.com/user-attachments/assets/dcac9bb8-5523-4775-89ef-d1879ae0d2ba" />

Task 5: Packet Filtering | Protocol Filters
What is the number of IP packets?

Ans: 84120

Filter out only packets with ip

<img width="678" height="81" alt="Screenshot 2025-09-25 at 4 11 21 PM" src="https://github.com/user-attachments/assets/73b30240-4df9-4737-8abc-1e21bbdd96ef" />
<img width="677" height="475" alt="Screenshot 2025-09-25 at 4 11 28 PM" src="https://github.com/user-attachments/assets/4dbca361-4454-436f-a550-048950d051b3" />
What is the number of packets with a “TTL value less than 10”?

Ans: 66
<img width="677" height="76" alt="Screenshot 2025-09-25 at 4 11 38 PM" src="https://github.com/user-attachments/assets/2e95539d-38cd-487b-926c-a9d59dac3230" />
<img width="678" height="474" alt="Screenshot 2025-09-25 at 4 11 46 PM" src="https://github.com/user-attachments/assets/642551c3-1b79-4788-9bff-37a2e23d8cd2" />
What is the number of packets which uses “TCP port 4444”?

Ans: 632
<img width="681" height="83" alt="Screenshot 2025-09-25 at 4 11 57 PM" src="https://github.com/user-attachments/assets/762f3bf0-c7ef-4d43-b6ee-53d28f72bf55" />
<img width="681" height="470" alt="Screenshot 2025-09-25 at 4 12 08 PM" src="https://github.com/user-attachments/assets/c4a6f7d4-3307-4c45-9f98-8225f1c0d187" />

What is the number of “HTTP GET” requests sent to port “80”?

Ans: 527

This filter joins two filters together. This filters out only “GET” http request method that uses tcp port 80.
<img width="679" height="78" alt="Screenshot 2025-09-25 at 4 22 59 PM" src="https://github.com/user-attachments/assets/7f7627cf-1149-4156-89f0-f82849886b8b" />
<img width="682" height="467" alt="Screenshot 2025-09-25 at 4 12 17 PM" src="https://github.com/user-attachments/assets/6b4d495b-fd97-41db-b77e-aa31f7393540" />

What is the number of “type A DNS Queries”?

Ans: 51

Let’s build a filter using the Display Filter Expression under the Analyze menu.
<img width="578" height="203" alt="Screenshot 2025-09-25 at 4 24 45 PM" src="https://github.com/user-attachments/assets/f00ac1d6-d35f-4fff-a61a-b0cd50dd033c" />

Search for dns then select dns.query.type A then click Ok.
<img width="556" height="570" alt="Screenshot 2025-09-25 at 4 24 52 PM" src="https://github.com/user-attachments/assets/5925b78b-b52f-47b8-b247-2804786c137a" />
Let’s add another filter to show all DNS responses

<img width="551" height="573" alt="Screenshot 2025-09-25 at 4 25 01 PM" src="https://github.com/user-attachments/assets/f07605f6-4281-4922-a702-bda21b77b198" />
<img width="677" height="77" alt="Screenshot 2025-09-25 at 4 25 09 PM" src="https://github.com/user-attachments/assets/b8dcb2dc-9fc4-4887-b08d-978ec7b6b4bf" />
<img width="679" height="380" alt="Screenshot 2025-09-25 at 4 25 17 PM" src="https://github.com/user-attachments/assets/f12cd0b8-b341-4b6d-a204-d306473b15e6" />
Task 6: Advanced Filtering
Find all Microsoft IIS servers. What is the number of packets that did not originate from “port 80”?

Ans: 21

This filters all http servers that contains the string “IIS” but excluding packets from source port 80.
<img width="787" height="544" alt="Screenshot 2025-09-25 at 4 25 26 PM" src="https://github.com/user-attachments/assets/23849c32-0cb0-4ad7-b415-c39f62f37302" />

Find all Microsoft IIS servers. What is the number of packets that have “version 7.5”?

Ans: 71

The following filters all http server that contains “IIS” and matches the string “7.5”.
<img width="772" height="552" alt="Screenshot 2025-09-25 at 4 25 36 PM" src="https://github.com/user-attachments/assets/88e10265-838f-4630-b7aa-e1a498e41343" />
What is the total number of packets that use ports 3333, 4444 or 9999?

Ans: 2235

Use curly braces and put spaces between strings.


<img width="784" height="563" alt="Screenshot 2025-09-25 at 4 25 43 PM" src="https://github.com/user-attachments/assets/0e0e3ae5-55f8-457b-98ef-94357e6e6dca" />
What is the number of packets with “even TTL numbers”?

Ans: 77289

What this filter does is, it will convert all ip.ttl fields to string values, and list ttl values only with even numbers.

<img width="753" height="575" alt="Screenshot 2025-09-25 at 4 25 50 PM" src="https://github.com/user-attachments/assets/cfe6a30f-3ec3-4028-8e69-76cd5b8cb114" />

Change the profile to “Checksum Control”. What is the number of “Bad TCP Checksum” packets?

Ans: 34185

Go to Edit then Configuration Profiles. Select the “Checksum Control” profile listed.
<img width="600" height="590" alt="Screenshot 2025-09-25 at 4 26 00 PM" src="https://github.com/user-attachments/assets/a7f12e64-bf53-4dab-93b8-64a8f3896004" />
We will then open the Display Filter Expression window and create a filter for a bad tcp checksum.

<img width="652" height="572" alt="Screenshot 2025-09-25 at 4 26 16 PM" src="https://github.com/user-attachments/assets/32a61675-bbf9-452b-8e83-7f278c01fb0f" />
<img width="643" height="58" alt="Screenshot 2025-09-25 at 4 26 30 PM" src="https://github.com/user-attachments/assets/ca170410-ef31-41b9-b150-d46b00adc000" />
<img width="678" height="436" alt="Screenshot 2025-09-25 at 4 26 41 PM" src="https://github.com/user-attachments/assets/843210aa-0fd9-40f6-b13e-2c0258c6db01" />

Use the existing filtering button to filter the traffic. What is the number of displayed packets?

Ans: 261

Click the button for the “Checksum Control” profile and it will populate the filter with the built-in filter.

<img width="678" height="378" alt="Screenshot 2025-09-25 at 4 26 52 PM" src="https://github.com/user-attachments/assets/8cd06e92-4b8d-4e97-b0b9-678d53aea02e" />
conclusion
