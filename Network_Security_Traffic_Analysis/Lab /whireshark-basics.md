
<img width="1358" height="269" alt="Screenshot 2025-09-25 at 3 23 41 PM" src="https://github.com/user-attachments/assets/98da139e-c7be-4030-b182-096c6c02c413" />


Wireshark is an open-source, cross-platform network packet analyser tool capable of sniffing and investigating live traffic and inspecting packet captures (PCAP). It is commonly used as one of the best packet analysis tools. In this room, we will look at the basics of Wireshark and use it to perform fundamental packet analysis.

Press the Start Machine button below.

Start Machine
The machine will start in Split-Screen view. If it is not visible, use the blue Show Split View button at the top of the page.

Note: A VM is attached to this room. You don’t need SSH or RDP; the room provides a “Split View” feature. We suggest completing the Networking module before starting working in this room.

There are two capture files given in the VM. You can use the “http1.pcapng” file to simulate the actions shown in the screenshots. Please note that you need to use the “Exercise.pcapng”file to answer the questions.
<img width="681" height="621" alt="Screenshot 2025-09-25 at 3 28 46 PM" src="https://github.com/user-attachments/assets/9ab81c69-a1d6-46a1-99fa-4309a5080ac9" />

Answer: http1.pcapng

1.2 Which file is used to answer the questions?

There are two capture files given in the VM. You can use the “http1.pcapng” file to simulate the actions shown in the screenshots. Please note that you need to use the “Exercise.pcapng” file to answer the questions.

<img width="674" height="604" alt="Screenshot 2025-09-25 at 3 30 11 PM" src="https://github.com/user-attachments/assets/51ca72b7-87d8-4fb0-a0cb-8782e3bd5d83" />

Answer: Exercise.pcapng

Task 2 Tool Overview

Use the “Exercise.pcapng” file to answer the questions.

Read the “capture file comments”.

What is the flag?

Ans: TryHackMe_Wireshark_Demo

Open the pcap file and open the capture file properties dialog on the bottom left-side of the status bar.
<img width="656" height="253" alt="Screenshot 2025-09-25 at 3 36 36 PM" src="https://github.com/user-attachments/assets/b6ac08e5-b929-4727-8353-7fdc77319b98" />
<img width="643" height="569" alt="Screenshot 2025-09-25 at 3 36 47 PM" src="https://github.com/user-attachments/assets/0ed8ce47-af44-4c89-9ba6-3903ba610aa0" />

What is the total number of packets?

Ans: 58620

What is the SHA256 hash value of the capture file?

Ans: f446de335565fb0b0ee5e5a3266703c778b2f3dfad7efeaeccb2da5641a6d6eb
<img width="627" height="720" alt="Screenshot 2025-09-25 at 3 38 23 PM" src="https://github.com/user-attachments/assets/08da9ae6-953b-4624-a215-e57e303daedc" />
Task 3: Packet Dissection
Use the “Exercise.pcapng” file to answer the questions.

View packet number 38. Which markup language is used under the HTTP protocol?

Ans: eXtensible Markup Language

Press ctrl+g. That will open a dialog box to find specific packets, then enter 38 and click the button. We should be directed to packet 38.
<img width="672" height="184" alt="Screenshot 2025-09-25 at 3 38 34 PM" src="https://github.com/user-attachments/assets/370944af-81b9-42ed-8c98-3b5eae7f76e3" />
Within the packet details pane, under the HTTP protocol is the Markup Language used.
<img width="677" height="134" alt="Screenshot 2025-09-25 at 3 38 42 PM" src="https://github.com/user-attachments/assets/0adf0f0b-5ee4-418c-b294-76e0cda258a6" />
What is the arrival date of the packet? (Answer format: Month/Day/Year)

Ans: 05/13/2004

