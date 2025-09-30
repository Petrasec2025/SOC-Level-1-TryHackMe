<img width="1402" height="193" alt="Screenshot 2025-09-30 at 3 26 56 PM" src="https://github.com/user-attachments/assets/c27fc3ce-b4e3-45c1-8475-bfb5a43a533c" />
I recently came back from my break and, as promised, will be redoing Splunk rooms to create a write-up. This also doubles as a review for me as I did this early on in the SOC Level 1 learning path, so this will help me reinforce what I learned before. Just like before, I will document my thinking and even include my wrong answer attempts to show that we are all learning. I will also be documenting if I used external help.

Task 3 Splunk Components

1: Which component is used to collect and send data over the Splunk instance?

This can be found in the reading.

Answer: Forwarder

Task 4 Navigating Splunk

1: In the Add Data tab, which option is used to collect data from files and ports?

I used my own virtual machine instead of TryHackMe’s Attack Box. To connect your own VM to TryHackMe’s network, follow my article on RDP until you connect to the network.

Once I connected, I opened Firefox and typed in the IP address that should display from Task 2. If the IP Address doesn’t work, try typing in http:// too. Once your Splunk loads, click on Add Data. Then scroll to the bottom and you’ll find the answer.
<img width="718" height="465" alt="Screenshot 2025-09-30 at 3 29 27 PM" src="https://github.com/user-attachments/assets/0b57af24-9004-4598-aedd-6a37e4fded07" />
Answer: Monitor

Task 5 Adding Data

I downloaded the files from my host machine and then uploaded it to file.io and then downloaded it to my VM. There’s probably more effective ways to do it but that’s just how I did it. Once the file is in file.io, I used the command wget -O VPNLogs.json (link) in the terminal. Remember where your current directory is as it will save it to that directory. The -O option allows us to rename the file. In this case, it will be renamed to VPNLogs.json.

Follow the instructions and gif in the reading to upload data. I took a couple of pics to show what was inputted since the gif is pretty long.
<img width="786" height="612" alt="Screenshot 2025-09-30 at 3 29 39 PM" src="https://github.com/user-attachments/assets/557a4162-3e7a-4eed-90e8-dc906ce27156" />
<img width="495" height="197" alt="Screenshot 2025-09-30 at 3 29 45 PM" src="https://github.com/user-attachments/assets/ffc91b9b-67de-4b0c-aaaf-83e2227d218e" />
Here’s how it should like when you review it.
<img width="320" height="187" alt="Screenshot 2025-09-30 at 3 29 49 PM" src="https://github.com/user-attachments/assets/67bd59ab-6f13-4f01-9fcd-0de2bd6e43b6" />

1: Upload the data attached to this task and create an index “VPN_Logs”. How many events are present in the log file?

When you finish uploading and start searching, it should already display the results. If it doesn’t, type index=vpn_logs in the search bar and change the present to “All time.”
<img width="1195" height="692" alt="Screenshot 2025-09-30 at 3 29 58 PM" src="https://github.com/user-attachments/assets/b007f05b-6431-4234-869f-126fce831a4b" />
<img width="457" height="121" alt="Screenshot 2025-09-30 at 3 30 11 PM" src="https://github.com/user-attachments/assets/a99c305b-daa8-410b-934a-b3fdd9613de2" />
Alternatively, you can just click on UserName and look at the count.
<img width="691" height="393" alt="Screenshot 2025-09-30 at 3 30 17 PM" src="https://github.com/user-attachments/assets/f345fca8-0d7f-4f68-a338-7fcf83cfcdad" />
Answer: 60

3: What is the name associated with IP 107.14.182.38?

Similar to above, I looked at the interesting fields. Source_ip is something we might need. I adjusted the filter to what I need and looked at the results and the accompanying user.
<img width="687" height="497" alt="Screenshot 2025-09-30 at 3 30 24 PM" src="https://github.com/user-attachments/assets/c099b99e-9ca9-493a-8a44-498793abd1ab" />
Answer: Smith

4: What is the number of events that originated from all countries except France?

Look at the interesting fields again. This time, it looks like Source_Country is what we need. I clicked on France so it will create the search query for me. Then I added “NOT” in front of Source_Country. How did I know to use “NOT”? I vaguely remember Splunk accepts boolean expressions.
<img width="491" height="132" alt="Screenshot 2025-09-30 at 3 30 32 PM" src="https://github.com/user-attachments/assets/9abb3f03-ed2f-441d-8587-1c8279240225" />

Alternatively, you can do some math. Since we know there is a total of 2862 events from question 1, we can click on Source_Country to see how many events have France as a source country. Then we subtract 48 to get 2814.
<img width="472" height="33" alt="Screenshot 2025-09-30 at 3 30 38 PM" src="https://github.com/user-attachments/assets/8c15fcab-c30c-4a5e-a4dc-8c5897d5bef8" />

Answer: 2814

5: How many VPN Events were observed by the IP 107.3.206.58?

Similar to question 3, I will be using Source_ip field as we are looking for a specific IP. I adjusted my search query to the one below and hit enter.
<img width="459" height="115" alt="Screenshot 2025-09-30 at 3 30 45 PM" src="https://github.com/user-attachments/assets/48ff710d-6449-4cc8-93c9-a121807cebb4" />
Answer: 14

Thoughts

While it is a review, I think this was a bit too basic for me. It is a introductory room, so it is absolutely understandable. I’m looking forward to the rest of the Splunk rooms to work on my querying skills. Thank you for being patient while I was gone. I’ll be redoing the Splunk rooms, phishing rooms, and I believe the first two Wireshark rooms so I can complete the SOC Level 1 path write-ups.
