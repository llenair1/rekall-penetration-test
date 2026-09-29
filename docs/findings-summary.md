# Selected findings | Rekall lab

These are two distinct findings from an authorized, fictional UC Berkeley bootcamp environment. The original 2024 course report named LeVonta Lenair as author. The public artifacts below show the basis and limits of each conclusion; severity labels from a scanner or course report are not independent production risk ratings.

## 1. Apache Struts exposure reported by Nessus

**Observation.** The [sanitized Nessus screenshot](../evidence/reconnaissance/02-nessus-critical-vulnerability-sanitized.png) shows plugin **97610**, “Apache Struts 2.3.5 - 2.3.31 / 2.5.x < 2.5.10.1 Jakarta Multipart Parser RCE (remote),” rated Critical. The [Nmap service enumeration](../evidence/reconnaissance/01-nmap-service-enumeration-sanitized.png) provides surrounding lab host and service context.

**Validation and limit.** This artifact documents a scanner result. The public evidence does not show a manual proof of code execution on the Struts target, its exact installed version, or a completed retest. Treat the finding as a prioritized exposure requiring confirmation, not as a demonstrated compromise. The original report's corresponding “Nessus Scan” entry describes a Struts vulnerability and recommends updating the component. [Source and attribution](evidence-notes.md#source-and-attribution)

**Risk.** If the affected component and conditions are confirmed, remote code execution could give an attacker the privileges of the application process. The scanner's Critical rating is a triage signal within this lab.

**Recommended action.** Inventory the affected Struts version and deployment, update to a fixed supported release, restrict exposure while remediation is pending, and verify the result with a follow-up scan and appropriate manual checks. This is a recommendation, not a claim that remediation occurred.

## 2. Tomcat shell session in the lab

**Observation.** Two screenshots embedded in my original report show the Metasploit `multi/http/tomcat_jsp_upload_bypass` module reporting a command shell session, then an active `java/linux` shell. In the interactive session, `id` returns `uid=0(root) gid=0(root) groups=0(root)` and `pwd` returns `/usr/local/tomcat`. See the [sanitized evidence excerpt and source description](evidence-notes.md#tomcat-shell-session).

**Validation and limit.** The session and command output support successful shell access with root privileges in this lab capture. They do not establish persistence, access to other hosts, or the precise software version and CVE. The original report labels this finding with CVE-2017-12617, but the available screenshots alone are insufficient to independently verify that identifier. The shell target is separate from the Nessus Struts finding; the two are **not** a single attack chain.

**Risk.** A remotely obtained shell with root privileges would permit full control of that simulated host. The screenshots show access in the exercise, not impact on a real organization.

**Recommended action.** Update Tomcat and affected deployment components, disable unnecessary deployment functions, restrict administrative access, run the service with least privilege, and retest the specific exploit path. These actions were proposed in the report; no completed remediation is evidenced.

## Evidence map

| Claim | Supporting artifact | Boundary |
|---|---|---|
| Host and service enumeration was recorded | [Nmap screenshot](../evidence/reconnaissance/01-nmap-service-enumeration-sanitized.png) | Direct screenshot; not a vulnerability by itself. |
| Struts RCE exposure was flagged | [Nessus screenshot](../evidence/reconnaissance/02-nessus-critical-vulnerability-sanitized.png) | Scanner finding; manual exploitation on this host is unshown. |
| A Tomcat exploit module opened a shell and an active session reported root | [Sanitized excerpt from report screenshots](evidence-notes.md#tomcat-shell-session) | Source captures are preserved outside this repository; raw screenshots contain lab identifiers and a course flag. The two screenshots show different session numbers. |
| LeVonta authored the original course report | [Source and attribution notes](evidence-notes.md#source-and-attribution) | Document history and contact fields name her; individual execution of every action is not independently established. |
