---
title: Analyzing WannaCry with MITRE ATT&CK
permalink: /wannacry
parent: 💥 Threat Analysis
---
# Analyzing WannaCry with MITRE ATT&CK
{: .no_toc }

{: .note }
MITRE ATT&CK, Threat Analysis, Malware Analysis, OSINT, Documentation
{: .fs-3 }

#### Contents
{: .no_toc }
- TOC
{:toc}

## Scenario
I will conduct an in-depth analysis of the 2017 WannaCry ransomware attack by discovering the attacker's tactics, techniques, and procedures using the MITRE ATT&CK framework.

## Objectives
Gain a comprehensive understanding of how the attackers behind WannaCry utilized various techniques and tactics, mapping them to the relevant ATT&CK framework components.

## Results

### Attack profile

The WannaCry ransomware attack, also known as WannaCrypt, was a global cyberattack that occurred in May 2017. It was one of the most significant and widespread ransomware attacks in history. The attack exploited vulnerabilities in Microsoft Windows operating systems, infecting hundreds of thousands of computers across the world.

The attackers behind WannaCry were financially motivated. Once the malware had spread to a system, it encrypted the user’s files and demanded a ransom payment in Bitcoin for decryption. They weren't interested in collecting data, they only wanted payment for access to it. 

### Method to gain initial access to systems

[WannaCry](https://attack.mitre.org/software/S0366/) used the EternalBlue exploit, which targeted a vulnerability in Microsoft’s Server Message Block (SMB). Adversaries may use this technique in conjunction with administrator-level Valid Accounts to remotely access a networked system over SMB.

### Methods of persistence after initial infection

The malware creates the following two registry run keys to ensure persistence:

```
Key: HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Run\<Random>
Value: <Full_path>\tasksche.exe

Key: HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run\<Random>
Value: <Full_path>\tasksche.exe
```
Source: [https://www.mandiant.com/resources/blog/wannacry-malware-profile](https://www.mandiant.com/resources/blog/wannacry-malware-profile)

| Technique | Description |
| --- | --- |
| [Registry Run Keys / Startup Folder](https://attack.mitre.org/techniques/T1547/001) | Adversaries may achieve persistence by adding a program to a startup folder or referencing it with a Registry run key. Adding an entry to the "run keys" in the Registry or startup folder will cause the program referenced (WannaCry ransomware) to be executed when a user logs in. The ransomware will be executed upon system startup. |

### Methods to avoid detection

| Technique | Description |
| --- | --- |
| [Asymmetric Cryptography](https://attack.mitre.org/techniques/T1573/002) | WannaCry uses Tor for command and control traffic and routes a custom cryptographic protocol over the Tor circuit. |
| [Windows File and Directory Permissions Modification](https://attack.mitre.org/techniques/T1222/001) | WannaCry uses attrib +h and icacls . /grant Everyone:F /T /C /Q to make some of its files hidden and grant all users full access controls. |
| [Hidden Files and Directories](https://attack.mitre.org/techniques/T1564/001) | WannaCry uses attrib +h to make some of its files hidden and obscure any indicators of compromise. |

### Methods for device detection and lateral movement

| Technique | Description |
| --- | --- |
| [Remote System Discovery](https://attack.mitre.org/techniques/T1018) | WannaCry scans its local network segment for remote systems to try to exploit and copy itself to. |
| [Lateral Tool Transfer](https://attack.mitre.org/techniques/T0867) | WannaCry can move laterally through industrial networks by means of the SMB service. |

**Additional notes**: WannaCry contains worm-like features to spread itself across a computer network. It can move laterally through industrial networks by means of the SMB service. It attempts to copy itself to remote computers after gaining access via an SMB exploit.

### Attack Impact

The attack had a massive impact on critical services, particularly healthcare systems, leading to postponed surgeries and patient care disruptions. Major corporations and government institutions were also hit, causing financial losses and operational disruptions.

The attack prompted discussions about the need for improved cybersecurity practices, timely patching, and international cooperation to counter cyber threats.

It highlighted the importance of regularly updating and patching software, particularly for critical security vulnerabilities and raised awareness about the potential impact of ransomware attacks on critical infrastructure and underscored the need for robust cybersecurity defenses.

### Reflections

The WannaCry ransomware attack was significant in emphasizing the critical importance of cybersecurity measures, particularly patch management and network segmentation. It exploited vulnerabilities in outdated systems, underlining the need for timely software updates and patching to prevent such attacks. Additionally, the rapid spread of WannaCry across networks underscored the necessity of network segmentation to contain and mitigate the impact of future cyber threats.

---

<a href="#top" id="back-to-top">Back to top</a>