# TryHackMe — **Summit** (Write‑Up)

> **Purple Team Challenge** · **Pyramid of Pain** · **Detection Engineering**
> Room: *Summit* (Subscribers only) — by TryHackMe

---

## 📌 Overview

**Scenario:** PicoSecure is running a purple‑team threat simulation to harden malware detection and response. You’ll analyze simulated malware samples and iteratively block them using indicators at increasing difficulty levels from the **Pyramid of Pain**.

**Goal:** Detect and prevent malware samples (`sample1.exe` → `sample4.exe`) using:

* Hash blocklist (Trivial)
* IP egress firewall (Easy)
* DNS filtering for malicious domains (Harder)
* Sigma rule for registry modification (Tough)

---

## 🧭 Table of Contents

* [Prerequisites](#prerequisites)
* [Connection Details](#connection-details)
* [Walkthrough](#walkthrough)

  * [Task 1 — Detect `sample1.exe` (Hash)](#task-1--detect-sample1exe-hash)
  * [Task 2 — Detect `sample2.exe` (IP/Egress Rule)](#task-2--detect-sample2exe-ipegress-rule)
  * [Task 3 — Detect `sample3.exe` (Malicious Domain / DNS Filter)](#task-3--detect-sample3exe-malicious-domain--dns-filter)
  * [Task 4 — Detect `sample4.exe` (Sigma Rule / Registry Modification)](#task-4--detect-sample4exe-sigma-rule--registry-modification)
* [Flags](#flags)
* [Notes & Tips](#notes--tips)
* [Credits](#credits)
* [License](#license)

---

## ✅ Prerequisites

* Completed rooms: **The Pyramid of Pain**, **MITRE** (from THM Cyber Defence Frameworks module)
* Active THM subscription (room is subscribers‑only)

---

## 🔗 Connection Details

1. Click **Start Machine** in Task 1, then open the URL:
   `https://LAB_WEB_URL.p.thmlabs.com`
2. If you see **Bad Gateway**, wait a couple of minutes and refresh.

**Landing page:**

![](https://github.com/user-attachments/assets/6fec2981-715e-4a26-8883-e7d810fdc921)

---

## 🛡️ Walkthrough

### Task 1 — Detect `sample1.exe` (Hash)

Read the email from **Sphinx**, then click **sample1.exe** to open the **Malware Sandbox**.

![](https://github.com/user-attachments/assets/e83c118a-c0a3-4275-bfd7-46bf6aeef382)

Submit the sample for analysis:

![](https://github.com/user-attachments/assets/275633c6-927d-4e49-889d-6e6711a6694b)

Copy the **SHA256** hash from *General Info*, then open **Manage Hashes** from the ☰ menu:

![](https://github.com/user-attachments/assets/dc3787a3-912b-42e1-8a74-3b9f0465d84a)

Add the hash to the **SHA256 blocklist** and submit:

![](https://github.com/user-attachments/assets/f2aa41b6-27b0-44f4-8a07-609e7a3f5697)

You should see a success message and a link back to **Inbox**:

![](https://github.com/user-attachments/assets/e915763d-f247-4e79-9113-6feb0bd141b0)

Open the email to get the first flag:

![](https://github.com/user-attachments/assets/33668ad6-9b14-47da-8909-364f1afcb9f1)

**Answer:** `THM{f3cbf08151a11a6a331db9c6cf5f4fe4}`

---

### Task 2 — Detect `sample2.exe` (IP/Egress Rule)

From the new email, click **sample2.exe**:

![](https://github.com/user-attachments/assets/575dca97-f71e-4470-81b1-07749fdf38e2)

Switch the file to `sample2.exe` and analyze:

![](https://github.com/user-attachments/assets/d73a1013-6617-4f8a-93de-a55d88e26fc1)

Scroll to **Network Activity** and copy the **destination IP** `154.35.10.113`:

![](https://github.com/user-attachments/assets/3a425cf1-953d-48e2-b26a-019adc6d5ab9)

Open **Firewall Manager** (☰ → Firewall Manager):

![](https://github.com/user-attachments/assets/2c181ec6-4371-4cb6-bb9a-11707bcb6963)

Create a new **Egress** rule: `Source IP = Any`, `Destination IP = 154.35.10.113`, `Action = Deny`.

![](https://github.com/user-attachments/assets/23def009-08d7-4df0-9878-816cd72a7a6d)

Save the rule to block the malware and check your **Inbox**:

![](https://github.com/user-attachments/assets/466d711d-2256-4fd1-8552-1839de9f8cba)

Open the email for the flag:

![](https://github.com/user-attachments/assets/05849f8b-c11a-4bc6-af8a-a10dc2b1438b)

**Answer:** `THM{2ff48a3421a938b388418be273f4806d}`

---

### Task 3 — Detect `sample3.exe` (Malicious Domain / DNS Filter)

Open the new email and click **sample3.exe**:

![](https://github.com/user-attachments/assets/5019bd87-2d96-4cae-835e-ca3a6a4073ce)

Analyze `sample3.exe`:

![](https://github.com/user-attachments/assets/fe9325e4-fa03-4804-aab6-6acabf985d19)

Review **Behaviour Analysis** and scroll to **Artifacts** → **Domains**. Copy the suspicious domain `emudyn.bresonicz.info`:

![](https://github.com/user-attachments/assets/c21428e6-ec8a-4530-bd59-61268d9dc075)

![](https://github.com/user-attachments/assets/b51ac904-2271-4622-920d-e4d9d038583c)

Open **DNS Filter** (☰ → DNS Filter):

![](https://github.com/user-attachments/assets/ab2f320f-8910-405d-8df6-a5aacb8be3a5)

Create a DNS rule — Name: *Stop Malware download*, Category: *Malware*, Domain: `emudyn.bresonicz.info`, Action: *Deny*.

![](https://github.com/user-attachments/assets/51713460-46e5-4467-9c3d-aaee76f147ba)

Save, see block confirmation, then head to **Inbox**:

![](https://github.com/user-attachments/assets/15c97e8f-8373-491e-9202-61fde2dfb6a9)

![](https://github.com/user-attachments/assets/79a4c650-e1c9-445d-b8ee-a110d9b6a525)

Open email for the flag:

![](https://github.com/user-attachments/assets/4074e0cb-243b-46ec-9b42-8d5b05e77a43)

**Answer:** `THM{4eca9e2f61a19ecd5df34c788e7dce16}`

---

### Task 4 — Detect `sample4.exe` (Sigma Rule / Registry Modification)

Open the new email and click **sample4.exe**:

![](https://github.com/user-attachments/assets/0fd39c6d-39b7-40bd-b5c7-1a410efc068c)

Analyze `sample4.exe`:

![](https://github.com/user-attachments/assets/5c9ab69d-31f5-4078-a950-94d19fb7e3a0)

From **Behaviour Analysis** note: *Malware disables Windows Defender Real-time monitoring*.

![](https://github.com/user-attachments/assets/68ff8d01-4575-430f-9d65-117a1719a41c)

Scroll to **Registry Activity** and copy the event that sets:

```
Key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Defender\Real-Time Protection
Name: DisableRealtimeMonitoring
Value: 1
```

![](https://github.com/user-attachments/assets/2a2cc005-8f85-4341-b1fe-4a80661c44c1)

Open **Sigma Rule Builder** (☰ → Sigma Rule Builder) and click **Create Sigma Rule**:

![](https://github.com/user-attachments/assets/963a7844-a4d0-4ccc-be19-57b6d839c2b0)

Choose **Sysmon Event Logs** → **Registry Modifications**:

![](https://github.com/user-attachments/assets/0b7f53ff-d020-4f66-a62e-c7cad3f09cca)

![](https://github.com/user-attachments/assets/42afe250-a4e7-41ed-8eff-3ef564eb4ae2)

Fill in the fields using the registry data above and map to **MITRE ATT\&CK: TA0005 (Defense Evasion)**. Click **Validate Rule**.

!\[]\([https://github.com/user-attachments/assets/15ae50e4-](https://github.com/user-attachments/assets/15ae50e4-)... placeholder)

> ⚠️ If validation succeeds you’ll hear a new‑mail chime; open **Mail** to retrieve the final flag.

![](https://github.com/user-attachments/assets/e4213bbe-da39-4f18-9c9d-1fec8cba2100)

![](https://github.com/user-attachments/assets/d35c872e-2940-4755-9003-2c5ab5cf2747)

**Answer:** *(Enter flag from the last email — add here once collected.)*

> If you captured it already, replace this line with the actual flag.

---

## 🏁 Flags

* **Task 1:** `THM{f3cbf08151a11a6a331db9c6cf5f4fe4}`
* **Task 2:** `THM{2ff48a3421a938b388418be273f4806d}`
* **Task 3:** `THM{4eca9e2f61a19ecd5df34c788e7dce16}`
* **Task 4:** *(TBD — from final email)*

> **Spoiler Notice:** This repository contains answers for educational purposes.

---

## 📝 Notes & Tips

* **Hashes** are trivial to change — good for quick containment, weak for long‑term.
* **IPs** can be rotated — blocklists should be paired with egress monitoring.
* **Domains** are more costly for adversaries — DNS filtering adds friction.
* **Behavioral/Sigma** detections are resilient — target *what* the malware does.

---

## 🙌 Credits

* Room & assets: **TryHackMe — Summit**
* Walkthrough & screenshots: @PetrasCyberExpert

---

## 📄 License

This write‑up is provided for educational use. Respect TryHackMe’s Terms of Service.

---

### 📷 Appendix — Raw Screens (Full‑size)

To ensure full‑width display on GitHub, images above use standard Markdown which auto‑scales to content width. Raw links (click to open original size):

* [https://github.com/user-attachments/assets/151c826e-5f50-4572-a571-28bb85e2e31f](https://github.com/user-attachments/assets/151c826e-5f50-4572-a571-28bb85e2e31f)
* [https://github.com/user-attachments/assets/aa6393e6-bc77-41c9-9ea6-f87c31a2c43f](https://github.com/user-attachments/assets/aa6393e6-bc77-41c9-9ea6-f87c31a2c43f)
* [https://github.com/user-attachments/assets/6fec2981-715e-4a26-8883-e7d810fdc921](https://github.com/user-attachments/assets/6fec2981-715e-4a26-8883-e7d810fdc921)
* [https://github.com/user-attachments/assets/e83c118a-c0a3-4275-bfd7-46bf6aeef382](https://github.com/user-attachments/assets/e83c118a-c0a3-4275-bfd7-46bf6aeef382)
* [https://github.com/user-attachments/assets/275633c6-927d-4e49-889d-6e6711a6694b](https://github.com/user-attachments/assets/275633c6-927d-4e49-889d-6e6711a6694b)
* [https://github.com/user-attachments/assets/dc3787a3-912b-42e1-8a74-3b9f0465d84a](https://github.com/user-attachments/assets/dc3787a3-912b-42e1-8a74-3b9f0465d84a)
* [https://github.com/user-attachments/assets/f2aa41b6-27b0-44f4-8a07-609e7a3f5697](https://github.com/user-attachments/assets/f2aa41b6-27b0-44f4-8a07-609e7a3f5697)
* [https://github.com/user-attachments/assets/e915763d-f247-4e79-9113-6feb0bd141b0](https://github.com/user-attachments/assets/e915763d-f247-4e79-9113-6feb0bd141b0)
* [https://github.com/user-attachments/assets/33668ad6-9b14-47da-8909-364f1afcb9f1](https://github.com/user-attachments/assets/33668ad6-9b14-47da-8909-364f1afcb9f1)
* [https://github.com/user-attachments/assets/575dca97-f71e-4470-81b1-07749fdf38e2](https://github.com/user-attachments/assets/575dca97-f71e-4470-81b1-07749fdf38e2)
* [https://github.com/user-attachments/assets/d73a1013-6617-4f8a-93de-a55d88e26fc1](https://github.com/user-attachments/assets/d73a1013-6617-4f8a-93de-a55d88e26fc1)
* [https://github.com/user-attachments/assets/3a425cf1-953d-48e2-b26a-019adc6d5ab9](https://github.com/user-attachments/assets/3a425cf1-953d-48e2-b26a-019adc6d5ab9)
* [https://github.com/user-attachments/assets/2c181ec6-4371-4cb6-bb9a-11707bcb6963](https://github.com/user-attachments/assets/2c181ec6-4371-4cb6-bb9a-11707bcb6963)
* [https://github.com/user-attachments/assets/23def009-08d7-4df0-9878-816cd72a7a6d](https://github.com/user-attachments/assets/23def009-08d7-4df0-9878-816cd72a7a6d)
* [https://github.com/user-attachments/assets/466d711d-2256-4fd1-8552-1839de9f8cba](https://github.com/user-attachments/assets/466d711d-2256-4fd1-8552-1839de9f8cba)
* [https://github.com/user-attachments/assets/05849f8b-c11a-4bc6-af8a-a10dc2b1438b](https://github.com/user-attachments/assets/05849f8b-c11a-4bc6-af8a-a10dc2b1438b)
* [https://github.com/user-attachments/assets/67181b23-a98d-4a14-8147-23b7f15eeb13](https://github.com/user-attachments/assets/67181b23-a98d-4a14-8147-23b7f15eeb13)
* [https://github.com/user-attachments/assets/5019bd87-2d96-4cae-835e-ca3a6a4073ce](https://github.com/user-attachments/assets/5019bd87-2d96-4cae-835e-ca3a6a4073ce)
* [https://github.com/user-attachments/assets/fe9325e4-fa03-4804-aab6-6acabf985d19](https://github.com/user-attachments/assets/fe9325e4-fa03-4804-aab6-6acabf985d19)
* [https://github.com/user-attachments/assets/c21428e6-ec8a-4530-bd59-61268d9dc075](https://github.com/user-attachments/assets/c21428e6-ec8a-4530-bd59-61268d9dc075)
* [https://github.com/user-attachments/assets/b51ac904-2271-4622-920d-e4d9d038583c](https://github.com/user-attachments/assets/b51ac904-2271-4622-920d-e4d9d038583c)
* [https://github.com/user-attachments/assets/ab2f320f-8910-405d-8df6-a5aacb8be3a5](https://github.com/user-attachments/assets/ab2f320f-8910-405d-8df6-a5aacb8be3a5)
* [https://github.com/user-attachments/assets/51713460-46e5-4467-9c3d-aaee76f147ba](https://github.com/user-attachments/assets/51713460-46e5-4467-9c3d-aaee76f147ba)
* [https://github.com/user-attachments/assets/15c97e8f-8373-491e-9202-61fde2dfb6a9](https://github.com/user-attachments/assets/15c97e8f-8373-491e-9202-61fde2dfb6a9)
* [https://github.com/user-attachments/assets/79a4c650-e1c9-445d-b8ee-a110d9b6a525](https://github.com/user-attachments/assets/79a4c650-e1c9-445d-b8ee-a110d9b6a525)
* [https://github.com/user-attachments/assets/4074e0cb-243b-46ec-9b42-8d5b05e77a43](https://github.com/user-attachments/assets/4074e0cb-243b-46ec-9b42-8d5b05e77a43)
* [https://github.com/user-attachments/assets/0fd39c6d-39b7-40bd-b5c7-1a410efc068c](https://github.com/user-attachments/assets/0fd39c6d-39b7-40bd-b5c7-1a410efc068c)
* [https://github.com/user-attachments/assets/5c9ab69d-31f5-4078-a950-94d19fb7e3a0](https://github.com/user-attachments/assets/5c9ab69d-31f5-4078-a950-94d19fb7e3a0)
* [https://github.com/user-attachments/assets/68ff8d01-4575-430f-9d65-117a1719a41c](https://github.com/user-attachments/assets/68ff8d01-4575-430f-9d65-117a1719a41c)
* [https://github.com/user-attachments/assets/2a2cc005-8f85-4341-b1fe-4a80661c44c1](https://github.com/user-attachments/assets/2a2cc005-8f85-4341-b1fe-4a80661c44c1)
* [https://github.com/user-attachments/assets/963a7844-a4d0-4ccc-be19-57b6d839c2b0](https://github.com/user-attachments/assets/963a7844-a4d0-4ccc-be19-57b6d839c2b0)
* [https://github.com/user-attachments/assets/0b7f53ff-d020-4f66-a62e-c7cad3f09cca](https://github.com/user-attachments/assets/0b7f53ff-d020-4f66-a62e-c7cad3f09cca)
* [https://github.com/user-attachments/assets/42afe250-a4e7-41ed-8eff-3ef564eb4ae2](https://github.com/user-attachments/assets/42afe250-a4e7-41ed-8eff-3ef564eb4ae2)
* [https://github.com/user-attachments/assets/e4213bbe-da39-4f18-9c9d-1fec8cba2100](https://github.com/user-attachments/assets/e4213bbe-da39-4f18-9c9d-1fec8cba2100)
* [https://github.com/user-attachments/assets/d35c872e-2940-4755-9003-2c5ab5cf2747](https://github.com/user-attachments/assets/d35c872e-2940-4755-9003-2c5ab5cf2747)

> **Tip:** Standard Markdown image syntax `![](URL)` renders at full content width on GitHub. Avoid fixed widths if you want images to scale across devices.
