🛡️ Mini IOC (Indicators of Compromise) Tracking Project

🔎 Summary

In this mini project, I created a simple CSV-based IOC tracker to log domains and IPs from various sources. The goal was to practice tracking potentially suspicious activity — like phishing attempts, SSH anomalies, or suspicious domains — while keeping everything structured and easy to read.

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

* Using a structured CSV makes tracking IOCs fast and repeatable.

* Status labels (benign, under review, blocked) help prioritize investigation.

* Adding “Notes” provides context — crucial for understanding why an indicator is flagged.

* Practicing this locally with demo/training data helps build SOC-like workflows safely.

💡 Assessment & Next Steps:

* This tracker is lightweight but effective for small-scale IOC monitoring.

📎 Evidence / Output:

https://github.com/MallikaKundeti/My-Cyber-projects/blob/a425a2c18d75c2fade980a7ec5fbd389a9178600/Screenshot%20(708).png
https://github.com/MallikaKundeti/My-Cyber-projects/blob/a425a2c18d75c2fade980a7ec5fbd389a9178600/Screenshot%20(709).png
https://github.com/MallikaKundeti/My-Cyber-projects/blob/a425a2c18d75c2fade980a7ec5fbd389a9178600/Screenshot%20(710).png
https://github.com/MallikaKundeti/My-Cyber-projects/blob/a425a2c18d75c2fade980a7ec5fbd389a9178600/Screenshot%20(711).png
https://github.com/MallikaKundeti/My-Cyber-projects/blob/a425a2c18d75c2fade980a7ec5fbd389a9178600/Screenshot%20(712).png


🏁 Outcome:

* Learned how to create a clean, structured IOC tracker using bash tools.

* Practiced categorizing and annotating indicators.

* Ready to scale this approach for bigger threat-intel or lab exercises.
