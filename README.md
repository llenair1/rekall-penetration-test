# Rekall Corporation Penetration Test

Authorized educational penetration-testing case study completed in a controlled lab environment as part of the UC Berkeley Cybersecurity Boot Camp.

## Overview

This project documents a multi-stage penetration test against the simulated Rekall Corporation environment. The assessment covered reconnaissance, vulnerability discovery, web application testing, exploitation, credential access, post-exploitation, and privilege escalation across Windows and Linux targets.

The goal of this repository is to present the work as a professional security assessment rather than a collection of raw lab screenshots. Evidence published here will be sanitized to remove credentials, flags, internal lab identifiers, and other unnecessary sensitive-looking data.

## Assessment Objectives

- Identify exposed services and vulnerable systems
- Discover web application weaknesses and information disclosure
- Validate selected vulnerabilities through controlled exploitation
- Evaluate opportunities for credential access and privilege escalation
- Document affected assets, impact, and remediation recommendations
- Preserve an evidence trail showing how findings were validated

## Tools and Techniques

| Area | Tools / Techniques |
|---|---|
| Reconnaissance | WHOIS, GitHub reconnaissance, robots.txt review |
| Network enumeration | Nmap, service/version discovery |
| Vulnerability assessment | Nessus Essentials |
| Web application testing | XSS testing, command injection, file-upload testing, information disclosure review |
| Exploitation | Metasploit Framework, Apache Tomcat exploitation in the lab environment |
| Windows post-exploitation | Meterpreter, Kiwi/Mimikatz, scheduled-task review, SAM credential extraction |
| Password testing | John the Ripper |
| Linux post-exploitation | SSH, sudoers review, privilege-escalation validation |

## Assessment Workflow

### 1. Reconnaissance and Enumeration

The assessment began with external and internal reconnaissance, including domain-registration research, public repository review, port and service enumeration, and vulnerability scanning.

### 2. Web Application Security Testing

Testing identified multiple classes of web application weakness in the lab environment, including:

- Cross-site scripting
- Command injection
- File-upload weaknesses
- Information disclosure
- Exposed credentials and configuration data
- Hidden or sensitive application paths

### 3. Vulnerability Validation and Exploitation

Selected findings were validated in the authorized lab using tools such as Nessus and Metasploit. Exploitation evidence included controlled remote-shell access to vulnerable services.

### 4. Windows Post-Exploitation

Post-exploitation activities included reviewing persistence mechanisms, enumerating compromised hosts, extracting credential material in the lab, and demonstrating the security impact of weak credential controls.

### 5. Linux Privilege Escalation

Linux testing included reviewing sudoers permissions and validating privilege-escalation paths within the authorized environment.

## Key Security Themes

The exercise reinforced several recurring security lessons:

- Internet-facing services should be continuously inventoried and patched.
- Web applications require strong input validation and secure file-handling controls.
- Credentials and configuration secrets should never be exposed in source repositories or application files.
- Least privilege reduces the impact of an initial compromise.
- Logging, vulnerability management, and remediation validation are essential parts of the assessment lifecycle.

## Evidence and Reporting

Recovered project artifacts include evidence from reconnaissance, Nmap and Nessus scanning, web vulnerability testing, Metasploit exploitation, Windows credential-access testing, and Linux privilege escalation.

Only curated and sanitized evidence will be published in this repository. Raw course flags, passwords, hashes, and unnecessary internal lab identifiers will not be included in public screenshots.

Planned repository structure:

```text
rekall-penetration-test/
├── README.md
├── evidence/
│   ├── reconnaissance/
│   ├── web-application/
│   ├── exploitation/
│   ├── windows-post-exploitation/
│   └── linux-privilege-escalation/
└── docs/
    └── findings-summary.md
```

## Ethics and Scope

All testing documented in this repository was performed in an authorized educational lab environment. The material is presented for defensive-security education and professional portfolio purposes.

## Status

**Portfolio reconstruction in progress.** The original project evidence has been recovered and integrity-checked. The next phase is sanitizing selected artifacts and converting the original assessment into a concise recruiter-facing case study.
