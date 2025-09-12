# Traffic Analysis Essentials – TryHackMe Room

![TryHackMe Badge](https://img.shields.io/badge/TryHackMe-Completed-success?style=flat-square)
![Cybersecurity Badge](https://img.shields.io/badge/Cybersecurity-Network%20Security-blue?style=flat-square)

---

## 📌 Overview

Network Security is a set of operations for protecting data, applications, devices and systems connected to the network. It is accepted as one of the significant subdomains of cyber security. It focuses on the system design, operation and management of the architecture/infrastructure to provide network accessibility, integrity, continuity and reliability. Traffic analysis (often called Network Traffic Analysis) is a subdomain of the Network Security domain, and its primary focus is investigating the network data to identify problems and anomalies.

This room will cover the foundations of Network Security and Traffic analysis and introduce the essential concepts of these disciplines to help you step into Traffic/Packet Analysis. We suggest completing the "Network Fundamentals" module before starting working in this room.

---

## 🖼️ Screenshots
![Network Security Diagram](https://github.com/user-attachments/assets/b557de4b-5314-4912-8275-27c7c90f136e)
![Network Security Overview](https://github.com/user-attachments/assets/08ce6f62-689d-4b3c-bd73-37ad6308ba4a)


---

## 🛡️ Network Security

The essential concern of Network Security focuses on two core concepts: **authentication** and **authorisation**. There are a variety of tools, technologies, and approaches to ensure and measure implementations of these two key concepts and go beyond to provide continuity and reliability. Network security operations contain three base control levels to ensure the maximum available security management.

**Base Network Security Control Levels:**

| Level         | Description |
|---------------|-------------|
| Physical      | Physical security controls prevent unauthorised physical access to networking devices, cable boards, locks, and all linked components. |
| Technical     | Data security controls prevent unauthorised access to network data, like installing tunnels and implementing security layers. |
| Administrative | Administrative security controls provide consistency in security operations like creating policies, access levels and authentication processes. |

**Main Approaches:**

| Approach       | Description |
|----------------|-------------|
| Access Control | Starting point of Network Security. Controls to ensure authentication and authorisation. |
| Threat Control | Detecting and preventing anomalous/malicious activities on the network, including internal and external traffic probes. |

**Access Control Elements:**

- **Firewall Protection:** Controls network traffic with predetermined security rules.  
- **Network Access Control (NAC):** Verifies device compliance before network access.  
- **Identity and Access Management (IAM):** Manages asset identities and user access.  
- **Load Balancing:** Distributes resources based on metrics to improve data flow.  
- **Network Segmentation:** Isolates users and groups assets for better protection.  
- **VPNs:** Provides encrypted communication for secure remote access.  
- **Zero Trust Model:** Configures minimal access per role – "Never trust, always verify."

**Threat Control Elements:**

- **IDS/IPS:** Detects and blocks anomalous traffic.  
- **DLP:** Prevents sensitive data extraction.  
- **Endpoint Protection:** Multi-layered security for all connected endpoints.  
- **Cloud Security:** Protects cloud resources with VPNs and encryption.  
- **SIEM:** Correlates logs/events to identify anomalies.  
- **SOAR:** Automates tasks between people, tools, and data.  
- **Network Traffic Analysis / NDR:** Inspects network traffic to detect anomalies.

---

## 📊 Typical Network Security Management Operation

| Deployment | Configuration | Management | Monitoring | Maintenance |
|------------|---------------|-----------|------------|------------|
| Device and software installation | Initial configuration | Automation | Feature configuration | Initial network access configuration |
| Security policy implementation | NAT and VPN implementation | Threat mitigation | System monitoring | User activity monitoring |
| Threat monitoring | Log and traffic sample capturing | Upgrades | Security updates | Rule adjustments |
| Licence management | Configuration updates | Managed Security Services | - | - |

**Managed Security Services (MSS):**

- **Network Penetration Testing:** Simulating attacks to assess security.  
- **Vulnerability Assessment:** Discovering and analyzing vulnerabilities.  
- **Incident Response:** Identifying, containing, and eliminating breaches.  
- **Behavioural Analysis:** Creating traffic/user baselines to detect anomalies.

---

### ✅ Quiz Answers

- Which Security Control Level covers creating security policies?  
**Answer:** Administrative  

- Which Access Control element works with data metrics to manage data flow?  
**Answer:** Load Balancing  

- Which technology helps correlate different tool outputs and data sources?  
**Answer:** SOAR  

---

## 🔍 Traffic Analysis / Network Traffic Analysis

Traffic Analysis is a method of intercepting, recording/monitoring, and analysing network data and communication patterns to detect and respond to system health issues, network anomalies, and threats.  

**Covered Disciplines:**

- Network Sniffing and Packet Analysis (Wireshark)  
- Network Monitoring (Zeek)  
- Intrusion Detection/Prevention (Snort)  
- Network Forensics (NetworkMiner)  
- Threat Hunting (Brim)

**Techniques:**

| Technique       | Description |
|-----------------|-------------|
| Flow Analysis   | Provides statistical summaries from network devices. Easy but lacks full packet details. |
| Packet Analysis | Deep Packet Inspection (DPI) to detect/block malicious packets. Full detail but requires time and skill. |

**Benefits:**

- Full network visibility  
- Asset baselining  
- Detect/respond to anomalies  
- Essential for advanced threat detection  

---

## 🖥️ Lab Activities

### Level 1 – Identify & Filter Malicious IPs

1. Started network traffic simulation.  
2. Detected malware activity.  
3. Identified suspicious IPs via IDS/IPS.  
4. Added malicious IPs to firewall filter.  
5. Restarted network traffic.

**Flag Found:** `THM{PACKET_MASTER}`

![Level 1 Screenshot](https://github.com/user-attachments/assets/584915c2-59a5-4b40-93fc-500b706ae5c3)  
![Restore Network Screenshot](https://github.com/user-attachments/assets/9a768297-ad33-4a72-9069-a9691326c284)  
![Restart Network Screenshot](https://github.com/user-attachments/assets/6c0bf0fe-aa30-4f5b-afaf-a900fc7267fa)  
![Suspicious IP Screenshot](https://github.com/user-attachments/assets/f277b1b0-7c39-4058-9dee-7f9eb6d65185)  
![Add to Filter Screenshot](https://github.com/user-attachments/assets/e3dbe570-e166-4cc5-8e5b-4678c805b19e)  
![Flag Pop-up Screenshot](https://github.com/user-attachments/assets/f84255e3-cd77-4b6a-9694-b161860d66c3)  

---

### Level 2 – Identify & Filter Malicious Ports

1. Analyzed suspicious IP traffic.  
2. Identified destination ports from Traffic Analyzer.  
3. Added malicious ports to firewall filter.  
4. Restarted network traffic.

![Traffic Analyzer Screenshot](https://github.com/user-attachments/assets/bbca05b6-2801-43e0-aebe-8f0619c5d443)  
![Add Ports Screenshot](https://github.com/user-attachments/assets/46dee19b-5cfa-4d6f-bbcc-42b750018200)  
![Restart Network Screenshot](https://github.com/user-attachments/assets/2e85ab3b-b388-4801-b515-4dc08e56887e)  
![Flag Pop-up Screenshot](https://github.com/user-attachments/assets/13306f32-fb40-4dfa-af88-302e9cedfa7e)  

---

## 🎓 Conclusion & Lessons Learned

I have successfully completed the **Traffic Analysis Essentials** room! Here’s what I learned:

- The foundations of **Network Security Operations** and the key control levels.  
- How **Access Control** and **Threat Control** work together to protect networks.  
- The importance of **firewalls, IDS/IPS, SOAR, and SIEM** in real-world operations.  
- How **Traffic Analysis** helps detect anomalies and malicious activity.  
- Hands-on skills: identifying malicious IPs, filtering traffic, and blocking suspicious ports.  
- Traffic analysis remains critical even with encrypted/cloud traffic, as patterns reveal anomalies.  

I am now ready to advance to the **Network Security and Traffic Analysis module** and continue building my practical cybersecurity skills.

---

🎉🎉🎉 **Congratulations! I completed the Traffic Analysis Essentials Room!** 🎉🎉🎉