Still on packet 38, expand the Frame and it will show the details specific to the Physical layer of the OSI model.
<img width="637" height="182" alt="Screenshot 2025-09-25 at 3 38 51 PM" src="https://github.com/user-attachments/assets/257f24da-a9a2-478e-8497-1a56e8d95cb4" />
What is the TTL value?

Ans: 47

The TTL value is found in Layer 3 of the OSI model, which is the Network Layer. Expand the Internet Protocol within the packet details pane.
<img width="677" height="295" alt="Screenshot 2025-09-25 at 3 39 00 PM" src="https://github.com/user-attachments/assets/50b4f136-44b5-472e-a5bb-69c52dba49ed" />
What is the TCP payload size?

Ans: 424

TCP details are found within the Transmission Control Protocol pane, which is the 4th layer of the OSI model.
<img width="686" height="378" alt="Screenshot 2025-09-25 at 3 39 10 PM" src="https://github.com/user-attachments/assets/27e7983e-b657-4ddb-8243-3f4fc454bf6e" />
What is the e-tag value?

Ans: 9a01a-4696–7e354b00

This particular value is found in Hypertext Transfer Protocol pane, from the Application protocol layer of the OSI model.

<img width="607" height="310" alt="Screenshot 2025-09-25 at 3 39 19 PM" src="https://github.com/user-attachments/assets/9416a2dc-3912-4823-be28-7e024927d791" />

Task 4: Packet Navigation
Use the “Exercise.pcapng” file to answer the questions.

Search the “r4w” string in packet details. What is the name of artist 1?

Ans: r4w8173

Press ctrl+f to search for the string inside the packets.
<img width="680" height="134" alt="Screenshot 2025-09-25 at 3 39 30 PM" src="https://github.com/user-attachments/assets/b7153b81-ef70-4c40-876e-d4e0ab6167e0" />

Within the details pane is the name of artist 1.

<img width="677" height="121" alt="Screenshot 2025-09-25 at 3 39 45 PM" src="https://github.com/user-attachments/assets/8914a401-1432-4eff-962a-b279eda92348" />

Go to packet 12 and read the comments. What is the answer?

Ans: 911cd574a42865a956ccde2d04495ebf

Press ctrl+g and enter the packet number and we will be directed to that packet.
<img width="682" height="347" alt="Screenshot 2025-09-25 at 3 39 56 PM" src="https://github.com/user-attachments/assets/e1815ace-f6e9-412b-a9f4-fdf74f64a606" />
We see that there is a comment in the details pane but it is incomplete. To read the full comment, we will go to Edit menu then select Packet Comment.
<img width="400" height="262" alt="Screenshot 2025-09-25 at 3 40 05 PM" src="https://github.com/user-attachments/assets/c0768a84-32c8-4f0c-9888-eeafab04be73" />
Upon reading the comment, we will go to packet 39765, look at the packet details pane and export the packet bytes by right-clicking on the JPEG section. As stated, this is another way of extracting data or objects from a pcap file. I saved the JPEG file as “jpeg” in the Desktop directory.
<img width="686" height="658" alt="Screenshot 2025-09-25 at 3 40 17 PM" src="https://github.com/user-attachments/assets/83497ec9-f91b-4e95-8069-8c95cd7cd5b4" />
<img width="675" height="125" alt="Screenshot 2025-09-25 at 3 40 44 PM" src="https://github.com/user-attachments/assets/f4c34b87-d95b-4943-851a-08448f1589df" />
Open a terminal and we will extract the MD5 hash value of the image.
<img width="453" height="81" alt="Screenshot 2025-09-25 at 3 40 54 PM" src="https://github.com/user-attachments/assets/019cdde8-396d-4afe-b81f-6c52b323a2a1" />
There is a “.txt” file inside the capture file. Find the file and read it; what is the alien’s name?

Ans: PACKETMASTER

