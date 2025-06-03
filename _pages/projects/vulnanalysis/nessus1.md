---
title: Nessus Scanning Exercise
permalink: /nessus1
parent: 👁️ Vulnerability Analysis
has_toc: false
---
# Nessus Scan: Analyzing ProFTPD 
{: .no_toc }

{: .note }
Vulnerability Assessment, Risk Mitigation, Nessus
{: .fs-3 }

#### Contents
{: .no_toc }
- TOC
{:toc}

## Scenario
The project allows me to familiarize myself with Nessus, a widely-used vulnerability scanner. I am scanning an intentionally vulnerable virtual machine.

Initiating new scan:
![](/assets/images/nessus1/scansetup.png)

## Objectives
1. Identify the most critical vulnerability in this machine.
2. Research this vulnerability using reliable sources such as security advisories or vulnerability databases.

## Results

### Vulnerability Assessment

#### Scan Results
After scanning the vulnerable machine, Nessus identifies 39 vulnerabilites.

![](/assets/images/nessus1/scanresults.png)
<br>
<br>
#### Most Critical Vulnerability
The most critical vulnerability is the ProFTPD mod_copy Information Disclosure.

![](/assets/images/nessus1/vuln_proftpd.png)

ProFTPd, a widely used open-source FTP server, is compatible with UNIX-like and Windows systems, particularly popular on UNIX-based platforms. However, a vulnerability affects all ProFTPd versions up to 1.3.6 (if installed before 7/17/19) in the mod_copy module. This flaw enables authenticated users, including anonymous users if enabled, to copy files to new names, even without the necessary write permissions. The issue arises from a bug in the SITE CPFR and SITE CPTO commands, which bypass "Limit WRITE" deny all directives and allows users to copy files to the current directory without proper permissions.
<br>
<br>
#### Risks & Consequences
Due to the SITE CPFR and SITE CPTO commands, the attacker has the ability to read, write, and copy files/directories from one place to another even though they don't have permissions to do that. The following risks and consequences present themselves:

1. **Access to sensitive data** - that attacker can expose PII, SPII, PHI
2. **Data exfiltration** - the attacker can copy files to another location using any web accessible path on the host
3. **Data manipulation** - write permissions allow for data manipulation
4. **Malware injection** - the attacker can copy malicious code into the server
5. **Compliance consequences** - the org can be held responsible for violating data handling laws and regulations
6. **Reputational damage** if SPII about individuals is exposed
7. **Financial loss** due to heavy fines, legal fees

<br>
#### Mitigation strategy
Nessus recommends upgrading to ProFTPD 1.3.5a / 1.3.6rc1 or later. In general, implementing strong access controls, updating and patching software, monitoring network traffic for suspicious activity, and staying updated on the latest vulnerabilities are possible ways to address this vulnerability.

---

<a href="#top" id="back-to-top">Back to top</a>