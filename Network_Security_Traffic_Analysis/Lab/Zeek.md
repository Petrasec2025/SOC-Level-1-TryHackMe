# 🕵️ Zeek Network Analysis Lab Report
---

### 🔗 Badges
![Zeek](https://img.shields.io/badge/Zeek-Network%20Analysis-blue)
![Security](https://img.shields.io/badge/Security-Monitoring-green)
![Forensics](https://img.shields.io/badge/Forensics-Traffic%20Analysis-red)
---

## 📖 Introduction
This report documents my hands-on experience with **Zeek** (formerly Bro), a powerful network analysis framework. Through a series of practical tasks, I explored Zeek's capabilities in network monitoring, log analysis, signature creation, scripting, and leveraging frameworks and packages for advanced threat detection and traffic analysis.

---

## 🧭 Table of Contents
1. [Introduction to Network Monitoring Approaches](#1-introduction-to-network-monitoring-approaches)
2. [Zeek Logs](#2-zeek-logs)
3. [CLI Kung-Fu Recall: Processing Zeek Logs](#3-cli-kung-fu-recall-processing-zeek-logs)
4. [Zeek Signatures](#4-zeek-signatures)
5. [Zeek Scripts: Fundamentals](#5-zeek-scripts-fundamentals)
6. [Zeek Scripts: Scripts and Signatures](#6-zeek-scripts-scripts-and-signatures)
7. [Zeek Scripts: Frameworks](#7-zeek-scripts-frameworks)
8. [Zeek Scripts: Packages](#8-zeek-scripts-packages)
9. [Conclusion](#-conclusion)

---

## 1. Introduction to Network Monitoring Approaches

### 🔍 Network Monitoring vs. Network Security Monitoring (NSM)

| Aspect                | Network Monitoring                          | Network Security Monitoring (NSM)               |
|-----------------------|---------------------------------------------|-------------------------------------------------|
| **Focus**             | Availability, performance, configuration    | Anomalies, intrusions, malicious traffic        |
| **Key Metrics**       | Uptime, device health, traffic balance      | Rogue hosts, encrypted traffic, suspicious ports|
| **Primary Users**     | Network administrators                      | Security analysts, incident responders          |
| **Scope**             | IT/Network management                       | Security Operations Center (SOC)                |

### 🛠️ What is Zeek?
Zeek is an open-source **passive network monitoring tool** that provides detailed logs for forensic analysis and data processing. It differs from traditional IDS/IPS tools like Snort by focusing on **event-based detection** and providing extensive **application-layer visibility**.

#### 🏗️ Zeek Architecture
Zeek operates through two primary layers:
- **Event Engine**: Processes packets and generates events.
- **Policy Script Interpreter**: Executes Zeek scripts for semantic analysis.

#### 📊 Zeek Frameworks
Zeek supports multiple frameworks to extend functionality:

| Category          | Frameworks                                  |
|-------------------|---------------------------------------------|
| Logging           | Notice, Input, Configuration, Intelligence |
| Cluster           | Broker, Supervisor, GeoLocation, File Analysis |
| Signature         | Summary, NetControl, Packet Analysis, TLS Decryption |

#### 🖥️ Working with Zeek
Zeek can be run in two modes:
- **As a service** (live traffic monitoring)
- **Against a PCAP file** (offline analysis)

---

## 2. Zeek Logs

Zeek generates **structured, tab-separated log files** categorized into seven groups:

| Category               | Description                          | Example Logs                          |
|------------------------|--------------------------------------|---------------------------------------|
| Network                | Protocol-specific logs               | `conn.log`, `dns.log`, `http.log`     |
| Files                  | File analysis results                | `files.log`, `pe.log`, `x509.log`     |
| NetControl             | Network control and flow logs        | `netcontrol.log`, `openflow.log`      |
| Detection              | Alerts and indicators                | `notice.log`, `intel.log`             |
| Network Observations   | Host and service summaries           | `known_hosts.log`, `known_services.log`|
| Miscellaneous          | Additional logs                      | `weird.log`, `reporter.log`           |
| Zeek Diagnostic        | System and diagnostic logs           | `stats.log`, `loaded_scripts.log`     |

### 🛠️ Tools for Log Processing
- **`zeek-cut`**: Extracts specific columns from Zeek logs.
- **CLI tools**: `grep`, `cut`, `sort`, `uniq`, `awk`.

---

## 3. CLI Kung-Fu Recall: Processing Zeek Logs

### 🧰 Essential Commands

| Command               | Purpose                                  |
|-----------------------|------------------------------------------|
| `cat file.log`        | Read entire file                         |
| `head/tail file.log`  | Read first/last 10 lines                 |
| `grep 'pattern'`      | Filter lines containing pattern          |
| `cut -f 1`            | Extract first field                      |
| `sort \| uniq`        | Sort and remove duplicates               |
| `zeek-cut field1 field2` | Extract specific fields from Zeek logs   |

---

## 4. Zeek Signatures

Zeek signatures allow **rule-based detection** of network anomalies. Signatures consist of:
- **Signature ID**: Unique name.
- **Conditions**: Header and content filters.
- **Action**: Logging or triggering scripts.

### 📝 Example Signature: Detect HTTP Cleartext Passwords

```zeek
signature http-password {
    ip-proto == tcp
    payload /.*password.*/
    event "Cleartext Password Submission Found!"
}
```

### 🧪 Signature Usage
```bash
zeek -C -r http.pcap -s http-password.sig
```

---

## 5. Zeek Scripts: Fundamentals

Zeek scripts are written in Zeek’s **event-driven scripting language**. They enable advanced correlation and automation.

### 📜 Example Script: Print New Connections
```zeek
event new_connection(c: connection) {
    print fmt("New connection: %s -> %s", c$id$orig_h, c$id$resp_h);
}
```

### 🗂️ Script Locations
- Base scripts: `/opt/zeek/share/zeek/base`
- User scripts: `/opt/zeek/share/zeek/site`
- Policy scripts: `/opt/zeek/share/zeek/policy`

---

## 6. Zeek Scripts: Scripts and Signatures

### 🔗 Combining Scripts and Signatures
Scripts can react to signature matches:

```zeek
event signature_match(state: signature_state, msg: string, data: string) {
    if (state$sig_id == "ftp-admin") {
        print("FTP admin login detected!");
    }
}
```

---

## 7. Zeek Scripts: Frameworks

### 📁 File Framework: Hashing and Extraction
```zeek
@load policy/frameworks/files/hash-all-files.zeek
@load policy/frameworks/files/extract-all-files.zeek
```

### 🗺️ Intelligence Framework
Load threat intelligence feeds to detect IOCs:

```zeek
@load policy/frameworks/intel/seen
@load policy/frameworks/intel/do_notice
redef Intel::read_files += { "/opt/zeek/intel/zeek_intel.txt" };
```

---

## 8. Zeek Scripts: Packages

### 📦 Zeek Package Manager (`zkg`)
Install third-party packages to extend Zeek’s functionality:

```bash
zkg install zeek/cybera/zeek-sniffpass
```

### 🌍 Example Package: `geoip-conn`
Add geolocation data to `conn.log`:

```bash
zeek -Cr case2.pcap geoip-conn
```

---

## 🏆 Conclusion

Through this lab, I gained comprehensive hands-on experience with **Zeek** as a network analysis tool. I learned to:

- ✅ Distinguish between **network monitoring** and **security monitoring**.
- ✅ Process and analyze **Zeek logs** using CLI tools and `zeek-cut`.
- ✅ Create and use **signatures** for detecting specific network events.
- ✅ Write and execute **Zeek scripts** for custom event correlation.
- ✅ Leverage **frameworks** for file analysis, intelligence feeds, and geolocation.
- ✅ Install and use **packages** to extend Zeek’s capabilities.

Zeek’s flexibility and depth make it an invaluable tool for **network forensics**, **threat hunting**, and **incident response**. Its ability to generate rich, structured logs and support custom scripting allows analysts to tailor detection and analysis to their specific needs.

This lab reinforced the importance of **CLI proficiency** and **scripting skills** in effective network security analysis. The experience has prepared me to leverage Zeek in real-world scenarios for detecting and investigating network threats.

---

## 🔍 Lab Answers & Solutions

### Task 1: Introduction to Network Monitoring Approaches
**Flag 1:** `4.2.1` (Zeek version)  
**Flag 2:** `2.4.0` (ZeekControl version)  
**Flag 3:** `8` (Generated alert files)

### Task 2: Zeek Logs
**Flag 1:** `DESKTOP-5C5K6HU` (DHCP hostname)  
**Flag 2:** `2` (Unique DNS queries)  
**Flag 3:** `332.319364` (Longest connection duration)

### Task 4: Zeek Signatures
**Flag 1:** `10.10.57.178` (Source IP of first event)  
**Flag 2:** `38712` (Source port of second event)  
**Flag 3:** `20` (Total packets from port 38706)  
**Flag 4:** `1413` (Unique events in notice.log)  
**Flag 5:** `1410` (ftp-brute signature matches)

### Task 5: Zeek Scripts Fundamentals
**Flag 1:** `astaro_vineyard` (Domain for vinlap01)  
**Flag 2:** `17` (Unique hostnames - 18 total minus 1 invalid)  
**Flag 3:** `jaalam.net` (Identified domain value)

### Task 6: Zeek Scripts & Signatures
**Flag 1:** `[Number of new connections]` (From 103.zeek output)  
**Flag 2:** `1401` (Signature hits in signatures.log)  
**Flag 3:** `731` (Administrator username detections)  
**Flag 4:** `498` (Loaded scripts count)  
**Flag 5:** `2` (Brute-force detections)

### Task 7: Zeek Scripts Frameworks
**Flag 1:** `IN_HOST_HEADER` (Intel info location)  
**Flag 2:** `knr.exe` (Downloaded .exe filename)  
**Flag 3:** `cc28e40b46237ab6d5282199ef78c464` (MD5 hash of .exe)  
**Flag 4:** `Microsoft NCSI` (Text file content)

### Task 8: Zeek Scripts Packages
**Flag 1:** `brozeek` (Username with most hits)  
**Flag 2:** `chicago` (Identified city name)  
**Flag 3:** `23.77.86.54` (IP associated with city)  
**Flag 4:** `[Number of status codes]` (From sumstats output)

---

## 🚀 How to Use This Repository

1. **Clone the repository:**
   ```bash
   git clone https://github.com/your-repo/zeek-analysis.git
   cd zeek-analysis
   ```

2. **Explore the scripts and signatures:**
   - Check the `scripts/` directory for Zeek scripts
   - Review the `signatures/` directory for signature files
   - Examine the `logs/` directory for sample outputs

3. **Run Zeek analyses:**
   ```bash
   # Process a PCAP file
   zeek -C -r sample.pcap
   
   # Use a specific signature
   zeek -C -r http.pcap -s signatures/http-password.sig
   
   # Execute a custom script
   zeek -C -r traffic.pcap scripts/custom-analysis.zeek
   ```

4. **Analyze logs with zeek-cut:**
   ```bash
   # Extract specific fields
   cat conn.log | zeek-cut uid id.orig_h id.resp_h
   
   # Find unique values
   cat dns.log | zeek-cut query | sort | uniq
   ```

---

## 📚 Additional Resources

- [Zeek Official Documentation](https://docs.zeek.org)
- [Zeek Package Manager](https://github.com/zeek/packages)
- [Corelight Zeek Tools](https://corelight.com/opensource)
- [TryHackMe Zeek Room](https://tryhackme.com/room/zeek)

---

**Note:** This lab was completed as part of the TryHackMe Zeek room, providing practical experience with network security monitoring and analysis using the Zeek framework.


