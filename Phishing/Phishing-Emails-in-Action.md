# Phishing Emails in Action Room Walkthrough

![Room Banner](https://github.com/user-attachments/assets/018a2c33-1bc4-480a-b05a-e87eb06e4ae1)

## 🏆 Badges
![Phishing](https://img.shields.io/badge/Phishing-Real_World_Analysis-0078D6?style=for-the-badge&logo=shield&logoColor=white)
![Email Security](https://img.shields.io/badge/Email_Security-Threat_Detection-00C800?style=for-the-badge&logo=mail&logoColor=white)
![Difficulty](https://img.shields.io/badge/Difficulty-Intermediate-FFA500?style=for-the-badge)
![Platform](https://img.shields.io/badge/Platform-TryHackMe-FF0000?style=for-the-badge&logo=tryhackme&logoColor=white)
![Completion](https://img.shields.io/badge/Completion-100%25-00FF00?style=for-the-badge)
![SOC](https://img.shields.io/badge/SOC-Analyst-800080?style=for-the-badge)

## Overview
Tryhackme – Phishing Emails in Action
In this walk through, we will be going through the Phishing Emails in Action room from Tryhackme. In this room, we will learn the different indicators of phishing attempts by examining actual phishing emails. So, let's get started without any delay.

---

## Task 1 – Introduction

![Task 1 Introduction](https://github.com/user-attachments/assets/ae6f5e21-d7de-4ea5-84b8-c3d78592573c)

---

## Task 2 – Cancel your PayPal order

### Question 1 – What phrase does the gibberish sender email start with?
![PayPal Phishing Email](https://github.com/user-attachments/assets/f8d16e49-2635-4e1d-bd78-d5484c3ca950)

**Answer:** `service.paypal`

---

## Task 3 – Track your package

### Question 1 – What is the root domain for each URL? Defang the URL.
![DHL Tracking Email](https://github.com/user-attachments/assets/b98ac6f4-a829-4747-820b-e5b1ec756fed)

![Defanged URL](https://github.com/user-attachments/assets/fb2b596c-ab34-4d5b-8d65-75d9662bc7fe)

**Answer:** `hxxps[://]dhl-tracker[.]org`

---

## Task 4 – Select your email provider to view document

### Question 1 – This email sample used the names of a few major companies, their products, and logos such as OneDrive and Adobe. What other company name was used in this phishing email?
![OneDrive Phishing Email](https://github.com/user-attachments/assets/d73e8185-e7df-4b23-809d-49e1f4ff2ae4)

![Company Names](https://github.com/user-attachments/assets/7d2b68b7-489f-4433-a3e1-9a4931c467f1)

**Answer:** `DocuSign`

---

## Task 5 – Please update your payment details

### Question 1 – What should users do if they receive a suspicious email or text message claiming to be from Netflix?
![Netflix Phishing Email](https://github.com/user-attachments/assets/af7d80e3-fea4-4e52-89cf-9e54911f4894)

![Netflix Security Notice](https://github.com/user-attachments/assets/a80bd031-51f9-4c93-b26e-576802d8d99d)

![Report Instructions](https://github.com/user-attachments/assets/75830726-42ca-47f0-a784-3e2d5c0e55f3)

**Answer:** `Report it`

---

## Task 6 – Your recent purchase

### Question 1 – What does BCC mean?
![BCC Definition](https://github.com/user-attachments/assets/108d1679-11e2-438b-887b-625aef548a68)

**Answer:** `Blind Carbon Copy`

### Question 2 – What technique was used to persuade the victim to not ignore the email and act swiftly?
![Urgency Technique](https://github.com/user-attachments/assets/9c686f83-07e8-48b3-8adb-25de97c36850)

**Answer:** `Urgency`

---

## Task 7 – DHL Express Courier Shipping notice

### Question 1 – What is the name of the executable that the Excel attachment attempts to run?
![DHL Excel Attachment](https://github.com/user-attachments/assets/5d3a3d03-e79b-4402-a85e-09af8f5ba3d1)

![Malicious Executable](https://github.com/user-attachments/assets/c2c1c035-1c0a-4c55-adec-c9ec801e39a3)

**Answer:** `cmd.exe`

---

## Task 8 – Conclusion

![Conclusion](https://github.com/user-attachments/assets/ea6294f5-1a4d-4b76-8246-3f0eaea3e4ef)

---

## 🎯 Final Badges
![PayPal](https://img.shields.io/badge/PayPal-Phishing_Scam-FF69B4?style=for-the-badge&logo=paypal&logoColor=white)
![DHL](https://img.shields.io/badge/DHL-Tracking_Scam-000080?style=for-the-badge&logo=dhl&logoColor=white)
![OneDrive](https://img.shields.io/badge/OneDrive-Credential_Harvesting-FF4500?style=for-the-badge&logo=microsoft&logoColor=white)
![Netflix](https://img.shields.io/badge/Netflix-Payment_Scam-008080?style=for-the-badge&logo=netflix&logoColor=white)

## Conclusion

So that was "Phishing Emails in Action" for you. We learned all the different indicators of phishing attempts by examining actual phishing emails. We started off with an alleged email from PayPal which was regarding cancellation of a order. Next, we looked into tracking scam related to DHL. Further, an Microsoft OneDrive credential harvesting attack. Moving on, a Netflix and Apple support email with a PDF and DOC attachments as lure. At last, looked into a DHL email that has a excel file with macros enabled to run the payload.

### Key Phishing Indicators Covered:
- **Suspicious Sender Addresses**: Gibberish email addresses masquerading as legitimate services
- **Fake URLs**: Domains that mimic legitimate services but are actually malicious
- **Brand Impersonation**: Use of trusted company names and logos to appear legitimate
- **Urgency Tactics**: Creating a sense of urgency to prompt immediate action
- **Malicious Attachments**: Excel files with macros designed to execute malicious code
- **BCC Usage**: Mass emailing techniques to target multiple victims

This room provided excellent practical experience in identifying real-world phishing techniques and understanding the common tactics used by attackers to deceive victims.

On that note, i would take your leave and will meet you in next one. Till then, "Happy hacking".

---

**Room Link:** [https://tryhackme.com/room/phishingemails2](https://tryhackme.com/room/phishingemails2rytmuv)
