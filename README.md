Password Cracking Lab — JTR & Networkwalks Tools

Cybersecurity & Ethical Hacking Project Task | Week 3

This repository documents the completion of two related lab exercises on password cracking, both performed against the same password-protected PDF file (My Locked PDF1.pdf). The goal is to understand how password hashes are extracted from protected files and how cracking tools recover the original password.

📌 Objective
Understand how files (PDF, ZIP, Office docs) store password protection as a hash.
Learn how to extract a crackable hash from a protected file.
Use both an industry-standard offline tool (John the Ripper / Johnny) and Networkwalks' free online tools (Hash Calculator + Password Cracker) to recover the password.
Reinforce why short/common passwords are insecure.

🧰 Tools Used
Tool	Purpose
John the Ripper (JTR)	Command-line password cracking tool
Johnny	GUI front-end for John the Ripper
Online Hash Extractor (onlinehashcrack.com)	Extracts a $pdf$... hash from a locked PDF
Networkwalks Hash Calculator	Browser-based tool to extract the PDF hash locally
Networkwalks Password Cracker	Browser-based dictionary attack tool
Notepad	Used to save the extracted hash as a .txt file
📄 Target File
File: My Locked PDF1.pdf
Protection type: Password-protected PDF (Document Open Password)

Method 1 — Cracking with John the Ripper (JTR) & Johnny

Step 1 — Install JTR

Download John the Ripper for Windows from one of:

https://www.openwall.com/john/
https://distro.ibiblio.org/openwall/projects/john/1.9.0/

Kali Linux users: JTR comes pre-installed, so this step can be skipped.

Step 2 — Install Johnny (GUI)

Download Johnny from:

https://openwall.info/wiki/john/johnny

Run the installer and launch Johnny from the desktop/start menu.

Step 3 — Point Johnny to John's executable
Open Johnny → Settings.
Click Browse next to "John the Ripper executable".
Navigate to the run folder inside the extracted JTR package and select john.exe.
Johnny should now report the detected John the Ripper version.

Step 4 — Extract the hash from the PDF
Go to the PDF hash extractor: https://www.onlinehashcrack.com/tools-pdf-hash-extractor.php
Browse to My Locked PDF1.pdf and click Upload.
Copy the full output hash (it must start with $pdf$).
⚠️ If the hash is copied with stray characters like a leading b', remove them before saving.

Step 5 — Save the hash to a text file
Open Notepad, paste the hash.
Save the file as hash1.txt.

Step 6 — Load the hash into Johnny
In Johnny, click Open password file (PASSWD format).
Browse to hash1.txt and open it.

Step 7 — Run the attack
Click Start new attack.
Johnny will run John the Ripper against the hash until it finds a match (time depends on password complexity and system speed).

Step 8 — Recover and use the password

Once cracked, the password is displayed next to the hash entry in Johnny.

<img width="879" height="693" alt="image" src="https://github.com/user-attachments/assets/e087ffe8-6afb-4bc2-bda7-2249f4d0693e" />


Step 9 — Open the PDF

Open My Locked PDF1.pdf in a PDF reader, enter password1 when prompted, and the document unlocks.

<img width="1375" height="1016" alt="image" src="https://github.com/user-attachments/assets/6e6cc261-7bf8-4484-a700-e38021f9542c" />

Method 2 — Cracking with Networkwalks Hash Calculator & Password Cracker

This method uses two free browser-based tools built by Networkwalks — no installation required.

Step 1 — Get the target file

Download My Locked PDF1.pdf from the lab page: https://networkwalks.com/project-task-lab-password-cracking-with-networkwalks-tools/

Step 2 — Open the Hash Calculator

https://networkwalks.com/hash-calculator/
<img width="1375" height="959" alt="image" src="https://github.com/user-attachments/assets/b39eb850-fb63-4f44-b4c6-6eb1b083dd4c" />


Step 3 — Extract the hash

Upload the locked PDF to the PDF tab of the Hash Calculator. It will parse the file locally in-browser and return a hash starting with $pdf$....

Step 4 — Copy the hash

Copy the complete hash value (starting from $pdf$) — don't truncate it.

Step 5 — Open the Password Cracker

https://networkwalks.com/password-cracker/

Step 6 — Run the attack
Paste the hash into the PDF HASH field.
Choose a wordlist — either the built-in 100-password list or upload a custom .txt wordlist.
Click Start Cracking.

The tool performs a dictionary attack, trying each word from the list against the hash.

Step 7 — Get the result

Once a match is found, the tool displays:

<img width="798" height="1004" alt="image" src="https://github.com/user-attachments/assets/ee8597a4-9101-4d54-89d6-06f9abe0537b" />


PASSWORD CRACKED SUCCESSFULLY
password1
Step 8 — Open the PDF

Open My Locked PDF1.pdf, enter password1 at the Document Open Password prompt.

Step 9 — Done

The PDF opens and confirms the flag has been captured.

✅ Result
<img width="919" height="1004" alt="image" src="https://github.com/user-attachments/assets/b3e08c33-fa2c-4108-a491-69220944a6d5" />

Both methods — the industry-standard John the Ripper / Johnny workflow and the lightweight Networkwalks Hash Calculator / Password Cracker workflow — successfully recovered the same password:

password1

This demonstrates how a dictionary attack can trivially crack a weak, common password, regardless of which tool performs the attack.

🔑 Key Takeaway

Encryption is two-way (reversible with the right key); hashing is one-way. Password cracking works by hashing candidate words and comparing them against the stored hash until a match is found. Short, common passwords like password1 fall almost instantly — strong, long, random passwords are the real defense.

📚 References
John the Ripper: https://www.openwall.com/john/
Johnny GUI: https://openwall.info/wiki/john/johnny
Networkwalks Hash Calculator: https://networkwalks.com/hash-calculator/
Networkwalks Password Cracker: https://networkwalks.com/password-cracker/
Online PDF Hash Extractor: https://www.onlinehashcrack.com/tools-pdf-hash-extractor.php
⚠️ Disclaimer

This lab is for educational purposes only, performed against a file provided specifically for this exercise. Password cracking techniques must only be used on systems/files you own or are explicitly authorized to test. Unauthorized access to protected data is illegal.


# 👤 Author

**liam ndiva**\
Cybersecurity Professional B084

LinkedIn: https://www.linkedin.com/feed/

---

## 📌 Project Information

**Program Name:** Cybersecurity at Networkwalks | **Week:** 01 | **Project:** Cybersecurity & Pentesting Lab Setup | **Repository:** GitHub
