🕵️‍♀️ Mini Nmap Scan Practice Challenge

🔎 Summary

I ran a few Nmap scans on my Kali VM to explore local ports and services. Since this was a controlled environment (127.0.0.1), it was mainly a practice exercise to get familiar with scanning options like service detection (-sV) and default scripts (-sC).

🧩 Scans & Findings

1️⃣ Basic scan:

* nmap -T4 -Pn 127.0.0.1

 -> Checked all 1000 TCP ports quickly.

 -> Result: All ports are closed. 

2️⃣ Service version detection:

* nmap -sV -T4 -Pn 127.0.0.1 | tee nmap_sv.txt

 -> Probed for service versions on open ports.

 -> Result: Still no open ports, so no services detected.


3️⃣ Service detection + default scripts:

* nmap -sC -sV -T4 -Pn 127.0.0.1 | tee nmap_scsv.txt

 -> Ran default scripts (-sC) along with service detection.

 -> Result: Again, all ports closed — scripts didn’t have anything to scan.

✨ Observations:

* All scanned ports on localhost were closed.

* No active services detected — perfect for a safe lab environment.

* Learned how to combine flags like -sV + -sC and save outputs with tee.

💡 Assessment:

* Even though nothing was open locally, this practice helps build the mindset for real-world reconnaissance.

* Know which ports/services are available before planning further analysis.

* Always save scan outputs to compare results over time.


📎 Saved Evidence / Output Files:

https://github.com/MallikaKundeti/My-Cyber-projects/blob/49abd8a0700deeb6e8f7c51ee57a31d7b33be209/Screenshot%20(703).png

🏁 Outcome:

* Learned Nmap basics on a local host.

* Practiced using flags, default scripts, and saving output.

* Ready to scale this workflow for real lab environments or future penetration-testing exercises.
