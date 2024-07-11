---
title: Vulnerability Assessment for a Small Business
permalink: /vulnassess1
parent: 👁️ Vulnerability Analysis
---
# Vulnerability Assessment for a Small Business
{: .no_toc }

{: .note }
Vulnerability Assessment, Risk Assessment, Threat Analysis, Report Writing, Risk Mitigation, Network Security, Access Control
{: .fs-3 }

#### Contents
{: .no_toc }
- TOC
{:toc}

## Scenario
I've recently joined an e-commerce company as a cybersecurity analyst. The company relies on a remote database server to store information, as many of our employees work from various locations worldwide. This server is accessible to the public and has been open since the company's inception three years ago. As a cybersecurity expert, I understand the criticality of this situation, as it poses a significant security risk.

## Goals & Objectives
Conduct a vulnerability assessment for a small business, evaluating the risks of a vulnerable information system and outline a remediation plan

## Results

### Vulnerability Assessment
#### System Description
{: .no_toc }
The server hardware consists of a powerful CPU processor and 128GB of memory. It runs on the latest version of Linux operating system and hosts a MySQL database management system. It is configured with a stable network connection using IPv4 addresses and interacts with other servers on the network. Security measures include SSL/TLS encrypted connections.

#### Scope
{: .no_toc }
The scope of this vulnerability assessment relates to the current access controls of the system. The assessment will cover a period of three months, from June 2023 to August 2023. NIST SP 800-30 Rev. 1 is used to guide the risk analysis of the information system.

#### Purpose
{: .no_toc }
The purpose of this vulnerability assessment is to evaluate the risk of having our database server open to the public. Having the server open to the public presents a risk because the data contained on that server assists our employees in finding potential customers. Data on the server can be easily compromised, impacting the business financially as well as damaging the company’s reputation with its employees. Customer data is contained on those servers as well and if stolen or misused, the company could be faced with heavy fines and other legal liabilities. 

#### Risk Assessment
{: .no_toc }

| Threat Source | Threat Event | Likelihood | Severity | Risk |  
|---|---|:---:|:---:|:---:|
 Competitor | Obtain sensitive information via exfiltration | 3 | 3 | 9 |
 Hacker | Disrupt mission-critical operations | 3 | 3 | 9 |
 Storage | Physical hardware can breakdown over time | 3 | 2 | 6 |

{: .note3 }
>*Risk* = Likelihood * Severity
>
>*Likelihood* is the probability or chance that a specific event or threat will occur. Scale 1-3. A score of 3 indicates highly probable. 
>
>*Severity* represents the extent of harm or damage that could be caused if the risk event were to occur. Scale 1-3. A score of 3 indicates high impact/damage.
{: .fs-3 }

#### Approach
{: .no_toc }
The main vulnerability that must be addressed in this assessment is the public nature of the data servers. Data that is open to the public is at risk for misuse and exploitation by competitors and hackers. Competing businesses can extract sensitive information to gain insight on our business strategies and hackers can partially or completely destroy all the data on that server, disrupting mission-critical operations. Another minor vulnerability to consider is the physical server hardware. Hardware can breakdown and become obsolete over time which also puts the integrity and availability of the data at risk.

#### Remediation Strategy
{: .no_toc }
To address the public nature of the data server and the risk it poses, implementing authentication servers and digital certificates allows for strong authentication and authorization processes, limiting server access to only company employees. Since this server is being accessed remotely, the use of VPN technology can further enhance the confidentiality of data in transit. Multi-factor authentication can also be used to strengthen access controls for the server. As for the physical hardware, transitioning to a cloud based server can reduce the risk of hardware breakdown, it can optimize the patch management process, and the company will be relieved of having to maintain or dispose of legacy hardware.

---

<a href="#top" id="back-to-top">Back to top</a>