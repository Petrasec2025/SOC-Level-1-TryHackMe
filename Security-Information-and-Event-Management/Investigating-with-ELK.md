<img width="1432" height="302" alt="Screenshot 2025-09-30 at 2 51 47 PM" src="https://github.com/user-attachments/assets/a31c5a05-14e3-486f-baa8-7d9f6d0e4873" />
Now that we’re all done with Endpoint Security Monitoring, we are moving on to Security Information and Event Management (SIEM). I mentioned this before but I have already done the Splunk labs, so redoing them and creating a write-up at this current time is low on my priority list. That being said, I am always up for more hands-on experience so I do want to do more Splunk labs in preparation for BTL1. We’re going to be using ELK for our SIEM. I never heard of ELK before admittedly, so as always, being exposed to more tools is great for a beginner like me. Let’s get started!

Task 3 ElasticStack Overview

1: Logstash is used to visualize the data. (yay / nay)

This is Kibana’s function.

Answer: Nay

2: Elasticstash supports all data formats apart from JSON. (yay / nay)

It’s actually the opposite. It supports JSON. Both the answers can be found in the reading.

Answer: Nay

Task 4 Kibana Overview

Make sure you’re connected to TryHackMe’s network using a VPN. You can read how over here. I downloaded my configuration file and connected using OpenVPN on my Kali Linux VM.

Once you’re connected, open a browser and then type in the IP address that should populate when you start the machine. For me, mine was 10.10.8.97.

<img width="176" height="117" alt="Screenshot 2025-09-30 at 2 55 12 PM" src="https://github.com/user-attachments/assets/aebac0d2-cfbd-408d-9bda-e69b44ee3e6c" />
Task 5 Discover Tab

1: Select the index vpn_connections and filter from 31st December 2021 to 2nd Feb 2022. How many hits are returned?

Once you typed the IP of the machine, you should be greeted with this screen. Click on the hamburger sign at the top left and then click on “Discover.”
<img width="686" height="709" alt="Screenshot 2025-09-30 at 2 55 43 PM" src="https://github.com/user-attachments/assets/3f89d8ff-baa5-4800-a1ec-92aab2e27724" />
From here, you should be greeted with a search bar. There may or may not be any results currently, but it’s ok. We are going to change it to get our answer. On the top right, there should be some dates or time references. We will be changing that to match what we need for our answer. Click on “Refresh” to populate the new results.
<img width="423" height="393" alt="Screenshot 2025-09-30 at 2 55 50 PM" src="https://github.com/user-attachments/assets/2bdf788b-5e9a-426d-8966-805dbce41430" />
Answer: 2861

2: Which IP address has the max number of connections?

With the results, we can filter it to match what we are looking for. In this case, we are looking for IP addresses and most connections. Click on “Source_ip” and look at which IP address shows up the most. By default, it shows the top 5 values.
<img width="577" height="534" alt="Screenshot 2025-09-30 at 2 55 58 PM" src="https://github.com/user-attachments/assets/284bdfc5-c753-4a9b-9c72-4755fd2f507f" />
Answer: 238.163.231.224

3: Which user is responsible for max traffic?

Very similar to above, but we will look at UserName instead.
<img width="573" height="512" alt="Screenshot 2025-09-30 at 2 56 05 PM" src="https://github.com/user-attachments/assets/c3b051bc-9354-43fc-8a2a-b4413428488d" />
Answer: James

4: Create a table with the fields IP, UserName, Source_Country and save.

I thought this was useful, so I added this in despite having no answer.

To create a table, go to any result and click on the down arrow key to expand it.
<img width="1079" height="71" alt="Screenshot 2025-09-30 at 2 56 16 PM" src="https://github.com/user-attachments/assets/97ced713-9c5b-4309-bd60-0e2a691ce52f" />
From here, you can create a new table for yourself to display what you want to see. In our case, we want to create one with IP, UserName, and Source_Country. What we will do is find the appropriate fields and then click the third from the left icon. It should say “Toggle column in table.”
<img width="446" height="576" alt="Screenshot 2025-09-30 at 2 56 33 PM" src="https://github.com/user-attachments/assets/8b6c451b-4783-485d-8f22-c3c8b9ab2c3c" />
Once done, just collapse the result and our results will only display what we asked!
<img width="1099" height="194" alt="Screenshot 2025-09-30 at 2 56 41 PM" src="https://github.com/user-attachments/assets/c8057131-fb30-469a-88e6-99c9314716db" />
5: Apply Filter on UserName Emanda; which SourceIP has max hits?

