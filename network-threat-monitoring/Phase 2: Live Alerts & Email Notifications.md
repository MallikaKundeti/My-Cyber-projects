Network Threat Monitoring System – Phase 2 Report

Project Goal: Enhance the network monitoring tool to provide real-time alerts for suspicious SSH activity and optional email notifications, while preventing duplicate alerts.

Environment Setup

OS: Kali Linux (VM)

Tools & Languages: Python 3, Bash/Linux commands, Wireshark/Tshark

Project Folder Structure:
network_monitor/
├── logs/          # Stores detected events
├── scripts/       # Python scripts for monitoring
│   ├── monitor.py       # Main SSH brute-force detection script
│   └── email_alerts.py  # Optional email alert module
└── logs/ssh_alerts.csv   # CSV log of detected events

Milestone 2: Real-Time Alerts + Email Notifications

Objective:

Detect repeated failed SSH login attempts in real-time.

Print live alerts in the terminal.

Optionally send email notifications for threshold-crossing attempts.

Prevent duplicate alerts for the same IP.

Continue updating the CSV log.

Implementation Details

1. Real-Time Monitoring (monitor.py):

Uses subprocess.Popen to run journalctl -u ssh -f --no-pager in follow mode, reading SSH logs as they occur.

Counts failed login attempts per IP and maintains a seen_alerts set to prevent duplicates.

Prints live alerts in terminal when the threshold (e.g., 3 failed attempts) is crossed.

Updates CSV log continuously.

Key Code Snippets:

```
# Track failed attempts and print live alerts
def print_alerts(failed_ips):
    for ip, count in failed_ips.items():
        if count >= THRESHOLD and ip not in seen_alerts:
            print(f"🚨 ALERT! Possible brute-force detected from {ip} — {count} failed attempts.")
            seen_alerts.add(ip)
            send_email_alert(ip, count)  # optional email alert
    save_to_csv(failed_ips)  # update CSV
``` 
2. Email Notifications (email_alerts.py):

Uses Gmail SMTP for email alerts.

Sends alert messages to a secondary email when threshold is crossed.

Uses app password for authentication (more secure than main password).

```
# Send alert via Gmail SMTP
def send_email_alert(ip, count):
    msg = f"Subject: SSH Alert\n\nDetected {count} failed SSH login attempts from {ip}."
    with smtplib.SMTP_SSL("smtp.gmail.com", 465) as server:
        server.login(FROM_ADDRESS, APP_PASSWORD)
        server.sendmail(FROM_ADDRESS, TO_ADDRESS, msg)
```

Testing

Open a new terminal in Kali Linux.

Simulate failed SSH login attempts:
```
ssh wronguser@localhost
```
Observe live terminal alerts:
```
🚨 ALERT! Possible brute-force detected from ::1 — 3 failed attempts.
```
Verify email notifications (sent to secondary email).

Check CSV updates:
```
cat logs/ssh_alerts.csv
```

Achievements – Milestone 2

✅ Real-time detection of SSH brute-force attempts.
✅ Live terminal alerts for immediate visibility.
✅ Optional email notifications successfully triggered.
✅ Duplicate alerts prevented per IP.
✅ Continuous CSV logging maintained.

Evidences: 

https://github.com/MallikaKundeti/My-Cyber-projects/blob/20ca89e0f37a5f24d3b44d895d4f09744e54e19f/NTM%20M2%20%20(1).png
https://github.com/MallikaKundeti/My-Cyber-projects/blob/20ca89e0f37a5f24d3b44d895d4f09744e54e19f/NTM%20M2%20(2).png
https://github.com/MallikaKundeti/My-Cyber-projects/blob/20ca89e0f37a5f24d3b44d895d4f09744e54e19f/NTM%20M2%20(3).png
https://github.com/MallikaKundeti/My-Cyber-projects/blob/20ca89e0f37a5f24d3b44d895d4f09744e54e19f/NTM%20M2%20(4).png
https://github.com/MallikaKundeti/My-Cyber-projects/blob/20ca89e0f37a5f24d3b44d895d4f09744e54e19f/NTM%20M2%20(5).png
https://github.com/MallikaKundeti/My-Cyber-projects/blob/20ca89e0f37a5f24d3b44d895d4f09744e54e19f/NTM%20M2%20(6)%20.png
https://github.com/MallikaKundeti/My-Cyber-projects/blob/20ca89e0f37a5f24d3b44d895d4f09744e54e19f/NTM%20M2%20%20(7).png
https://github.com/MallikaKundeti/My-Cyber-projects/blob/20ca89e0f37a5f24d3b44d895d4f09744e54e19f/NTM%20M2%20%20(8).png
