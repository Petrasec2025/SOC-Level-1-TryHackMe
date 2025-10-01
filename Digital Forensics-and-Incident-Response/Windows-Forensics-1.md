<img width="1432" height="248" alt="Screenshot 2025-10-01 at 5 42 03 PM" src="https://github.com/user-attachments/assets/af6e3011-8a77-4e8c-913c-2679385f6aec" />
For me, it’s the final stretch to completing the SOC Level 1 learning path. I have completed all the phishing rooms already early on before thinking of doing write-ups to document my progress. That being said, I do want to complete most of the rooms and write the accompanying write-up. I plan on doing that in the future! Also, where is the DFIR: An Introduction room? I didn’t want to create a write-up for rooms that don’t have much hands on. As always, I’ll document my thinking process, whether right or wrong, and will document if I looked for help or not. We’re all learning together and I’m not afraid to say I am not an expert at all. Without furder ado, let’s get started!

Task 1 Introduction to Windows Forensics

1: What is the most used Desktop Operating System right now?

This can be found in the reading.

Answer: Microsoft Windows

Task 2 Windows Registry and Forensics

1: What is the short form for HKEY_LOCAL_MACHINE?

This can be found in the reading. Also quite good information as to what the information in each of the five root keys hold.

Answer: HKLM

Task 3 Accessing registry hives offline

1: What is the path for the five main registry hives, DEFAULT, SAM, SECURITY, SOFTWARE, and SYSTEM?

This can be found in the reading.

Answer: C:\Windows\System32\Config

2: What is the path for the AmCache hive?

This can be found in the reading.

Answer: C:\Windows\AppCompat\Programs\Amcache.hve

Task 6 System Information and System Accounts

1: What is the Current Build Number of the machine whose data is being investigated?

We will be using the screenshot provided in the reading. The OS Version section tells us to use the screenshot to answer question 1.

Answer: 19044

2: Which ControlSet contains the last known good configuration?

The screenshot in Current Control Set section will contain the answer we need.

Answer: 1

3: What is the Computer Name of the computer?

The screenshot in Computer Name section will contain the answer we need.

Answer: THM-4N6

4: What is the value of the TimeZoneKeyName?

The screenshot in Time Zone Information section will contain the answer we need.

Answer: Pakistan Standard Time

5: What is the DHCP IP address

The screenshot in Network Interface and Past Networks will contain the answer we need.

Answer: 192.168.100.58

6: What is the RID of the Guest User account?

The screenshot in SAM Hive and User Information section will contain the answer we need. Look at theUser ID colume in the screenshot.

Answer: 501

Task 7 Usage or knowledge of files/folders

1: When was EZtools opened?

The screenshot in Recent Files section will contain the answer we need.

Answer: 2021-12-01 13:00:34

2: At what time was My Computer last interacted with?

The screenshot in ShellBags section will contain the answer we need.

Answer: 2021-12-01 13:06:47

3: What is the Absolute Path of the file opened using notepad.exe?

The screenshot in Open/Save and LastVisited Dialog MRUs section will contain the answers we need for this question and the next.

Answer: C:\Program Files\Amazon\Ec2ConfigService\Settings

4: When was this file opened?

Answer: 2021-11–30 10:56:19

Task 8 Evidence of Execution

1: How many times was the File Explorer launched?

The screenshot in UserAssist section will contain the answer we need.

Answer: 26

2: What is another name for ShimCache?

The answer can be found in the reading. The shorter name is the answer.

Answer: AppCompatCache

3: Which of the artifacts also saves SHA1 hashes of the executed programs?

The answer can be found in the reading.

Answer: AmCache

4: Which of the artifacts saves the full path of the executed programs?

The answer can be found in the reading.

Answer: BAM/DAM

Task 9 External Devices/USB device forensics

1: What is the serial number of the device from the manufacturer ‘Kingston’?

The screenshot in Device Identification section will contain the answers we need for this question and the next.

Answer: IC6F654E59A3B0C179D366AE&0

2: What is the name of this device?

Answer: Kingston DataTraveler 2.0 USB Device

3: What is the friendly name of the device from the manufacturer ‘Kingston’?

