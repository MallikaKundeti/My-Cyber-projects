🛡️ Cybersecurity Projects

A collection of hands-on security practice exercises, log analysis notes, and small investigations I’ve been working on.

This repository tracks my learning path as I explore cybersecurity fundamentals using real tools, CLI workflows, and small scenarios. Each project includes a short write-up, screenshots, and the commands I used — all organized to be easy to follow and build on.

```
My-Cyber-projects/
│
├── phishing-header/
│ ├── report.md
│ └── screenshots/
│
├── ssh-log-hunt/
│ ├── report.md
│ └── screenshots/
│
├── nmap-basics/
│ ├── report.md
│ └── screenshots/
│
├── ioc-tracker/
│ ├── report.md
│ └── ioc_tracker.csv
│
└── README.md
```

Each folder contains:

report.md → The write-up for that mini-project

screenshots/ → Evidence, commands, or tool output (when applicable)

data files → Logs, CSVs, or artifacts generated during the exercise

🔍 Projects Overview
1. Email Header Triage (phishing-header/)

A small analysis where I inspected raw email headers to identify:

Sending infrastructure

SPF/DKIM/DMARC alignment

Potential anomalies or spoofing attempts

This helped me practice reading real header fields and spotting common phishing red flags.

2. SSH Brute-Force Log Hunt (ssh-log-hunt/)

I created a lightweight demo auth.log to mimic failed and successful SSH logins.
Using tools like grep, awk, and sort, I analyzed patterns such as:

Repeated failed attempts

Targeted usernames

Suspicious IP repetition

This project reinforced how to interpret Linux authentication logs and detect brute-force behavior.

3. Nmap Localhost Scan Basics (nmap-basics/)

A quick hands-on exploration of basic Nmap modes:

nmap -T4 -Pn

nmap -sV (service detection)

nmap -sC -sV (default scripts + version detection)

All targeted at 127.0.0.1 to understand port states, scan timing, and what Nmap reports when no services are exposed.

4. IOC Tracking Practice (ioc-tracker/)

I built a simple IOC (Indicators of Compromise) tracker in CSV format — useful for organizing findings during investigations.

The table includes:

Domains, IP addresses, Source of discovery, First-seen date, Status (benign / under review / blocked), Notes


🎯 Goal of This Repository

This repo helps me build confidence with:

Basic threat hunting steps

Interpreting logs

Understanding how attackers behave

Using CLI tools effectively

Documenting findings cleanly

I’ll keep expanding this with more small labs, scenarios, and investigations as I learn.

### 🎯 What's Next?

I'm currently pursuing my **Master of Computer Applications (Cybersecurity)** and working toward certifications in network security and ethical hacking. If you have recommendations, corrections, or ideas for new projects or mini-projects, feel free to open an issue or start a discussion.

Stay tuned! 🚀

---

### 🔗 Let’s Connect

Feel free to explore my [LinkedIn profile](https://www.linkedin.com/in/mallika-kundeti-440557317?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=android_app) to know more about my academic journey, internships, and language interests.

