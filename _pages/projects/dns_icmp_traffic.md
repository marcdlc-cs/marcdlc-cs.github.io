---
title: DNS and ICMP Traffic Analysis
permalink: /dnsicmp/
---
# DNS, ICMP Network Traffic Analysis
{: .no_toc }

{: .note }
Network Analysis, Incident Response, Protocol Analysis, Documentation
{: .fs-3 }

#### Contents
{: .no_toc }
- TOC
{:toc}

## Scenario
I'm a cybersecurity analyst working for an IT consultancy firm. Multiple customers reported being unable to access our website, www.yummyrecipesforme.com, and received a "destination port unreachable" error. I'm tasked with identifying the affected network protocol. I encountered the same error when visiting the site. I then used the tcpdump network analyzer tool and observed numerous packets. The analyzer revealed that sending UDP packets triggered an ICMP response with an error message: "udp port 53 unreachable." Now, I must determine the impacted network protocol and service and prepare a follow-up report. I can inspect network data to pinpoint the issue's cause, while security engineers are handling the incident after we've reported it to our supervisor.

**Tcpdump Output**
```
13:24:32.192571 IP 192.51.100.15.52444 > 203.0.113.2.domain: 35084+ A? yummyrecipesforme.com. (24)
13:24:36.098564 IP 203.0.113.2 > 192.51.100.15: ICMP 203.0.113.2 
udp port 53 unreachable length 254

13:26:32.192571 IP 192.51.100.15.52444 > 203.0.113.2.domain: 35084+ A? yummyrecipesforme.com. (24)
13:27:15.934126 IP 203.0.113.2 > 192.51.100.15: ICMP 203.0.113.2 
udp port 53 unreachable length 320

13:28:32.192571 IP 192.51.100.15.52444 > 203.0.113.2.domain: 35084+ A? yummyrecipesforme.com. (24)
13:28:50.022967 IP 203.0.113.2 > 192.51.100.15: ICMP 203.0.113.2 
udp port 53 unreachable length 150
```

## Goals & Objectives
Analyze the situation by:
<ol>
    <li>Identifying which network protocol and service were impacted by this incident</li>
    <li>Writing a follow-up report.</li>
</ol>

## Results
### Summary of Problem

Customers have reported that they are unable to access the company website at “www.yummyrecipesforme.com.” The UDP protocol reveals that port 53 of the DNS server is unreachable. After scanning the network with tcpdump, the ICMP reply is “udp port 53 unreachable.” Port 53 must be available for the DNS server to retrieve the IP address of the company website, otherwise the website cannot be accessed by customers.

### Report and Remediation Step

The incident occurred today at 1:23 p.m. Customers called the organization to notify the IT team they received the message “destination port unreachable” when they attempted to visit the website. The network security professionals within the organization are currently investigating the issue so customers can access the website again. 

In our investigation into the issue, we conducted packet sniffing tests using tcpdump. In the resulting log file, we found that DNS port 53 was unreachable. The DNS server is unable to return the IP address of the company website due to port 53 being unreachable. Because the IP address cannot be obtained, any request sent by customers’ computers to the company website server will not be fulfilled. This error may be due to a firewall configuration  which is blocking port 53. System administrators for the DNS server will be contacted to check for firewall misconfigurations and signs of a possible DoS attack.
