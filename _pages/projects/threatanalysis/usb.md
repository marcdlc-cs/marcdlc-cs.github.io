---
title: USB Baiting Attack Vectors
permalink: /usbbait
parent: 💥 Threat Analysis
has_toc: false
---
# USB Baiting Attack Vectors
{: .no_toc }

{: .note }
Digital Forensics, Risk Assessment & Mitigation, Threat Analysis
{: .fs-3 }

#### Contents
{: .no_toc }
- TOC
{:toc}

## Scenario
I am part of the security team at Rhetorical Hospital and arrive to work one morning. On the ground of the parking lot, I find a USB stick with the hospital's logo printed on it. There’s no one else around who might have dropped it, so I decide to pick it up out of curiosity.

I bring the USB drive back to my office where the team has virtualization software installed on a workstation, allowing me to safely examine its contents:

![](/assets/images/usbcontents_crop.png)

## Objectives
Assess the attack vectors of a USB drive by describing its contents, the attacker's mindset (if this is a USB baiting attack), and analyzing the risks involved.

## Results

### Contents

There are files that contain PII as well as sensitive work files. It is not safe to store personal files with work files.

### Attacker Mindset

The information could be used against employees. For example, the information in the shift schedule could make it easier for the attacker to monitor and track top-level employees/executives.

The information can be used against relatives. The wedding list can be used to retrieve physical addresses or emails of the guests on that list. The attacker can launch a massive phishing attack on the friends and family of the employee.

There is enough information for an attacker to attempt to steal login credentials of any company employee.

### Risk Analysis

Malicious software contained on the drive could be worms, ransomware, and malware. An employee could take the infected device and access through a computer within the company network. This could provide a backdoor for the attacker to gain access into the network.

The types of sensitive information that an attacker can find on this device are: physical addresses, email addresses, employee names, phone numbers, and sensitive financial information pertaining to the company.

That information can enable an attacker to launch a phishing attack on the organization, or friends and family of the employee. Knowing specific employee names and their shift schedules can help the attacker find targets for whaling or spear phishing. Smishing is also a possibility with employee phone numbers.

Security controls to mitigate USB baiting:

*Technical* - using a VM to investigate unknown USB devices, disable Autorun on all endpoints within a network, install and update all security software on all devices within the hospital's network

*Operational* - USB baiting awareness training, general cybersecurity awareness training

*Managerial* - enforce a USB data handling policy that discourages employees from mixing personal and  professional data/files on the same device. Unknown portable file storage devices should be turned in to the cybersecurity team for analysis.

---

<a href="#top" id="back-to-top">Back to top</a>

