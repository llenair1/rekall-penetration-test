# Rekall Corporation | penetration-testing lab case study

An authorized, simulated assessment completed during the UC Berkeley Cybersecurity Boot Camp in 2024. This repository presents selected evidence from a course report authored under my name. Rekall was a fictional lab target, not a commercial client. The report's “Quantum Security LLC” and “Lead Penetration Tester” labels were part of the exercise scenario.

## At a glance

I documented reconnaissance, vulnerability assessment, exploitation, and remediation in the original lab report. This public case study focuses on two findings with a clear evidence trail: a **critical Apache Struts scanner result** and a **Tomcat shell session**. The [findings](docs/findings-summary.md) distinguish scanner output from confirmed access and explain the limits of each conclusion.

| Stage | Public evidence | What it shows |
|---|---|---|
| Service enumeration | [Sanitized Nmap capture](evidence/reconnaissance/01-nmap-service-enumeration-sanitized.png) | A service/version scan of a private lab subnet identified live hosts and services, including HTTP, SSH, FTP, and VNC. |
| Vulnerability review | [Sanitized Nessus capture](evidence/reconnaissance/02-nessus-critical-vulnerability-sanitized.png) | Nessus plugin 97610 reported a critical Apache Struts Jakarta Multipart Parser remote-code-execution exposure. This is a scan finding, not proof that code execution occurred on that host. |
| Exploit validation | [Sanitized Tomcat session image](evidence/exploitation/tomcat-root-shell-sanitized.png) and [source notes](docs/evidence-notes.md#tomcat-shell-session) | Screenshots embedded in my original report show a Metasploit Tomcat JSP upload-bypass module opening a shell session, followed by an active session where `id` returned `uid=0(root)`. This is a separate target and path from the Struts scan finding. |

## My contribution and the lab boundary

The [original report](docs/evidence-notes.md#source-and-attribution) records LeVonta Lenair as its author and contains the screenshots behind this case study. It supports my reporting and the recorded lab workflow. The available artifacts do not independently establish whether every lab action was performed alone, so this repository does not claim solo execution or professional client experience.

The report covered additional web, Windows, credential, and Linux exercises. They are not presented as verified public findings here because their evidence has not yet been curated and checked to the same standard. Tools named in this case study are limited to the linked Nmap, Nessus, and Metasploit evidence.

## Read the case study

- [Two evidence-backed findings and remediation analysis](docs/findings-summary.md)
- [Evidence provenance, sanitized transcript, and limitations](docs/evidence-notes.md)

Original report and recovered screenshots are preserved separately. Published excerpts omit passwords, hashes, course flags, and personal information. No testing outside the authorized educational environment is represented.