Combining the information from both the first screenshot and the third from the reading, I can see the Disk Id from the first screenshot and Guid from the third screenshot shows a match. So the device name is Kingston DataTraveler 2.0 USB Device and the friendly name is USB.
<img width="615" height="316" alt="Screenshot 2025-10-01 at 5 43 14 PM" src="https://github.com/user-attachments/assets/9966d5ac-45bb-4ae0-ac5b-d76c9403bfff" />
Answer: USB

Task 10 Hands-on Challenge

I will be RDPing into the machine. I wrote the instructions here on how I did it.

Loading the hives into RegistryExplorer took me about 20 minutes of searching and messing around with the interface. It was difficult when I didn’t even start on the actual questions yet! To load the hives into RegistryExplorer, we need to open it first. RegistryExplorer is located by going to EZTools folder -> RegistryExplorer -> RegistryExplorer. It may take a while for the application to load.
<img width="694" height="253" alt="Screenshot 2025-10-01 at 5 43 52 PM" src="https://github.com/user-attachments/assets/374ea819-b580-486c-954b-d2f9c4461d62" />
Once Registry Explorer loads, we will load the hive. Do this by going to File -> Load hive.
<img width="245" height="85" alt="Screenshot 2025-10-01 at 5 44 00 PM" src="https://github.com/user-attachments/assets/771d0edb-95f3-4bc0-9621-f65d1b5fd7d6" />
From here, go to triage -> C -> Windows -> System 32 -> config to access the registry files.
<img width="679" height="341" alt="Screenshot 2025-10-01 at 5 44 06 PM" src="https://github.com/user-attachments/assets/2687a772-e653-42f4-8086-f4235634bec9" />
I loaded each file one at a time starting with “DEFAULT.” A warning should pop up about sequence numbers not matching. Do not worry. Just press Yes. Next, it says select transaction logs. We will select both DEFAULT.LOG1 and DEFAULT.LOG2 files. To select more than one file, you can click on the first file, then hold CTRL and click on the second file.
<img width="625" height="277" alt="Screenshot 2025-10-01 at 5 44 12 PM" src="https://github.com/user-attachments/assets/38ffa995-8c17-4550-92d6-2e23805e1219" />
We should get a pop up saying to select a location for our new and updated hive. I just saved it at the default location, which should be our Desktop. Next, it should ask if you want to load the updated hive. Select Yes. Now it should ask if we want to load the dirty/original hive. Select No.
<img width="521" height="211" alt="Screenshot 2025-10-01 at 5 44 34 PM" src="https://github.com/user-attachments/assets/95871c50-7a37-4419-b3d5-2e599923704e" />
Congratulations! We loaded our first hive!
<img width="581" height="268" alt="Screenshot 2025-10-01 at 5 44 40 PM" src="https://github.com/user-attachments/assets/dd74a21e-b9a6-46bc-8a09-c69636521bc0" />
Now do it again for the hives, which are SAM, SECURITY, SOFTWARE, and SYSTEM. SAM was the only one that didn’t seem to have any trouble with it being “dirty” but I’m not sure if it’s just me. I also loaded NTUSER.DAT since I think I might need it later on. NTUSER.DAT is located at a different folder. It is found in triage -> C -> Users -> THM-4n6 -> NTUSER.DAT. Once you finish loading everything, it should look like this.
<img width="578" height="547" alt="Screenshot 2025-10-01 at 5 44 49 PM" src="https://github.com/user-attachments/assets/50e4f815-a22e-4625-ac03-5fc4bef4829f" />
Now we’re ready to begin!

1: How many user created accounts are present on the system?

On the top left, I clicked on “Available bookmarks” and then clicked on “Users” which should display the list of users associated on this computer.
<img width="591" height="216" alt="Screenshot 2025-10-01 at 5 44 57 PM" src="https://github.com/user-attachments/assets/4fabe5cb-4621-47ce-93ed-b2d0f7530129" />
The right handed side should then show something similar to this. Look at “User Id” column and look for IDs starting with 10. That means it’s a user created account. I only knew that because I checked the hint.

Press enter or click to view image in full size
<img width="1074" height="283" alt="Screenshot 2025-10-01 at 5 45 02 PM" src="https://github.com/user-attachments/assets/22706f1c-a5e8-4bf8-b7ab-4d756cb5dede" />
Answer: 3