I clicked on “UserName” And clicked on the “+” next to Emanda’s name to display only results that has her name. From there, I clicked on “Source_ip” to display IP addresses that is under the UserName “Emanda.”
Answer: 107.14.1.247

6: On 11th Jan, which IP caused the spike observed in the time chart?

I changed the filter to search for only activities that happened on January 11, 2021. Then I removed the filter that was searching for only Emanda by clicking on “x.”
<img width="486" height="159" alt="Screenshot 2025-09-30 at 2 56 55 PM" src="https://github.com/user-attachments/assets/cec61d21-9ed7-4b6a-a56c-1f06b57da065" />

Refresh to display the new results. Then click on “Source_ip” to look at the top 5 values of the new results.
<img width="278" height="354" alt="Screenshot 2025-09-30 at 2 57 01 PM" src="https://github.com/user-attachments/assets/423a2c96-1268-4f06-9e61-40657f8f87f3" />

Answer: 172.201.60.191

7: How many connections were observed from IP 238.163.231.224, excluding the New York state?

What I did first is click on the “+” icon on the correct IP address to add it to our filter.
<img width="248" height="53" alt="Screenshot 2025-09-30 at 2 57 08 PM" src="https://github.com/user-attachments/assets/a19ccee7-afaa-4110-9e91-5098bb3c8a68" />

Next, I head over to “source_state” and clicked on “-” icon next to New York, which means to display results coming from the states excluding New York.
<img width="270" height="283" alt="Screenshot 2025-09-30 at 2 57 13 PM" src="https://github.com/user-attachments/assets/c1dcf55a-18bb-4ec0-a8c6-788465ac7d98" />
An overview of my filters used and the number of hits that resulted.
<img width="609" height="230" alt="Screenshot 2025-09-30 at 2 57 20 PM" src="https://github.com/user-attachments/assets/01a118cb-318d-41d7-91bd-a65869c1c87f" />
… Except it was wrong because it didn’t use results from ONLY January 11. I changed the dates back to how it was originally and the answer was accepted.

Press enter or click to view image in full size
<img width="1081" height="81" alt="Screenshot 2025-09-30 at 2 57 26 PM" src="https://github.com/user-attachments/assets/c49eb663-8034-49b2-9edc-c7e28423701e" />
Answer: 48

Task 6 KQL Overview

1: Create a search query to filter out the logs from Source_Country as the United States and show logs from User James or Albert. How many records were returned?

I followed the example and attempted to create my own. I typed in Source_Country : United States AND UserName : James OR Albert into the search bar. The important thing is to remember that there is a space between the field name and colon.

Press enter or click to view image in full size
<img width="1074" height="83" alt="Screenshot 2025-09-30 at 2 57 35 PM" src="https://github.com/user-attachments/assets/ec516b1f-a304-4108-8384-900fabd69dff" />

Answer: 161

2: As User Johny Brown was terminated on 1st January 2022, create a search query to determine how many times a VPN connection was observed after his termination.

I changed the date range and made it start on January 1, 2022. I typed in his name and waited for the results. Admittedly, I thought this wasn’t the answer because it felt too little, but it was the answer!
<img width="687" height="59" alt="Screenshot 2025-09-30 at 2 57 41 PM" src="https://github.com/user-attachments/assets/66e754ff-ccea-461c-aa08-a558bec0b1d1" />
Answer: 1

Task 7 Creating Visualizations

1: Which user was observed with the greatest number of failed attempts?

The reading will tell you exactly how to do it. I didn’t notice until after I did my attempt. What I did was using 3 fields first. I chose Source_ip, UserName, and action. From there, I was presented with a lot of data. I didn’t know how to filter yet, but on a whim, I decided to hover over failed to see if I can filter it this way, and I can!
<img width="677" height="238" alt="Screenshot 2025-09-30 at 2 57 48 PM" src="https://github.com/user-attachments/assets/791ac640-111f-40a3-9c9a-a1c6718dd194" />
You can see on the top left with a new filter where actions has to have a value of “failed.” This resulted in only one line of result, very easy to read.
<img width="686" height="112" alt="Screenshot 2025-09-30 at 2 57 55 PM" src="https://github.com/user-attachments/assets/3f5f4885-5053-43e8-bc9f-4ce05c4d6414" />
Answer: Simon

2: How many wrong VPN connection attempts were observed in January?

Answer: 274

Thoughts:

This was a really nice room that exposed me to another SIEM tool. I personally felt like it’s easier than Splunk but this is really just an introduction room, so it is deFsigned to be easy. What I really enjoyed about it was just how intuitive the filter is. It seems beginner friendly when trying to find what you need. Can’t wait to utilize what we learned in the next room!




