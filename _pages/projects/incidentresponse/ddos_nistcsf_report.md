---
title: DDoS Attack Incident Report
permalink: /ddosnist
parent: Incident Reponse
---
# DDoS Attack Incident Report
{: .no_toc }

{: .note }
Incident Response & Reporting, NIST CSF, Compliance, Vulnerability Assessment & Mitigation, Network Security
{: .fs-3 }

#### Contents
{: .no_toc }
- TOC
{:toc}

## Scenario
I'm a cybersecurity analyst at a multimedia company that provides web design, graphic design, and social media marketing services to small businesses. Recently, our organization faced a DDoS attack that disrupted our internal network for two hours.

During the attack, our network services suddenly became unresponsive due to a massive influx of ICMP packets. This essentially blocked normal internal network traffic from accessing any network resources. Our incident management team responded by blocking incoming ICMP packets, taking non-critical network services offline, and restoring critical network services.

Subsequently, our cybersecurity team conducted an investigation into the security incident. We discovered that a malicious actor had flooded our network with ICMP pings through an unconfigured firewall, exploiting this vulnerability to launch a distributed denial of service (DDoS) attack that disrupted our operations.

## Goals & Objectives
Analyze the situation using the NIST CSF and create an incident report, building trust and improving security practices within the company. 

## Results
### NIST CSF Incident Report

<table>
    <tr>
        <td>Identify</td>
        <td>An ICMP flood attack was used by the threat actor. The systems affect were the network server,  network router, and firewall.</td>
    </tr>
    <tr>
        <td>Protect</td>
        <td>The following protective measures must be put in place to prevent further occurrences of this type of attack:
            <ul>
                <li>A new firewall rule to limit the rate of incoming ICMP packets</li>
                <li>Check for spoofed IP addresses. If spoofed IP addresses are found, then a new firewall rule must be put in place to block incoming traffic from that specific IP address or addresses</li>
                <li>Network monitoring software to detect abnormal traffic patterns such as an IDS or IPS</li>
                <li>Network segmentation so that incidents can be isolated to prevent the threat from spreading to other critical networks</li>
            </ul></td>
    </tr>
    <tr>
        <td>Detect</td>
        <td>Implementing both an IDS and IPS system will help monitor and stop any malicious network activity such as an ICMP flood attack. Employing the use of SIEM tools will help cybersecurity personnel monitor and analyze both normal and malicious network traffic.</td>
    </tr>
    <tr>
        <td>Respond</td>
        <td>In response to this type of attack, the Cybersecurity team can perform the following:
            <ul>
                <li>Configure the affected firewall to temporarily block all incoming traffic to the company network</li>
                <li>Shutdown any devices and networks that were compromised during the attack to contain the attack and regain control</li>
                <li>Use a combination of SIEM tools, incident playbooks, and tcpdump logs to analyze the incident on a more granular level</li>
                <li>Document this incident in order to better prepare the organization for a similar attack. All playbooks must be updated accordingly for quicker response times</li>
                <li>A firewall rule to blacklist spoofed IP addresses, preferably through a NGFW</li>
                <li>Create updated backups of all critical systems and data</li>
            </ul></td>
    </tr>
    <tr>
        <td>Recover</td>
        <td>To recover:
            <ul>
                <li>Analyze the initial security audit to determine which systems and devices were affected</li>
                <li>Restore all affected systems, devices, and networks to their last known good configuration using backups</li>
            </ul></td>
    </tr>
</table>

