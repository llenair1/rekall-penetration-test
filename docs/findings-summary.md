# Two findings from the Rekall lab

The [Nmap scan](../evidence/reconnaissance/01-nmap-service-enumeration-sanitized.png) gave me a starting map of the lab network. It showed live hosts and services, including HTTP, SSH, FTP, and VNC. The findings below came from **different hosts**. They are not steps in one attack chain.

## 1. Apache Struts alert

The [Nessus capture](../evidence/reconnaissance/02-nessus-critical-vulnerability-sanitized.png) shows plugin **97610** reporting a Critical Jakarta Multipart Parser remote code execution issue in certain Apache Struts versions.

**What I can conclude:** Nessus flagged the host for investigation. The public evidence does not confirm the installed Struts version or show code execution on that host. A scanner alert is a lead, not a confirmed compromise.

**Recommended fix:** Check the deployed version and configuration, update any affected Struts component to a fixed supported release, then scan and test again. Limit exposure while the issue is being checked. The report recommended an update; I have no evidence that a fix or retest was completed.

## 2. Tomcat shell access

The original report includes one capture of Metasploit's `multi/http/tomcat_jsp_upload_bypass` module opening a command shell. A second capture shows an active `java/linux` session. In the [sanitized session image](../evidence/exploitation/tomcat-root-shell-sanitized.png), `id` returns `uid=0(root) gid=0(root) groups=0(root)`, and `pwd` returns `/usr/local/tomcat`.

**What I can conclude:** The active session had root privileges on that lab host. The two captures have different session numbers, so I cannot establish that they show one uninterrupted run. They do not prove persistence or access to another host. The report names a CVE, but these captures alone do not verify the exact version or CVE.

**Recommended fix:** Patch the affected Tomcat deployment, restrict or remove unnecessary deployment features, limit administrative access, and run the service with the least privilege it needs. Retest the specific path after changes. The lab report proposed fixes; it does not show their implementation.

The [evidence notes](evidence-notes.md) explain the source report, sanitization, and attribution.
