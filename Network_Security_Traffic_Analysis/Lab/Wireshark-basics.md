# 🦈 Wireshark Basics Walkthrough

![Wireshark](https://img.shields.io/badge/Tool-Wireshark-blue?style=flat-square)
![PCAP](https://img.shields.io/badge/File-PCAP-green?style=flat-square)
![TryHackMe](https://img.shields.io/badge/Platform-TryHackMe-red?style=flat-square)

---

<img src="https://github.com/user-attachments/assets/98da139e-c7be-4030-b182-096c6c02c413" alt="Screenshot 1" />

Wireshark is an open-source, cross-platform network packet analyser tool capable of sniffing and investigating live traffic and inspecting packet captures (PCAP). It is commonly used as one of the best packet analysis tools. In this room, we will look at the basics of Wireshark and use it to perform fundamental packet analysis.

Press the Start Machine button below.

Start Machine
The machine will start in Split-Screen view. If it is not visible, use the blue Show Split View button at the top of the page.

Note: A VM is attached to this room. You don’t need SSH or RDP; the room provides a “Split View” feature. We suggest completing the Networking module before starting working in this room.

There are two capture files given in the VM. You can use the “http1.pcapng” file to simulate the actions shown in the screenshots. Please note that you need to use the “Exercise.pcapng” file to answer the questions.

![Screenshot](https://github.com/user-attachments/assets/9ab81c69-a1d6-46a1-99fa-4309a5080ac9)

**Answer:** http1.pcapng

---

### 1.2 Which file is used to answer the questions?

There are two capture files given in the VM. You can use the “http1.pcapng” file to simulate the actions shown in the screenshots. Please note that you need to use the “Exercise.pcapng” file to answer the questions.

![Screenshot](https://github.com/user-attachments/assets/51ca72b7-87d8-4fb0-a0cb-8782e3bd5d83)

**Answer:** Exercise.pcapng

---

### Task 2 — Tool Overview

Use the “Exercise.pcapng” file to answer the questions.

Read the “capture file comments”.

**What is the flag?**
**Answer:** TryHackMe\_Wireshark\_Demo

Open the pcap file and open the capture file properties dialog on the bottom left-side of the status bar.

![Screenshot](https://github.com/user-attachments/assets/b6ac08e5-b929-4727-8353-7fdc77319b98)
![Screenshot](https://github.com/user-attachments/assets/0ed8ce47-af44-4c89-9ba6-3903ba610aa0)

**What is the total number of packets?**
**Answer:** 58620

**What is the SHA256 hash value of the capture file?**
**Answer:** f446de335565fb0b0ee5e5a3266703c778b2f3dfad7efeaeccb2da5641a6d6eb

![Screenshot](https://github.com/user-attachments/assets/08da9ae6-953b-4624-a215-e57e303daedc)

---

### Task 3 — Packet Dissection

Use the “Exercise.pcapng” file to answer the questions.

**View packet number 38. Which markup language is used under the HTTP protocol?**
**Answer:** eXtensible Markup Language

![Screenshot](https://github.com/user-attachments/assets/370944af-81b9-42ed-8c98-3b5eae7f76e3)

![Screenshot](https://github.com/user-attachments/assets/257f24da-a9a2-478e-8497-1a56e8d95cb4)

**What is the arrival date of the packet? (Answer format: Month/Day/Year)**
**Answer:** 05/13/2004

**What is the TTL value?**
**Answer:** 47

![Screenshot](https://github.com/user-attachments/assets/50b4f136-44b5-472e-a5bb-69c52dba49ed)

**What is the TCP payload size?**
**Answer:** 424

![Screenshot](https://github.com/user-attachments/assets/27e7983e-b657-4ddb-8243-3f4fc454bf6e)

**What is the e-tag value?**
**Answer:** 9a01a-4696–7e354b00

![Screenshot](https://github.com/user-attachments/assets/9416a2dc-3912-4823-be28-7e024927d791)

---

### Task 4 — Packet Navigation

Use the “Exercise.pcapng” file to answer the questions.

**Search the “r4w” string in packet details. What is the name of artist 1?**
**Answer:** r4w8173

![Screenshot](https://github.com/user-attachments/assets/b7153b81-ef70-4c40-876e-d4e0ab6167e0)

**Go to packet 12 and read the comments. What is the answer?**
**Answer:** 911cd574a42865a956ccde2d04495ebf

![Screenshot](https://github.com/user-attachments/assets/e1815ace-f6e9-412b-a9f4-fdf74f64a606)
![Screenshot](https://github.com/user-attachments/assets/c0768a84-32c8-4f0c-9888-eeafab04be73)

**What is the alien’s name (from note.txt)?**
**Answer:** PACKETMASTER

![Screenshot](https://github.com/user-attachments/assets/83497ec9-f91b-4e95-8069-8c95cd7cd5b4)

![Screenshot](https://github.com/user-attachments/assets/825fa79c-85f3-4ff0-a052-3ba927023ed2)

![Screenshot](https://github.com/user-attachments/assets/c37fc37c-d4d0-46f7-96cf-c6d01f3e7a3b)

**What is the number of warnings (Expert Info)?**
**Answer:** 1636

![Screenshot](https://github.com/user-attachments/assets/e178aaae-338d-41e0-a7c9-f14327af8222)

---

### Task 5 — Packet Filtering

**Go to packet number 4. What is the filter query?**
**Answer:** http

![Screenshot](https://github.com/user-attachments/assets/b48d966f-8c69-4783-a80f-b169e18beb54)

**What is the number of displayed packets?**
**Answer:** 1089

![Screenshot](https://github.com/user-attachments/assets/d5a0062c-b75f-48ce-b3a1-ada7b152e049)

**Go to packet number 33790 and follow the stream. What is the total number of artists?**
**Answer:** 3

**What is the name of the second artist?**
**Answer:** Blad3

![Screenshot](https://github.com/user-attachments/assets/7070f4b9-c0f9-4ae7-b8c7-be04bc5e205b)

![Screenshot](https://github.com/user-attachments/assets/fa482588-2e11-44fc-a869-cd7542fca26b)

![Screenshot](https://github.com/user-attachments/assets/ab4b1238-1efd-41de-b88e-5b501b1dad49)

---

## ✅ Conclusion

Wireshark remains one of the most important tools for cybersecurity analysts and network engineers. Through this room, you learned how to:

* Navigate packet captures effectively
* Extract file objects from captures
* Perform filtering and searching
* Inspect protocol details across the OSI layers

> 🔑 **Key Takeaway:** Wireshark provides unparalleled visibility into network traffic, making it a must-have tool for SOC workflows, DFIR, and threat hunting.

---

*End of file.*
