🧾 Personal cybersecurity mini-project focused on email header analysis and phishing triage.

🔎 Summary

This was a quick but fun little email-header deep dive I did using Kali Linux inside a VMware lab setup. The goal was to figure out whether a random promotional email I got was real or just a sneaky phishing attempt. 
I saved the raw header, pulled it apart with grep, and then used tools like whois and dig to trace where it actually came from. From there, I checked the sender info, authentication results (SPF, DKIM, DMARC), and delivery path to see if anything seemed off. 
Basically, a mini investigation to sharpen my phishing triage skills 👩🏻‍💻!

🧰 Tools & Commands Used

All the work was done inside a Kali terminal using simple Linux utilities:

Purpose	Command(s) Used
* View header file	cat header.txt / nano header.txt
* Extract specific header fields	grep -i 'from:' header.txt / grep -i 'spf=' header.txt etc.
* Domain info lookup	whois replit.com
* DNS and mail record lookups	dig +short A mail.replit.com / dig +short A sparkpostmail.com / dig +short -x 168.203.32.122
* Advanced validation (follow-up tests)	dig +short TXT replit.com, dig +short MX replit.com, dig +short TXT 20250624._domainkey.mail.replit.com, whois sparkpostmail.com

* All commands were executed successfully and results were consistent with legitimate Replit and SparkPost infrastructure.

🧩 Findings

* Sender information:

 -> From: Replit contact@mail.replit.com

 -> Return-Path: <…@bounce.replit.com>

 -> Reply-To: contact@replit.com

  Both addresses belong to Replit’s domain space, showing no spoof or mismatch.

* Authentication results:

 -> SPF: pass ✅ — the IP 168.203.32.122 is authorized for the sender domain.

 -> DKIM: pass ✅ — header.i=@mail.replit.com confirmed the cryptographic signature.

 -> DMARC: pass ✅ — enforced by p=REJECT, meaning the brand has strict anti-spoofing policy.

* Delivery path:

 -> Message routed via mta-203-32-122.sparkpostmail.com (168.203.32.122).

 -> Reverse DNS lookup confirmed this host belongs to SparkPost, a trusted bulk email service.

 -> Additional IPs for sparkpostmail.com (18.161.229.13/18/19/76) align with Amazon AWS infrastructure used by SparkPost.

* WHOIS results (replit.com):

 -> Registrar: Nom-iq Ltd. dba COM LAUDE

 -> Created: 2011-09-02 | Expires: 2029-09-02

 -> Nameservers: CODY.NS.CLOUDFLARE.COM, IVY.NS.CLOUDFLARE.COM
 
  These details match Replit’s official registration records, confirming domain legitimacy.

* WHOIS results (sparkpostmail.com):

 -> Registered to Message Systems, Inc. (SparkPost)

  Actively maintained and used by various verified companies for transactional emails.

* DNS record checks:

 -> dig +short TXT replit.com → valid SPF and verification records.

 -> dig +short MX replit.com → routes through Google mail servers (standard for Replit).

 -> dig +short TXT 20250624._domainkey.mail.replit.com → valid DKIM public key returned.

* Indicators collected:
  mail.replit.com, replit.com, bounce.replit.com, sparkpostmail.com, 168.203.32.122

|           Purpose                                |                                Command(s) Used                                                     |
|--------------------------------------------------|----------------------------------------------------------------------------------------------------|
| View header file                                 | `cat header.txt` / `nano header.txt`                                                               |
| Extract specific header fields                   | `grep -i 'from:' header.txt` / `grep -i 'spf=' header.txt` etc.                                    |
| Domain info lookup                               | `whois replit.com`                                                                                 |
| DNS and mail record lookups                      | `dig +short A mail.replit.com` / `dig +short A sparkpostmail.com` / `dig +short -x 168.203.32.122` |
| Advanced validation (follow-up tests)            | `dig +short TXT replit.com`, `dig +short MX replit.com`, `dig +short TXT 20250624._domainkey.mail.replit.com`, `whois sparkpostmail.com` |

🧠 Assessment

Risk Level: Low ⚪
All validation checks passed, and headers align with verified domains and senders. The infrastructure matches Replit’s legitimate mail pipeline (Replit → SparkPost → recipient).
No signs of spoofing or manipulation were detected.

The message is likely a legitimate Replit promotional or transactional email, but users should always confirm the intent of the message before interacting with any embedded links.

check 👉: https://github.com/MallikaKundeti/My-Cyber-projects/blob/a2ec497951e28d9584870e040f45215cd11a792a/Screenshot%20(689).png


💡 Recommendations for Users

* If the message matches what you expect (like newsletters or updates), it’s probably safe.