This is another method of exporting objects from a pcap file. Go to File menu then select Export Objects and then HTTP (or whatever protocol that may have been used to transfer objects). Save the “note.txt” file.
<img width="509" height="490" alt="Screenshot 2025-09-25 at 3 41 03 PM" src="https://github.com/user-attachments/assets/825fa79c-85f3-4ff0-a052-3ba927023ed2" />
<img width="628" height="462" alt="Screenshot 2025-09-25 at 3 41 13 PM" src="https://github.com/user-attachments/assets/c37fc37c-d4d0-46f7-96cf-c6d01f3e7a3b" />
<img width="502" height="139" alt="Screenshot 2025-09-25 at 3 41 21 PM" src="https://github.com/user-attachments/assets/b0f26162-4641-4fa4-9033-5ace8ac0b98a" />
We can actually read the contents of the text file on the details pane but the objective of this task is for us to learn how to export objects.
<img width="679" height="524" alt="Screenshot 2025-09-25 at 3 41 29 PM" src="https://github.com/user-attachments/assets/6747b546-43f0-4675-bdd0-130f820fc27d" />
Open and read the contents of the file. We can use a text editor or terminal to read the contents.
<img width="628" height="529" alt="Screenshot 2025-09-25 at 3 41 37 PM" src="https://github.com/user-attachments/assets/4d19cc21-a86c-4b54-94e5-5c6351987bee" />
Look at the expert info section. What is the number of warnings?

Ans: 1636

We can either go to Analyze Menu then select Expert Information or at the bottom left part of the status bar and click on the first image.

<img width="683" height="443" alt="Screenshot 2025-09-25 at 3 41 45 PM" src="https://github.com/user-attachments/assets/e178aaae-338d-41e0-a7c9-f14327af8222" />
<img width="637" height="213" alt="Screenshot 2025-09-25 at 3 41 53 PM" src="https://github.com/user-attachments/assets/3729fb6f-9555-4408-8591-94deb89ee869" />
Task 5: Packet Filtering
Go to packet number 4. Right-click on the “Hypertext Transfer Protocol” and apply it as a filter. Now, look at the filter pane. What is the filter query?

Ans: http

Press ctrl+g and enter packet number 4. Follow the instructions provided then look at the Display filter of what filter has been applied.
<img width="636" height="631" alt="Screenshot 2025-09-25 at 3 42 01 PM" src="https://github.com/user-attachments/assets/b48d966f-8c69-4783-a80f-b169e18beb54" />
<img width="677" height="304" alt="Screenshot 2025-09-25 at 3 42 10 PM" src="https://github.com/user-attachments/assets/16914757-b28b-4c08-84b5-ce3dbe5d125b" />
What is the number of displayed packets?

Ans: 1089

It is displayed at the bottom right-side of the status bar.
<img width="473" height="40" alt="Screenshot 2025-09-25 at 3 42 33 PM" src="https://github.com/user-attachments/assets/d5a0062c-b75f-48ce-b3a1-ada7b152e049" />
Go to packet number 33790 and follow the stream. What is the total number of artists?

Ans: 3

<img width="628" height="329" alt="Screenshot 2025-09-25 at 3 42 43 PM" src="https://github.com/user-attachments/assets/7070f4b9-c0f9-4ae7-b8c7-be04bc5e205b" />
<img width="681" height="586" alt="Screenshot 2025-09-25 at 3 42 54 PM" src="https://github.com/user-attachments/assets/50ed3458-c2d2-4e21-b838-8894440d8b45" />
From the HTTP Stream we can search for the string “artist”.
<img width="681" height="247" alt="Screenshot 2025-09-25 at 3 43 04 PM" src="https://github.com/user-attachments/assets/fa482588-2e11-44fc-a869-cd7542fca26b" />
What is the name of the second artist?

Ans: Blad3

Modify the string to artist=2.
<img width="679" height="235" alt="Screenshot 2025-09-25 at 3 43 12 PM" src="https://github.com/user-attachments/assets/ab4b1238-1efd-41de-b88e-5b501b1dad49" />
conclusion