2: What is the username of the account that has never been logged in?

After the above, I extended some of the columns so I can see what the column headers were. From here, we can see one user never logged on.
<img width="618" height="140" alt="Screenshot 2025-10-01 at 5 45 09 PM" src="https://github.com/user-attachments/assets/15123d26-526d-41d6-932d-3f46e583705a" />
Answer: thm-user2

3: What’s the password hint for the user THM-4n6?

Similar to question 2, I looked at the columns to see which one gives me the answer I need and extended it for better visibility.
<img width="682" height="92" alt="Screenshot 2025-10-01 at 5 45 17 PM" src="https://github.com/user-attachments/assets/fc450c58-11d8-4482-9ecb-f7b19c07a884" />
Answer: count

4: When was the file ‘Changelog.txt’ accessed?

I went back to one of the reading sections as I recalled learning where to find recent files. It’s in Task 7. The location to find where a file was last accessed is at NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\RecentDocs. Alternatively, you can type “RecentDocs” in the search bar and then look for the result that is under NTUSER.DAT. I was practicing navigating it and didn’t use the search bar.
<img width="557" height="706" alt="Screenshot 2025-10-01 at 5 45 34 PM" src="https://github.com/user-attachments/assets/ba2662ea-780b-4b6d-bdab-31764f4899cf" />
Once you find the right folder, look at the right side for “ChangeLog.txt” and information that seems like the answer.

<img width="1073" height="198" alt="Screenshot 2025-10-01 at 5 45 42 PM" src="https://github.com/user-attachments/assets/b0766f04-4801-462d-8998-62b312b613be" />
Answer: 2021–11–24 18:18:48

5: What is the complete path from where the python 3.8.2 installer was run?

Admittedly, I found this on a whim. I clicked on the Available bookmarks tab on the top left and then just looked around for a bit. I limited myself to only NTUSER.DAT since it’ll limit ourselves to only user THM-4n6. From there, I checked if the answer could be there judging from the folder names only. I saw something interesting when I clicked on RecentApps.
<img width="1201" height="296" alt="Screenshot 2025-10-01 at 5 45 49 PM" src="https://github.com/user-attachments/assets/5079c063-782e-4356-a497-1d12506d76ea" />

I checked the hint to see how to do this section properly. It said to look at UserAssist to look for any execution artifacts. I ended up doing that and looking through each of the folder in UserAssist. Found python again!

<img width="1205" height="322" alt="Screenshot 2025-10-01 at 5 45 58 PM" src="https://github.com/user-attachments/assets/a517c942-7024-4db7-b443-262ba5f21bec" />
Answer: Z:\setups\python-3.8.2.exe

6: When was the USB device with the friendly name ‘USB’ last connected?

I reread task 9 to jog my memory on how to get the device name. I went to SOFTWARE\Microsoft\Windows Portable Devices\Devices first. Unfortunately, Microsoft folder didn’t exist, so the path I used was SOFTWARE\Windows Portable Devices\Devices. I saw that one of the two folders had a FriendlyName value of USB. I took note of, what I believe to be, the serial number in the folder name.
<img width="437" height="67" alt="Screenshot 2025-10-01 at 5 46 08 PM" src="https://github.com/user-attachments/assets/bc7a170a-78ff-4f3a-9c56-6d6f0f83373a" />
Now I searched for “USBSTOR” and looked at the right side to compare values. It looks like the value I took note of wasn’t the serial number but disk ID instead.
<img width="1201" height="153" alt="Screenshot 2025-10-01 at 5 46 15 PM" src="https://github.com/user-attachments/assets/b71c0c9e-18e4-426e-acc4-13ad8576dfaa" />
Answer: 2021–11–24 18:40:06

Thoughts:

I personally felt like this was the right difficulty for me. I’ve used EnCase and Autopsy before but never even heard of Registry Explorer. I love getting exposed to more tools as you’ll never know what your organization will be using. Definitely took me a while to get started as the hardest part for me was understanding how to load the files into Registry Explorer. I enjoyed digging around trying to look for the answer. I even saved the cheat sheet that was given at the end of the room. There is absolutely no way I remembered everything I’ve read so the cheat sheet will definitely be useful. Excited to see what the next room entails!
