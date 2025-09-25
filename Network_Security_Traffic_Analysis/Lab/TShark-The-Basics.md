# 🖥️ TShark - The Basics

![Wireshark](https://img.shields.io/badge/Wireshark-TShark-blue?style=flat-square) ![Packet Analysis](https://img.shields.io/badge/Packet_Analysis-Basics-green?style=flat-square) ![Capture](https://img.shields.io/badge/Capture-Exercises-orange?style=flat-square)

<img src="https://github.com/user-attachments/assets/6db600fe-1d01-4aea-bfa8-27bfcdd9807a" alt="Screenshot 2025-09-25 at 5 53 32 PM" style="max-width:100%; height:auto;" />
Question 1: Find the task files on the Desktop in the “exercise-files” folder.

Answer 1: No answer is needed

Question 2: View the details of the demo.pcapng file with “capinfos”.
<img src="https://github.com/user-attachments/assets/39115196-3494-441c-b138-ef886269cd4c" alt="Screenshot 2025-09-25 at 5 53 32 PM" style="max-width:100%; height:auto;" />
Command:
capinfos demo.pcapng

What is the “RIPEMD160” value?
Answer 2: 6ef5f0c165a1db4a3cad3116b0c5bcc0cf6b9ab7

Question 3: What is the installed TShark version in the given VM?
<img src="https://github.com/user-attachments/assets/8dcd7aad-269a-4e02-9c30-dc68748e69f3" alt="Screenshot 2025-09-25 at 5 57 11 PM" style="max-width:100%; height:auto;" />

Command:
tshark -v

Answer 3: 3.2.3

Question 4: List the available interfaces with TShark.
<img src="https://github.com/user-attachments/assets/deb46e45-fc33-4e39-9192-50a5336b31d5" alt="Screenshot 2025-09-25 at 5 57 20 PM" style="max-width:100%; height:auto;" />
Command:
sudo tshark -D

What is the number of available interfaces in the given VM?
Answer 4: 12

Question 5: Read the “demo.pcapng” file with TShark.

<img src="https://github.com/user-attachments/assets/bcf4acb7-ad21-4903-a7d6-636ce73cd50a" alt="Screenshot 2025-09-25 at 5 57 29 PM" style="max-width:100%; height:auto;" />
Command:
tshark -r demo.pcapng

What are the assigned TCP flags in the 29th packet?
Answer 5: PSH, ACK

Question 6: What is the “Ack” value of the 25th packet?
<img src="https://github.com/user-attachments/assets/7221fe88-7db4-40f0-b42a-26f9947cc86f" alt="Screenshot 2025-09-25 at 5 57 38 PM" style="max-width:100%; height:auto;" />
Command:
tshark -r demo.pcapng -T fields -e tcp.ack -Y frame.number==25

Answer 6: 12421

Question 7: What is the “Window size value” of the 9th packet?
<img src="https://github.com/user-attachments/assets/c5eb9ef3-c381-471d-a521-87479a807702" alt="Screenshot 2025-09-25 at 5 57 48 PM" style="max-width:100%; height:auto;" />
Command:
tshark -r demo.pcapng -T fields -e tcp.window_size -Y frame.number==9

Answer 7: 9660

Question 8: Which parameter can help analysts to create a continuous capture dump?
<img src="https://github.com/user-attachments/assets/7daa536d-8aa1-4593-83cd-84d0ad00d18f" alt="Screenshot 2025-09-25 at 5 58 04 PM" style="max-width:100%; height:auto;" />
Answer 8: -b

Question 9: Can we combine autostop and ring buffer parameters with TShark? y/n
<img src="https://github.com/user-attachments/assets/77ecfa41-04d6-4341-99e3-dbb5714a30e0" alt="Screenshot 2025-09-25 at 5 58 13 PM" style="max-width:100%; height:auto;" />
Answer 9: y

Question 10: Which parameter is used to set “Capture Filters”?
<img src="https://github.com/user-attachments/assets/ab5a1267-6eec-4ebd-a306-114c68ad9f93" alt="Screenshot 2025-09-25 at 5 58 22 PM" style="max-width:100%; height:auto;" />
Answer 10: -f

Question 11: Which parameter is used to set “Display Filters”?
Answer 11: -Y

Run the commands from the above Terminator terminals on the target machine and answer the questions.

Question 12: What is the number of packets with SYN bytes?
<img src="https://github.com/user-attachments/assets/3a289bae-580c-4628-b4d8-7736a1d260c4" alt="Screenshot 2025-09-25 at 5 58 31 PM" style="max-width:100%; height:auto;" />
Command:
tshark -r demo.pcapng -Y "tcp.flags.syn == 1" | wc -l

Answer 12: 2

Question 13: What is the number of packets sent to the IP address “10.10.10.10”?
Command:
tshark -r demo.pcapng -Y "ip.dst == 10.10.10.10" | wc -l

Answer 13: 7

Question 14: What is the number of packets with ACK bytes?
Command:
tshark -r demo.pcapng -Y "tcp.flags.ack == 1" | wc -l

Answer 14: 8

Use the “demo.pcapng” file to answer the questions.

Question 15: What is the number of packets with a “65.208.228.223” IP address?
Command:
tshark -r demo.pcapng -Y "ip.addr == 65.208.228.223" | wc -l

Answer 15: 34

Question 16: What is the number of packets with a “TCP port 3371”?
Command:
tshark -r demo.pcapng -Y "tcp.port == 3371" | wc -l

Answer 16: 7

Question 17: What is the number of packets with a “145.254.160.237” IP address as a source address?
Command:
tshark -r demo.pcapng -Y "ip.src == 145.254.160.237" | wc -l

Answer 17: 20

Rerun the previous query and look at the output.

Question 18: What is the packet number of the “Duplicate” packet?
Command:
tshark -r demo.pcapng -Y 'ip.src == 145.254.160.237 and udp.analysis.duplicate' -T fields -e frame.number

Answer 18: 37

---

## Conclusion
Thank You!  

---

![Wireshark](https://img.shields.io/badge/Wireshark-TShark-blue?style=flat-square) ![Packet Analysis](https://img.shields.io/badge/Packet_Analysis-Basics-green?style=flat-square) ![Capture](https://img.shields.io/badge/Capture-Exercises-orange?style=flat-square)

