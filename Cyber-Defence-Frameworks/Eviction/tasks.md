Eviction— SOC Level 1 -Cyber Defence Frameworks — TryHackMe Challenge Walkthrough

<img width="679" height="342" alt="Screenshot 2025-09-01 at 12 01 57 AM" src="https://github.com/user-attachments/assets/6bd5a96b-6d59-4616-90e9-26dd62c9c050" />

Site Link: https://tryhackme.com/room/eviction
Task 1
Understand the adversary
<img width="707" height="265" alt="Screenshot 2025-09-01 at 12 02 08 AM" src="https://github.com/user-attachments/assets/e2f9e177-cafd-41cf-84f4-e062b57058f3" />
Sunny is a SOC analyst at E-corp, which manufactures rare earth metals for government and non-government clients. She receives a classified intelligence report that informs her that an APT group (APT28) might be trying to attack organizations similar to E-corp. To act on this intelligence, she must use the MITRE ATT&CK Navigator to identify the TTPs used by the APT group, to ensure it has not already intruded into the network, and to stop it if it has.

Please visit this link (https://static-labs.tryhackme.cloud/sites/eviction/)

to check out the MITRE ATT&CK Navigator layer for the APT group and answer the questions below.
<img width="681" height="327" alt="Screenshot 2025-09-01 at 12 02 20 AM" src="https://github.com/user-attachments/assets/9d44e1c0-8e62-4d4d-9840-28c3f2b1d8e5" />
Answer the questions below

What is a technique used by the APT to both perform recon and gain initial access?
Expand the view to see the technique
<img width="712" height="641" alt="Screenshot 2025-09-01 at 12 02 29 AM" src="https://github.com/user-attachments/assets/1729c776-6f85-4da1-ad49-0fdb2554a0d0" />
APT28 often uses Spearphishing Attachment to conduct recon and gain initial access simultaneously. They send carefully crafted emails with malicious attachments to target employees, gaining access when the target opens the attachment.

Answer: Spearphishing Link

2. Sunny identified that the APT might have moved forward from the recon phase. Which accounts might the APT compromise while developing resources?
   <img width="686" height="296" alt="Screenshot 2025-09-01 at 12 02 38 AM" src="https://github.com/user-attachments/assets/bb0dd279-dcc1-4933-bcc0-e20e89bf819a" />
   Because it Spearphishing the accounts that might the APT compromise while developing resources

Press enter or click to view image in full size

<img width="677" height="284" alt="Screenshot 2025-09-01 at 12 02 45 AM" src="https://github.com/user-attachments/assets/3da58cbd-50ce-48d7-88f1-6214886e63d5" />
Answer: Email Account

3. E-corp has found that the APT might have gained initial access using social engineering to make the user execute code for the threat actor. Sunny wants to identify if the APT was also successful in execution. What two techniques of user execution should Sunny look out for? (Answer format: <technique 1> and <technique 2>)

Press enter or click to view image in full size
<img width="713" height="286" alt="Screenshot 2025-09-01 at 12 05 34 AM" src="https://github.com/user-attachments/assets/cd4d1b84-1125-4a8a-8462-0dffcc001f35" />
The two techniques of user execution should Sunny look out for is

The first one is the Malicious File
<img width="697" height="699" alt="Screenshot 2025-09-01 at 12 05 44 AM" src="https://github.com/user-attachments/assets/917f4cd9-afd8-411f-8ea2-d975518dfeda" />
The second one is Malicious Link
<img width="698" height="640" alt="Screenshot 2025-09-01 at 12 05 51 AM" src="https://github.com/user-attachments/assets/dc36811c-25c4-405a-8713-530d00ead0c8" />
These interpreters are commonly abused by attackers for code execution once the initial compromise occurs.

Answer: Malicious File and Malicuious Link

4. If the above technique was successful, which scripting interpreters should Sunny search for to identify successful execution? (Answer format: <technique 1> and <technique 2>)
   <img width="687" height="290" alt="Screenshot 2025-09-01 at 12 05 58 AM" src="https://github.com/user-attachments/assets/554166f7-b366-439e-a11f-715b5fa3803d" />

The scripting interpreters should Sunny search for to identify successful execution

the first one
<img width="687" height="644" alt="Screenshot 2025-09-01 at 12 06 04 AM" src="https://github.com/user-attachments/assets/de550d42-d9df-408d-a696-020736aad0bf" />

The second one
<img width="720" height="658" alt="Screenshot 2025-09-01 at 12 06 12 AM" src="https://github.com/user-attachments/assets/3b51a60c-f31e-43b4-b112-9fc6a5ee1112" />
Answer: PowerShell and Windowes Command Shell

5. While looking at the scripting interpreters identified in Q4, Sunny found some obfuscated scripts that changed the registry. Assuming these changes are for maintaining persistence, which registry keys should Sunny observe to track these changes? (Question Hint Use the exact text from the ATT&CK Navigator.

Now we at the Persistence Stage
<img width="686" height="636" alt="Screenshot 2025-09-01 at 12 06 22 AM" src="https://github.com/user-attachments/assets/1b577b2e-ad8a-4b37-bdc1-6ee76a109a59" />

<img width="688" height="308" alt="Screenshot 2025-09-01 at 12 06 29 AM" src="https://github.com/user-attachments/assets/b7af563c-5de7-48b0-87bd-2f13821e1908" />
The registry keys that Sunny should observe to track these changes is

Answer: Registry Run Keys

6. Sunny identified that the APT executes system binaries to evade defences. Which system binary’s execution should Sunny scrutinize for proxy execution?
