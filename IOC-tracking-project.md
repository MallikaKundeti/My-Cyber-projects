🛡️ Mini IOC (Indicators of Compromise) Tracking Project

🔎 Summary

In this exercise, I created a simple CSV-based IOC tracker to log domains and IPs from various sources. The goal was to practice tracking potentially suspicious activity — like phishing attempts, SSH anomalies, or suspicious domains — while keeping everything structured and easy to read.

I used the printf command to populate the CSV and then column -t to get a neat, tabulated view. This helps mimic how SOC analysts or security teams maintain IOC logs in a real environment.

🧩 Tracked Indicators & Findings

| Indicator                | Type   | Source            | First_Seen  | Status        | Notes                                      |
|--------------------------|--------|-----------------|------------|--------------|--------------------------------------------|
| mail.replit.com           | domain | header triage    | 2025-11-12 | benign       | Brand sending domain                        |
| replit.com                | domain | header triage    | 2025-11-12 | benign       | Primary brand domain                         |
| bounce.replit.com         | domain | header triage    | 2025-11-12 | benign       | Bounce/return path domain                    |
| sparkpostmail.com         | domain | header triage    | 2025-11-12 | benign       | Email delivery platform                      |
| 168.203.32.122            | ip     | reverse dns      | 2025-11-12 | benign       | Reverse to sparkpostmail                     |
| 203.0.113.10              | ip     | ssh demo log     | 2025-11-12 | under review | Repeated failed SSH logins                   |
| 198.51.100.23             | ip     | ssh demo log     | 2025-11-12 | under review | Single failed SSH login                       |
| bad-login.example         | domain | training sample  | 2025-11-13 | under review | Suspicious sign-in domain lookalike         |
| login-secure.example      | domain | training sample  | 2025-11-13 | under review | Possible phishing lookalike                  |
| update-portal.example     | domain | training sample  | 2025-11-13 | under review | Generic lure name                            |
| 45.12.34.56               | ip     | open intel search| 2025-11-13 | blocked      | Added to test blocklist                      |
| 91.210.15.7               | ip     | open intel search| 2025-11-13 | under review | Seen in noisy login attempts                 |
| docs-login-example.net    | domain | open intel search| 2025-11-13 | under review | Potential doc lure                           |
| dl-update-example.net     | domain | open intel search| 2025-11-13 | under review | Potential download lure                      |
| cdn-assets-example.net    | domain | open intel search| 2025-11-13 | benign       | Likely static asset host                      |


✨ Quick Observations:

Using a structured CSV makes tracking IOCs fast and repeatable.

Status labels (benign, under review, blocked) help prioritize investigation.

Adding “Notes” provides context — crucial for understanding why an indicator is flagged.

Practicing this locally with demo/training data helps build SOC-like workflows safely.

💡 Assessment & Next Steps:

This tracker is lightweight but effective for small-scale IOC monitoring.

Next, I can experiment with automatic enrichment (like pulling ASN info for IPs or WHOIS data for domains) to make the tracker smarter.

Could also implement sorting/filtering scripts to quickly see “under review” vs “blocked” indicators.

📎 Evidence / Output:

CSV created: ioc_tracker.csv

Pretty tabulated view using:

column -s, -t ioc_tracker.csv | less -S


🏁 Outcome:

Learned how to create a clean, structured IOC tracker using bash tools.

Practiced categorizing and annotating indicators.

Ready to scale this approach for bigger threat-intel or lab exercises.
