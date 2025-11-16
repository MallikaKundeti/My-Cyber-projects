Network Threat Monitoring System – Milestone 1 Report :

Project Goal:
Build a local network monitoring tool in Kali Linux to detect suspicious activity, specifically SSH brute-force attempts, log events, and store them for analysis.

Environment Setup

OS: Kali Linux (VM)

Tools & Languages: Python 3, Bash/Linux commands, Wireshark/Tshark

Project Folder Structure:
network_monitor/
├── logs/                 # Stores detected events
├── scripts/              # Python scripts for monitoring
└── monitor.py            # Main SSH brute-force detection script

Milestone 1: SSH Brute-Force Detection
Objective:

Detect repeated failed SSH login attempts and log them in a CSV file for easy analysis.

Implementation Details:

Python Script (monitor.py):

Reads /var/log/auth.log for failed login attempts.

Counts failed attempts per IP address.

Saves results in a CSV file (logs/ssh_alerts.csv) with columns: IP and Failed_Attempts.

Key Code Snippets:

```
# Count failed SSH attempts
def check_ssh_log():
    suspicious_ips = {}
    with open(log_file, "r") as f:
        for line in f:
            if "Failed password" in line:
                ip = line.split()[-4]
                suspicious_ips[ip] = suspicious_ips.get(ip, 0) + 1
    return suspicious_ips

# Save results to CSV
def save_to_csv(suspicious_ips):
    with open(csv_file, "w", newline="") as csvfile:
        writer = csv.writer(csvfile)
        writer.writerow(["IP", "Failed_Attempts"])
        for ip, attempts in suspicious_ips.items():
            writer.writerow([ip, attempts])
```
Testing

Open a new terminal in Kali Linux.

Simulate failed SSH attempts:
```
ssh wronguser@localhost
```
Check CSV file updates:
```
cat logs/ssh_alerts.csv
```
Expected Output:
```
IP,Failed_Attempts
127.0.0.1,3
```
Each failed attempt is logged and counted per IP.

Achievements – Milestone 1

✅ Successfully detected SSH brute-force attempts in real-time.

✅ Logged events in CSV for easy tracking and analysis.

✅ First working version of a cybersecurity tool ready for further enhancement.

Evidences: 

https://github.com/MallikaKundeti/My-Cyber-projects/blob/ff45f60d78a391d340e32a8e7a7e6dfe8e755e0f/NTM%20M1%20(1)%20.png
https://github.com/MallikaKundeti/My-Cyber-projects/blob/ff45f60d78a391d340e32a8e7a7e6dfe8e755e0f/NTM%20M1%20(2).png
https://github.com/MallikaKundeti/My-Cyber-projects/blob/ff45f60d78a391d340e32a8e7a7e6dfe8e755e0f/NTM%20M1%20%20(3).png
https://github.com/MallikaKundeti/My-Cyber-projects/blob/ff45f60d78a391d340e32a8e7a7e6dfe8e755e0f/NTM%20M1%20(4).png
https://github.com/MallikaKundeti/My-Cyber-projects/blob/ff45f60d78a391d340e32a8e7a7e6dfe8e755e0f/NTM%20M1%20(5).png
https://github.com/MallikaKundeti/My-Cyber-projects/blob/ff45f60d78a391d340e32a8e7a7e6dfe8e755e0f/NTM%20M1%20(6).png
https://github.com/MallikaKundeti/My-Cyber-projects/blob/ff45f60d78a391d340e32a8e7a7e6dfe8e755e0f/NTM%20M1%20%20(7).png
https://github.com/MallikaKundeti/My-Cyber-projects/blob/ff45f60d78a391d340e32a8e7a7e6dfe8e755e0f/NTM%20M1%20(8).png
https://github.com/MallikaKundeti/My-Cyber-projects/blob/ff45f60d78a391d340e32a8e7a7e6dfe8e755e0f/NTM%20M1%20(9).png
