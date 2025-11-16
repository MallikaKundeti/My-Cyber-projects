🔐 Password Strength Analyzer + Breach Check (Mini Cybersecurity Project)

🧾 Personal cybersecurity mini-project focused on password strength evaluation and leaked-password detection.

🔎 Summary

This was a hands-on password-analysis project I built using Python on a Kali Linux VM (running inside VMware). The goal was simple:
➡️ Check how strong a list of passwords really is, and
➡️ Verify whether any of them appear in a real leaked-password dataset (rockyou.txt).

I wrote a Python script that reads password inputs, analyzes complexity, checks them against the breach list, and then exports everything into a clean CSV report. Basically a compact password-audit tool to sharpen my Python, regex, and Linux skills 🔥👩🏻‍💻.

🧰 Tools & Technologies Used

All work was done inside a Kali terminal using Python + basic Linux utilities:


| Purpose                         | Tools / Commands Used                 |
| ------------------------------- | ------------------------------------- |
| Script editing                  | `nano password_analyzer.py`           |
| View input files                | `cat passwords.txt`                   |
| Analyze password fields (regex) | Python `re` module                    |
| Cross-check passwords           | `rockyou.txt` wordlist                |
| Run the tool                    | `python3 password_analyzer.py`        |
| Export results                  | Writes output → `password_report.csv` |
| OS environment                  | Kali Linux VM (VMware Workstation)    |

🧠 Assessment

Everything executed smoothly and processed the sample list instantly.

🧩 How It Works
🔍 Password Analysis

For each password, the script checks:

Length

Uppercase/lowercase usage

Digits

Special characters

Overall complexity score → Weak / Medium / Strong

🔥 Breach Check

The script performs a lookup inside rockyou.txt, one of the most commonly referenced leaked-password lists.

If a password exists in the breach list, it’s flagged as Breached: YES ⚠️.

🗂 Output Format

The final CSV includes:

Password

Strength rating

Breached (Yes/No)

Notes (e.g., “Weak – appears in breach list”)

🧠 Results & Observations

Weak passwords like "qwerty" and "password123" were immediately flagged as breached ⚠️

Strong passwords with symbols, mixed case, and good length passed with “Strong” ratings

The script processed all sample passwords in under one second ⚡

Workflow proves scalable for larger datasets

💡 What I Learned

Practical Python scripting with regex and file handling

Working with large breach datasets in Linux environments

Why password complexity + breach awareness both matter

Automating reports for security assessments

Structuring scripts for real-world cybersecurity use cases

🚀 Future Enhancements

🔧 Things I’d like to add:
Entropy-based scoring for more accurate strength metrics

GUI or simple web dashboard

Multi-threading for faster breach checks

Support for API-based live breach lookups

Automatic strong-password suggestions

📎 Appendix (Evidence)

password_report.csv (generated output)

passwords.txt sample input

Python script: password_analyzer.py

Screenshots of terminal execution and CSV generation
(You can upload these to your GitHub repo just like your other project!)

🏁 Outcome

A fun and practical mini-project that strengthened my understanding of password security, Python automation, and handling real-world breach data. Plus, it’s a great foundational tool for security assessments and future blue-team projects 🔐💙.
