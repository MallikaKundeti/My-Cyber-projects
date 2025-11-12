🕵️‍♀️ Mini Nmap Reconnaissance Practice Challenge

🔎 Summary

I ran a few Nmap scans on my Kali VM to explore local ports and services. Since this was a controlled environment (127.0.0.1), it was mainly a practice exercise to get familiar with scanning options like service detection (-sV) and default scripts (-sC).


🧩 Scans & Findings

1️⃣ Basic scan:

nmap -T4 -Pn 127.0.0.1


Checked all 1000 TCP ports quickly.

Result: All ports are closed. 

2️⃣ Service version detection:

nmap -sV -T4 -Pn 127.0.0.1 | tee nmap_sv.txt


Probed for service versions on open ports.

Result: Still no open ports, so no services detected.

Output saved in nmap_sv.txt for record-keeping. ✅

3️⃣ Service detection + default scripts:

nmap -sC -sV -T4 -Pn 127.0.0.1 | tee nmap_scsv.txt


Ran default scripts (-sC) along with service detection.

Result: Again, all ports closed — scripts didn’t have anything to scan.

Output saved in nmap_scsv.txt for reference.

✨ Quick Stats / Observations:

All scanned ports on localhost were closed.

No active services detected — perfect for a safe lab environment.

Learned how to combine flags like -sV + -sC and save outputs with tee.

💡 Assessment:
Even though nothing was open locally, this practice helps build the mindset for real-world reconnaissance:

Know which ports/services are available before planning further analysis.

Always save scan outputs to compare results over time.

📝 Recommendations / Next Steps:

Try scanning a VM or lab container with intentionally open ports.

Experiment with Nmap scripts (--script) for info gathering or vulnerability detection.

Practice parsing outputs to include in reports — makes your findings look clean and professional.

📎 Saved Evidence / Output Files:

nmap_sv.txt

nmap_scsv.txt

🏁 Outcome:

Learned Nmap basics on a local host.

Practiced using flags, default scripts, and saving output.

Ready to scale this workflow for real lab environments or future penetration-testing exercises.
