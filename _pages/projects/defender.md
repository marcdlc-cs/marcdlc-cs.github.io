---
title: Configure Windows Defender Firewall
permalink: /defender
---
# Configure Windows Defender Firewall
{: .no_toc }

{: .note }
Firewall Configuration, Network Hardening, Security Configuration
{: .fs-3 }

#### Contents
{: .no_toc }
- TOC
{:toc}

## Scenario
This is a guided project provided by Coursera called <a href="https://www.coursera.org/projects/microsoft-windows-defender-and-firewall-for-beginners" target="_blank">Microsoft Windows Defender and Firewall for Beginners</a>. In one of the labs in this project, I am shown how to configure firewall rules for Windows Defender Firewall.

See my <a href="https://www.coursera.org/account/accomplishments/certificate/DV4HA9GNXVK9" target="_blank">Certificate of Completion</a>.

## Goals & Objectives
Configure firewall rules using Microsoft Windows Defender Firewall with Advanced Security:
- Allow the connection for Key Management Service on the Domain and Private network
- Deny the connection for Key Management Service on the Public network

## Results
### 📄 Task 1: Navigate to Advanced Firewall Settings

I go to Advanced Settings of the Firewall and Network Protection settings.

![](/assets/images/wf_coursera/wf_step1.png)  

![](/assets/images/wf_coursera/wf_step2.png)

Inbound rules determine what traffic is allowed to the computer. 
Outbound rules determine what traffic is allowed to leave the computer. 


### 📄 Task 2: Identify the Key Management Service rule
{: .mt-8 }

I select Inbound Rules and identify the Key Management Service rule.

![](/assets/images/wf_coursera/wf_step2a.png)

Currently, the rule is not enabled. If enabled, it would allow communication with the Domain, Private, and Public Networks. However, I only want this rule to allow communication with only the Domain and Private networks.

### 📄 Task 3: Change and enable and existing rule
{: .mt-8 }

In the properties window of the Key Management Service rule, under the Advanced tab,I uncheck Public and click Apply. Then, I right click and select Enable to enable the rule.

![](/assets/images/wf_coursera/wf_step3.png)  

![](/assets/images/wf_coursera/wf_step3a.png)


### 📄 Task 4: Create an additional inbound rule
{: .mt-8 }

Next, I will create an inbound rule that blocks communication with the public network. Since the new rule will be similar to the last, I will copy the existing rule by right-clicking on it to bring up the context menu, then copying and pasting it.

![](/assets/images/wf_coursera/wf_step4.png)

### 📄 Task 5: Complete the new inbound rule
{: .mt-8 }

In the properties menu of the new rule, I select Block the connection and check only the Public network under the Advanced tab.

![](/assets/images/wf_coursera/wf_step5.png)

![](/assets/images/wf_coursera/wf_step5a.png)

Finally, to enable the new rule, I right-click it and select Enable.

![](/assets/images/wf_coursera/wf_step5b.png)