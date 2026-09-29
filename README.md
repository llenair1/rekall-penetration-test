# Rekall penetration test

In 2024, I completed a penetration-testing project in UC Berkeley's cybersecurity bootcamp. Rekall was a fictional company with a web application and Linux and Windows systems. I wrote a report covering reconnaissance, vulnerability scanning, exploitation, and recommended fixes.

This repo shows two parts of that work with evidence I can share publicly.

| What I found | Evidence | What it proves |
|---|---|---|
| Several live hosts and services in the lab network | [Nmap scan](evidence/reconnaissance/01-nmap-service-enumeration-sanitized.png) | Service enumeration, including HTTP, SSH, FTP, and VNC. |
| A critical Apache Struts alert | [Nessus result](evidence/reconnaissance/02-nessus-critical-vulnerability-sanitized.png) | The scanner flagged a possible remote code execution issue. I have not shown a successful exploit of this Struts finding. |
| A shell on a Tomcat host | [Sanitized session capture](evidence/exploitation/tomcat-root-shell-sanitized.png) | The active lab session returned `uid=0(root)`. This was a different target from the Struts scan. |

**[Read the two findings and recommended fixes](docs/findings-summary.md).** For the original report, redactions, and what the captures do not establish, see the [evidence notes](docs/evidence-notes.md).

This was an authorized class lab, not a client engagement. The consulting company and job title in the course report were fictional scenario details. I am responsible for the evidence and conclusions shown here. I kept the original report and screenshots separate from this public repo because they contain credentials and course flags.
