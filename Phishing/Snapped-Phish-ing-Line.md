<img width="1429" height="284" alt="Screenshot 2025-10-01 at 12 18 20 PM" src="https://github.com/user-attachments/assets/a53a8b73-92b0-4c95-a1b3-65b22eaaf828" />
Disclaimer

Based on real-world occurrences and past analysis, this scenario presents a narrative with invented names, characters, and events.

Please note: The phishing kit used in this scenario was retrieved from a real-world phishing campaign. Hence, it is advised that interaction with the phishing artefacts be done only inside the attached VM, as it is an isolated environment.

<img width="412" height="516" alt="Screenshot 2025-10-01 at 12 22 02 PM" src="https://github.com/user-attachments/assets/9a7d2327-9886-4e5d-9e48-cda3aa444cf5" />

An Ordinary Midsummer Day...

As an IT department personnel of SwiftSpend Financial, one of your responsibilities is to support your fellow employees with their technical concerns. While everything seemed ordinary and mundane, this gradually changed when several employees from various departments started reporting an unusual email they had received. Unfortunately, some had already submitted their credentials and could no longer log in.

You now proceeded to investigate what is going on by:

Analysing the email samples provided by your colleagues.
Analysing the phishing URL(s) by browsing it using Firefox.
Retrieving the phishing kit used by the adversary.
Using CTI-related tooling to gather more information about the adversary.
Analysing the phishing kit to gather more information about the adversary.
Connecting to the machine

Start the virtual machine in split-screen view by clicking the green Start Machine button on the upper right section of this task. If the VM is not visible, use the blue Show Split View button at the top-right of the page. Alternatively, using the credentials below, you can connect to the VM via RDP.
<img width="443" height="168" alt="Screenshot 2025-10-01 at 12 22 43 PM" src="https://github.com/user-attachments/assets/3fc743af-e9b9-4e38-88dd-491b1a2a9cd6" />
Note: The phishing emails to be analysed are under the phish-emails directory on the Desktop. Usage of a web browser, text editor and some knowledge of the grep command will help.

Q. Who is the individual who received an email attachment containing a PDF?

Q. What email address was used by the adversary to send the phishing emails?
<img width="688" height="314" alt="Screenshot 2025-10-01 at 12 24 18 PM" src="https://github.com/user-attachments/assets/211d9d42-40d2-41fc-90b7-67a0a5a74db1" />
Answer — William McClean

Answer — Accounts.Payable@groupmarketingonline.icu

Q. What is the redirection URL to the phishing page for the individual Zoe Duncan? (defanged format)

Step 1 — Download HTML file attachment from Zoe Duncan’s email

Step 2 —

<img width="671" height="109" alt="Screenshot 2025-10-01 at 12 24 28 PM" src="https://github.com/user-attachments/assets/b97b46ee-6ef9-4982-8306-02b8cf2fdef9" />
Copy the first URL & use Cyberchef’s defang URL filter —
<img width="648" height="66" alt="Screenshot 2025-10-01 at 12 24 36 PM" src="https://github.com/user-attachments/assets/02bfa5f2-8935-458a-b755-af92504a8d7b" />
Q. What is the URL to the .zip archive of the phishing kit? (defanged format)

Hint — enumerate the URL

Visiting

http://kennaroads.buzz/data/Update365/ and http://kennaroads.buzz/data/
<img width="666" height="315" alt="Screenshot 2025-10-01 at 12 24 46 PM" src="https://github.com/user-attachments/assets/50272957-3403-496d-b542-1ec6ea88cb60" />
<img width="619" height="411" alt="Screenshot 2025-10-01 at 12 24 54 PM" src="https://github.com/user-attachments/assets/4826f5d8-1b57-491a-8a6d-3368416eab58" />
<img width="700" height="340" alt="Screenshot 2025-10-01 at 12 25 04 PM" src="https://github.com/user-attachments/assets/74205bb4-d8f7-4903-bd53-c8dfb8bca533" />
Findings —

Files: log.txt, Update365.zip

Q. What is the SHA256 hash of the phishing kit archive?
<img width="662" height="94" alt="Screenshot 2025-10-01 at 12 25 12 PM" src="https://github.com/user-attachments/assets/24527157-9635-4a48-9498-567e34431025" />
Q. When was the phishing kit archive first submitted? (format: YYYY-MM-DD HH:MM:SS UTC)

Step 1 — Visit the VirusTotal site

Step 2 — Search for the SHA256 hash of the phishing kit archive

Press enter or click to view image in full size
<img width="670" height="396" alt="Screenshot 2025-10-01 at 12 25 20 PM" src="https://github.com/user-attachments/assets/e2c25543-c4e4-4c14-9c75-069052be23ab" />
Q. When was the phishing domain that was used to host the phishing kit archive first registered? (format: YYYY-MM-DD)

Step 1 — Since the website that the victims of the phishing attack visited kennarods.buzz search for kennarods.buzz on ThreatBook CTI
<img width="683" height="326" alt="Screenshot 2025-10-01 at 12 25 29 PM" src="https://github.com/user-attachments/assets/43828c7b-f4d7-45a0-8716-5b35ffba56b8" />
Q. What was the email address of the user who submitted their password twice?

Analyzing log.txt
<img width="685" height="348" alt="Screenshot 2025-10-01 at 12 25 36 PM" src="https://github.com/user-attachments/assets/e61f52d5-cd73-441f-9584-f13b723e6047" />
Q. What was the email address used by the adversary to collect compromised credentials?

After analyzing submit.php.

Press enter or click to view image in full size
<img width="542" height="328" alt="Screenshot 2025-10-01 at 12 25 41 PM" src="https://github.com/user-attachments/assets/e60dd4af-ddb7-4401-923e-39acab7ba07e" />
Q. The adversary used other email addresses in the obtained phishing kit. What is the email address that ends in “@gmail.com”?
<img width="679" height="341" alt="Screenshot 2025-10-01 at 12 25 48 PM" src="https://github.com/user-attachments/assets/9beb591a-378a-46c3-be10-bb4345294406" />

Q. What is the hidden flag?

Question Hint

The flag contains a “.txt” extension and, with some adjustments, should be downloadable from the phishing URL. Look for the flag in every subdomain/directory of the phishing URL.
<img width="679" height="284" alt="Screenshot 2025-10-01 at 12 25 58 PM" src="https://github.com/user-attachments/assets/e12bbfd1-a15b-425f-b854-a52a6f760f48" />
<img width="682" height="366" alt="Screenshot 2025-10-01 at 12 26 04 PM" src="https://github.com/user-attachments/assets/c206f4a6-67fe-4dec-844a-94989aaf514b" />
This room helps one to understand the process of analyzing phishing emails and phishing kits through log file analysis and OSINT techniques and platforms such as VirusTotal and ThreatBook CTI. Ending with some source code review to capture the adversary’s email address.







