
# 💻 TryHackMe — *Your First Hack*

Learn ethical hacking safely! This project walks you through simulating a real attack scenario using **Gobuster** to find hidden web pages and ethically exploit a vulnerable page in a controlled lab environment.

---

## 📋 Table of Contents

* [About](#-about)
* [Key Concepts](#-key-concepts)
* [Steps & Commands](#-steps--commands)
* [Mission](#-mission)
* [Answers](#-answers)
* [Results](#-results)
* [Assets (Screenshots & Video)](#-assets-screenshots--video)
* [Learnings](#-learnings)
* [Contact](#-contact)

---

## 🔍 About

This TryHackMe room introduces you to **Offensive Security** — the process of ethically simulating hacker behavior to discover system vulnerabilities.

You’ll use the `Gobuster` tool to **enumerate hidden pages** on a fake banking site (`fakebank.thm`) and uncover a sensitive endpoint `/bank-transfer`.

---

## 🧭 Key Concepts

* **Offensive Security:** Simulating real hacker methods to find security holes before malicious actors do.
* **Gobuster:** A directory brute-forcing tool that finds hidden files and folders on web servers.
* **Ethical Hacking:** Authorized, legal testing of systems to improve security.

---

## ⚙️ Steps & Commands

### 🧩 Step 1 — Open the Terminal

Click on the **Terminal** icon on the TryHackMe machine to open a command-line interface.

### 🧠 Step 2 — Run Gobuster

Use the following command to find hidden directories:

```bash
gobuster dir -u http://fakebank.thm -w wordlist.txt
```

**Explanation:**

* `dir` → Mode to find directories
* `-u` → URL of target site
* `-w` → Path to your wordlist file

Gobuster will list all discovered pages (status `200 OK`).

### 🏦 Step 3 — Visit the Hidden Page

Once Gobuster discovers `/bank-transfer`, open it in your browser:

```
http://fakebank.thm/bank-transfer
```

Transfer **$2000** from **account 2276 → 8881**, then refresh your account page.

---

## 🎯 Mission

Your goal was to:

* Discover the hidden `/bank-transfer` page
* Perform an authorized transfer simulation
* Observe the message displayed above your account balance

✅ **Mission accomplished!**
You successfully transferred the amount and saw the message `bank-hacked`.

---

## 🧩 Answers

| Question                                                            | Answer                 |
| ------------------------------------------------------------------- | ---------------------- |
| Which process simulates a hacker's actions to find vulnerabilities? | **Offensive Security** |
| What message appeared after a successful transfer?                  | **bank-hacked**        |

---

## 📊 Results

Below are visual snapshots and the screen recording of your successful hack simulation.
They showcase how Gobuster discovers hidden directories and how the FakeBank portal reveals the vulnerable transfer page.

---

## 🖼️ Assets (Screenshots & Video)

<div align="center">

🎥 **Screen Recording** <video src="https://github.com/nihanth6721/TryHackme_blogs/raw/main/Pre%20Security/Storage/Offensive%20security/Screen%20Recording%202025-10-06%20213952.mp4" controls width="80%"></video>

<br><br>

<img src="https://github.com/nihanth6721/TryHackme_blogs/raw/main/Pre%20Security/Storage/Offensive%20security/Screenshot%202025-10-06%20214150.png" alt="Gobuster output" width="48%"/>  
<img src="https://github.com/nihanth6721/TryHackme_blogs/raw/main/Pre%20Security/Storage/Offensive%20security/Screenshot%202025-10-06%20214409.png" alt="Hidden Page Found" width="48%"/>  

<br><br>

<img src="https://github.com/nihanth6721/TryHackme_blogs/raw/main/Pre%20Security/Storage/Offensive%20security/Screenshot%202025-10-06%20214434.png" alt="Bank Transfer Page" width="48%"/>  
<img src="https://github.com/nihanth6721/TryHackme_blogs/raw/main/Pre%20Security/Storage/Offensive%20security/Screenshot%202025-10-06%20214531.png" alt="Success Message" width="48%"/>

</div>

---

## 📘 Learnings

* You explored **ethical hacking methodology** in a legal, sandboxed environment.
* You learned how to **enumerate hidden endpoints** using Gobuster.
* You experienced the importance of **security testing before deployment**.
* You saw how **human error (unsecured pages)** can lead to major vulnerabilities.

---

## 📫 Contact

* **Author:** [nihanth6721](https://github.com/nihanth6721)
* **Email:** [jnihanthreddy@gmail.com](mailto:jnihanthreddy@gmail.com)
* **Project Repository:** [TryHackMe Blogs](https://github.com/nihanth6721/TryHackme_blogs)

---

### 🛡️ Ethical Reminder

> ⚠️ Always perform security testing **only on systems you have explicit permission** to test.
> The purpose of this room is **education and awareness**, not exploitation.

---

###  “Every ethical hacker was once a curious learner.”

---

Would you like me to now create an **HTML version** (like your Plant Diseases one, with sections and embedded media in `<div>` tags) that matches this same layout for your GitHub Pages or website?
