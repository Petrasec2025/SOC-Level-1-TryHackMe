# Snort – Network Intrusion Detection and Prevention System (NIDS/NIPS)

![TryHackMe Badge](https://img.shields.io/badge/TryHackMe-Completed-success?style=flat-square)
![Cybersecurity Badge](https://img.shields.io/badge/Cybersecurity-Network%20Security-blue?style=flat-square)

---

## 📌 Overview

This room expects you to be familiar with basic Linux command-line functionalities like general system navigation and Network fundamentals (ports, protocols, and traffic data). The room aims to encourage you to start working with Snort to analyse live and captured traffic.

Before joining this room, we suggest completing the ‘Network Fundamentals’ module. If you have general knowledge of network basics and Linux fundamentals, you will be ready to begin! If you need assistance in the Linux command line, you can refer to our “Linux Fundamentals” rooms (here 1 2 3).

**SNORT** is an open-source, rule-based Network Intrusion Detection and Prevention System (NIDS/NIPS) developed and maintained by Martin Roesch, open-source contributors, and the Cisco Talos team.

> Official description:  
> “Snort is the foremost Open Source Intrusion Prevention System (IPS) in the world. Snort IPS uses a series of rules that help define malicious network activity and uses those rules to find packets that match against them and generate alerts for users.”

---

## 🖼️ Screenshots & VM Setup

![Task Intro Screenshot](https://github.com/user-attachments/assets/9f86ba2c-462a-4e4a-b670-c49cc0db8339)  
![Interactive Material Screenshot](https://github.com/user-attachments/assets/8dc65415-972e-4119-8e4d-3f6d52aeffda)  
![Split Screen VM Screenshot](https://github.com/user-attachments/assets/90386e79-be43-414a-b903-94dd40abbb4d)  
![Task Exercises Folder Screenshot](https://github.com/user-attachments/assets/707343b7-5861-42db-8740-0deefc04bdfc)  
![Traffic Generator Script Screenshot](https://github.com/user-attachments/assets/552f0e4e-a2f0-40d9-aeae-e719282b6733)  
![Traffic Generator in Action Screenshot](https://github.com/user-attachments/assets/766c3a41-0000-4e11-8a8b-954ef39e4b9a)  
![Traffic Generator Terminal Screenshot](https://github.com/user-attachments/assets/129dae18-10fc-4f61-b3d0-70b33a87dc0a)  
![Terminal Navigation Screenshot](https://github.com/user-attachments/assets/8d057bbe-2d9d-4695-9eeb-479ab542b66d)  
![Navigate to Task-Exercises Screenshot](https://github.com/user-attachments/assets/7433279f-d1ea-43cf-b547-8b1eb0078995)  
![Run Command Screenshot](https://github.com/user-attachments/assets/94bf7251-11f7-4dd2-9220-69df954a3868)  

---

## 🛡️ Introduction to IDS/IPS

### IDS (Intrusion Detection System)
- Passive monitoring solution to detect malicious activities, abnormal incidents, and policy violations.  
- Generates alerts for suspicious events.  
- **Types of IDS:**
  - **Network IDS (NIDS):** Monitors traffic flow across network subnets.  
  - **Host-based IDS (HIDS):** Monitors traffic on a single endpoint.

### IPS (Intrusion Prevention System)
- Active protection solution that detects and **stops malicious activities**.  
- Automatically prevents/terminates suspicious events.  
- **Types of IPS:**
  - **Network IPS (NIPS):** Protects the entire subnet; drops malicious connections.  
  - **Behaviour-based IPS (NBA):** Requires training/baselining to learn normal traffic.  
  - **Wireless IPS (WIPS):** Protects wireless networks.  
  - **Host-based IPS (HIPS):** Protects single endpoints; terminates malicious connections.

### Detection & Prevention Techniques
![IDS/IPS Techniques Screenshot](https://github.com/user-attachments/assets/0df01e0c-d55d-4e57-a9a9-ffc9bd34714e)

---

## 🔹 Snort Overview

Capabilities of Snort:

- Live traffic analysis  
- Attack and probe detection  
- Packet logging  
- Protocol analysis  
- Real-time alerting  
- Modules & plugins  
- Pre-processors  
- Cross-platform support (Linux & Windows)

**Snort Modes:**

1. **Sniffer Mode:** Reads IP packets and displays them in the console.  
2. **Packet Logger Mode:** Logs all inbound and outbound IP packets.  
3. **NIDS/NIPS Mode:** Logs or drops packets deemed malicious based on rules.

![Snort Capabilities Screenshot](https://github.com/user-attachments/assets/7ed0708a-335a-441a-8b94-9eb4d03fefb6)

---

## 📝 TryHackMe Questions & Answers

| Question | Answer |
|----------|--------|
| Which Snort mode can help stop threats on a local machine? | HIPS |
| Which Snort mode can help detect threats on a local network? | NIDS |
| Which Snort mode can help detect threats on a local machine? | HIDS |
| Which Snort mode can help stop threats on a local network? | NIPS |
| Which Snort mode works similar to NIPS mode? | NBA |
| According to Snort’s official description, what kind of NIPS is it? | Network |
| NBA training period is also known as … | Baselining |

---

## 🎓 Conclusion & Lessons Learned

I have successfully completed the **Snort – IDS/IPS Essentials** room! Here’s what I learned:

- The **difference between IDS and IPS** and their respective subtypes.  
- How **NIDS, HIDS, NIPS, HIPS, WIPS, and NBA** operate in real-world environments.  
- The importance of **training/baselining** for behaviour-based intrusion detection.  
- Snort’s **modes**: Sniffer, Packet Logger, NIDS/NIPS, and their applications.  
- Hands-on skills: navigating Linux, running scripts, analysing network traffic, and interpreting Snort alerts.  
- Understanding how Snort can detect, log, and block threats in a networked environment.  

This room strengthened my practical knowledge of **network intrusion detection and prevention**, preparing me for real-world network security tasks and further modules in traffic analysis.

---

🎉🎉🎉 **Congratulations! I completed the Snort Room!** 🎉🎉🎉



