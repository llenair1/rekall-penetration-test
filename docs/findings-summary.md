# Representative Findings Summary

This document summarizes representative findings from the authorized Rekall Corporation penetration-testing lab. It is not a reproduction of the full course report and excludes credentials, hashes, course flags, personal information, and unnecessary lab identifiers.

## Representative Findings

| Area | Finding | Risk | Recommended Action |
|---|---|---|---|
| Web application | SQL injection in authentication workflow | Critical | Use parameterized queries, strict server-side validation, and secure authentication controls. |
| Web application | Sensitive data exposed in application source | Critical | Remove hardcoded credentials and sensitive data from client-accessible source, rotate exposed credentials, and enforce secure secret handling. |
| Web application | Command injection | Critical | Enforce strict server-side validation and allow-listing, and prevent untrusted input from reaching operating-system commands. |
| Web application | Brute-force exposure | Critical | Enforce strong password requirements, rate limiting, and account lockout controls. |
| Web application | Local file inclusion / unsafe file handling | Critical | Validate and constrain file paths, restrict permitted file types, and store uploaded content outside the web root. |
| Web application | Stored cross-site scripting | Critical | Validate input, apply contextual output encoding, and use appropriate browser-side protections such as Content Security Policy. |
| Application server | Apache Tomcat remote code execution, CVE-2017-12617 | Critical | Upgrade and patch the affected service, restrict deployment functionality, and validate remediation. |
| Linux system | Shellshock exploitation path | Critical | Patch Bash, restrict CGI exposure, disable unnecessary services, and validate affected systems. |
| Windows environment | Credential-access and lateral-movement opportunities | Critical | Strengthen credential protections, enforce least privilege and segmentation, and monitor post-exploitation activity. |
| Application server | Apache Struts vulnerability identified through Nessus | Critical | Upgrade the affected application framework and apply relevant security patches. |
| Credential security | Credentials exposed through public source material | Critical | Remove sensitive material from source control, rotate exposed credentials, and use managed secret storage and repository scanning. |
| Linux system | Privilege-escalation path | Critical | Review SSH and sudo permissions, remove unnecessary elevated access, and enforce least privilege. |
| Web application | Advanced local file inclusion | High | Apply secure coding practices, strict validation and sanitization, file-type restrictions, and safer upload storage. |
| Web application | Advanced command injection | High | Combine server-side validation with allow-listing, regular testing, and code review. |
| Web application | Sensitive information exposed through robots.txt | High | Keep sensitive paths and information out of publicly accessible crawler directives. |
| Windows service | Open FTP service | High | Restrict FTP exposure, disable anonymous access, require strong authentication, and keep the service patched. |

## Notes on Severity Counts

The final report contains a summary table listing 14 Critical and 7 High findings, while the detailed findings section visible in the report contains 17 documented entries. Because those sections do not reconcile cleanly, this public summary intentionally avoids publishing an aggregate vulnerability count.

## Assessment Approach

The assessment followed the methodology documented in the final report:

1. Reconnaissance
2. Identification of vulnerabilities and services
3. Vulnerability exploitation
4. Reporting

[View scope and methodology](scope-methodology.md)

## Evidence Handling

Only curated, sanitized evidence is intended for publication in this repository. Original assessment artifacts are preserved separately and are not included here.

> All testing was performed in an authorized educational lab environment.
