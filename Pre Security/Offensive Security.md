
# TryHackMe – Beginning Your Learning Journey[1]

This repository documents completing the TryHackMe “Beginning Your Learning Journey / Intro to Offensive Security” room, including running Gobuster against the FakeBank site, locating hidden paths, and performing the guided money transfer to reveal the answer banner. It includes terminal commands, outputs, screenshots, and a screen recording for reproducibility.[3][1]

### Table of contents[4]
- Overview[1]
- Prerequisites[2]
- Outline (what gets done)[1]
- Step 1: Open terminal[1]
- Step 2: Run Gobuster[1]
- Step 3: Visit hidden page[2]
- Step 4: Perform transfer[3]
- Step 5: Verify banner[1]
- Answers[1]
- Media (screenshots and video)[5]

### Overview[1]
The room guides learners through a safe, legal simulation of a first website hack on a practice application called FakeBank, demonstrating how ethical hackers enumerate and test web apps. It culminates in using a discovered transfer page to submit a controlled transaction that reveals a banner containing the answer.[3][1]

### Prerequisites[2]
- Access to the TryHackMe room and the FakeBank target VM.[1]
- A wordlist file accessible to the command environment (e.g., wordlist.txt or a full path to a known list).[2]

### Outline (what gets done)[1]
- Launch the terminal in the provided VM.[1]
- Enumerate hidden content with Gobuster against http://fakebank.thm using a wordlist.[1]
- Identify the /bank-transfer path from Gobuster results.[2]
- Submit a guided transfer: $2000 from 2276 to 8881.[3]
- Refresh the account page and read the banner to capture the answer.[1]

### Step 1: Open terminal[1]
Use the desktop terminal icon on the right of the TryHackMe machine interface to open a terminal; this provides command-line access to run Gobuster and other tools. The room explicitly notes the terminal as the interface for interacting without a GUI file manager.[6][1]

### Step 2: Run Gobuster[1]
Run directory brute forcing with Gobuster against FakeBank using a wordlist; the core syntax is dir mode with -u for URL and -w for the wordlist file. A representative command:  
- Command:  
  - gobuster -u http://fakebank.thm -w wordlist.txt dir[1]
- Notes:  
  - -u specifies the target, -w supplies candidate names, and dir sets directory/file enumeration mode.[7]
  - Common options include -t for threads, -x for extensions, and -o for output files if needed.[7]

### Step 3: Visit hidden page[2]
From Gobuster’s findings, navigate to the discovered endpoint /bank-transfer in the browser, which is the page useful for this exercise; /images may also appear but is not required for the transfer. Example: http://fakebank.thm/bank-transfer.[2][1]

### Step 4: Perform transfer[3]
Submit the transfer form to move $2000 from account 2276 to the learner account 8881 as instructed by the room’s task flow, which should return a visible success confirmation when the operation completes. After the success message, return to the account page to observe the balance update.[8][3]

### Step 5: Verify banner[1]
Reload the account page and look above the balance for the banner that contains the answer string; in this room, the banner text that serves as the answer is “bank-hacked.” This string is to be submitted to the question prompt to complete the task.[3][1]

### Answers[1]
- Which option represents simulating a hacker to find vulnerabilities? Offensive Security.[2][1]
- Banner flag above the balance after transfer? bank-hacked.[3][1]

### Commands and tips[7]
- Basic usage: gobuster dir -u http://fakebank.thm -w wordlist.txt[7]
- Helpful flags:  
  - -t 50 increases threads to speed enumeration if supported by the environment.[7]
  - -x php,txt appends extensions to wordlist entries during enumeration.[7]
  - -o results.txt persists findings for later review and documentation.[7]

### Media (screenshots and video)[5]
- Video walkthrough stored in the repo and linked from README using the standard GitHub-friendly image-to-video link pattern; GitHub renders an image link to the raw video file for reliable playback. Example pattern:  
  - [![Watch the video](https://raw.githubusercontent.com/nihanth6721/TryHackme_blogs/main/Pre%20Security/Storage/Offensive%20security/Screenshot%202025-10-06%(https://raw.githubusercontent.com/nihanth6721/TryHackme_blogs/main/Pre%20Security/Storage/Offensive%20security/Screen%20Recording%202025[5]
- Individual screenshots can be embedded directly in Markdown; use raw.githubusercontent.com for consistent rendering in README:  
  - ![Gobuster Output 1](https://raw.githubusercontent.com/nihanth6721/TryHackme_blogs/main/Pre%20Security/Storage/Offensive%20security/Screenshot%202025-10-06% [9]
  - ![Bank Transfer Form](https://raw.githubusercontent.com/nihanth6721/TryHackme_blogs/main/Pre%20Security/Storage/Offensive%20security/Screenshot%202025-10-06% [9]
  - ![Transfer Success](https://raw.githubusercontent.com/nihanth6721/TryHackme_blogs/main/Pre%20Security/Storage/Offensive%20security/Screenshot%202025-10-06% [9]
  - ![Account Banner](https://raw.githubusercontent.com/nihanth6721/TryHackme_blogs/main/Pre%20Security/Storage/Offensive%20security/Screenshot%202025-10-06% [9]

### Appendix: Markdown embedding notes[5]
- GitHub READMEs do not autoplay videos; best practice is an image that links to an MP4 hosted in the same repository via the raw URL. Use the thumbnail image as the clickable preview for a consistent UX across browsers.[10][5]
- For YouTube, use a thumbnail image that links to the YouTube URL; this pattern is common and renders reliably in GitHub markdown without HTML.[4][5]

### References[1]
- TryHackMe room overview, task instructions, and banner answer language.[1]
- Community/demo walkthroughs confirming endpoints and the “bank-hacked” banner string.[3]

Notes:
- The provided answers as seen in the room are Offensive Security and bank-hacked.[3][1]
- If using a different wordlist filename or location, adjust the -w argument accordingly.[2]