* If it ever asks for sensitive info (passwords, payments, or personal data), don’t click links — instead, go to [replit.com](https://replit.com) directly and verify from there.
  
* Report suspicious messages to IT or your email provider if anything still feels off.

Indicators collected:

* From: Replit <contact@mail.replit.com>
* Return-Path: <…@bounce.replit.com>
* Auth results: spf=pass; dkim=pass (header.i=@mail.replit.com); dmarc=pass (header.from=replit.com)
* Reverse DNS: 168.203.32.122 → mta-203-32-122.sparkpostmail.com, mail.replit.com, replit.com, bounce.replit.com, sparkpostmail.com, 168.203.32.122


📎 Appendix (Evidence Snippets)

* https://github.com/MallikaKundeti/My-Cyber-projects/blob/7ff0e5db91e9bc6e31caf68956997252080dcfe8/Screenshot%20(693).png
* https://github.com/MallikaKundeti/My-Cyber-projects/blob/72a6f26a39cc55e0028d5b6cdf848982410152a6/Screenshot%20(694).png
* https://github.com/MallikaKundeti/My-Cyber-projects/blob/fd1262d7160e9c9f39c80d83c0d6117ab26aa196/Screenshot%20(695).png
* https://github.com/MallikaKundeti/My-Cyber-projects/blob/fd1262d7160e9c9f39c80d83c0d6117ab26aa196/Screenshot%20(696).png
* https://github.com/MallikaKundeti/My-Cyber-projects/blob/fd1262d7160e9c9f39c80d83c0d6117ab26aa196/Screenshot%20(697).png
* https://github.com/MallikaKundeti/My-Cyber-projects/blob/fd1262d7160e9c9f39c80d83c0d6117ab26aa196/Screenshot%20(698).png32.122

🏁 Outcome: Gained practical experience in header analysis, mail authentication mechanisms, and interpreting DNS records — plus built confidence using Linux command-line tools for real-world security checks.










🧾 Mini SSH brute-force detection challenge using log parsing tools (grep, awk, wc)
 
🔎 Summary

* I did this mini log-analysis challenge on my Kali VM to see if I could spot traces of an SSH brute-force attempt. 

* Since my /var/log/auth.log didn’t have real traffic, I made up a small demo file (demo_auth.log), with a few realistic login entries — both failed and successful ones.
    
   -> Here's how I did that 👉 https://github.com/MallikaKundeti/My-Cyber-projects/blob/e9a0369a30f629749a257d7c1be98e3f5d382bfe/Screenshot%20(701).png


* From there, I used command-line tools like grep, awk etc to count failed logins, find which IPs were behind them, and see which user accounts they were trying to break into. 

 
🧩 Findings 

Nov 12 10:01:02 kali sshd: Failed password for invalid user admin from 203.0.113.10 port 54321 ssh2  
Nov 12 10:01:07 kali sshd: Failed password for root from 198.51.100.23 port 51111 ssh2  
Nov 12 10:02:15 kali sshd: Accepted password for mallika from 203.0.113.10 port 54321 ssh2  
Nov 12 10:05:00 kali sshd: Failed password for root from 203.0.113.10 port 60001 ssh2  


✨ Quick stats:

* Failed logins → 3

* Successful logins → 1

* Repeat offender → 203.0.113.10 (2 attempts)

* Accounts hit → root (2), admin (1)

* The repeat attempts from one IP — especially targeting root — look exactly like early brute-force noise that sysadmins keep an eye out for.


🧠 Assessment

Risk level: Medium ⚠️ (for demo)

Even though this was a handcrafted dataset, it mimics real-world SSH brute-force behavior — multiple failed attempts from the same IP and privileged-account targeting. These patterns would usually trigger automated defenses like fail2ban or IP-based blocks.


💡 Recommendations

* Disable direct root SSH login (PermitRootLogin no in /etc/ssh/sshd_config).

* Use SSH keys instead of passwords for remote access.

* Install fail2ban or similar tools to ban repeat offenders automatically.

* Keep monitoring /var/log/auth.log for recurring failed attempts.

🧰 Tools & Commands Used

|       Purpose	                                                      |                                                  Command(s) Used                           
|---------------------------------------------------------------------|------------------------------------------------------------------------------------------|
|Create demo log file	                                                | cat > demo_auth.log << 'EOF' ... EOF                                                     |                                                                      
|Preview file contents                                                |	head -n 5 demo_auth.log / tail -n 10 demo_auth.log                                       |                                                                              
|Count failed logins	                                                 | grep "Failed password" demo_auth.log | wc -l                                             |                                                                            
|Count accepted logins	                                               | grep "Accepted password" demo_auth.log | wc -l                                           |                                                                               
|Find attacking IPs	                                                  | grep "Failed password" demo_auth.log | awk '{print $(NF-3)}' | sort | uniq -c | sort -nr |                                            
|Show timestamps of failures                                          |	grep "Failed password" demo_auth.log | awk '{print $1,$2,$3,$(NF-3)}'                    |                                                   
|List failed users                                                    |	grep "Failed password for" demo_auth.log | awk '{for(i=1;i<=NF;i++) if($i=="for"){print $(i+1);break}}' | sort | uniq -c | sort -nr |

|Quick summary line                                                   |	echo -n "Fails: "; grep -c "Failed password" demo_auth.log; echo -n "Accepts: "; grep -c "Accepted password" demo_auth.log |      
 

📎 Appendix (Evidence Snippets)

https://github.com/MallikaKundeti/My-Cyber-projects/blob/8e899d34539d1e0d274a010f52466d81a18629c5/Screenshot%20(700).png
https://github.com/MallikaKundeti/My-Cyber-projects/blob/8e899d34539d1e0d274a010f52466d81a18629c5/Screenshot%20(701).png

🏁 Outcome

* Built a small but realistic SSH log dataset.
* Practiced parsing Linux authentication logs manually.
* Used text-processing tools to detect potential brute-force attempts.
