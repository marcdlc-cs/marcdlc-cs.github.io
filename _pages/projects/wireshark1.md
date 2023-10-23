---
title: Capturing Credentials With Wireshark
permalink: /wireshark1
---
# Capturing Credentials With Wireshark
{: .no_toc }

{: .note }
Wireshark, Network Analysis, Network Protocols, Packet Filtering & Analysis, Kali Linux
{: .fs-3 }

#### Contents
{: .no_toc }
- TOC
{:toc}

## Scenario
In this lab, I will be capturing requests sent and received from my Kali machine. I will then analyze these requests for captured information. I will also capture usernames and passwords submitted through http websites with Wireshark.

## Goals & Objectives

1. Examine the contents of packets to find important pieces of information.
2. Use Wireshark to capture packets in order to find user credentional transmitted in cleartext through this website: http://testphp.vulnweb.com/login.php. This website is a *deliberately* vulnerable web application that is **used for educational and testing purposes**.
3. Filter packets to only show http POST requests and DNS traffic pertaining to the website http://testphp.vulnweb.com.

## Results
### 📄 Task 1: Capture login credentials

**Step 1:**  In Kali Linux, I open Wireshark by typing ```sudo wireshark``` in the terminal.

**Step 2:** In Wireshark, I select the eth0 interface.

![](/assets/images/101_wireshark1/step2.png)

**Step 3:** I open Firefox and go to: http://testphp.vulnweb.com/login.php. Wireshark begins to capture packets.

![](/assets/images/101_wireshark1/step3.png)

**Step 4:** Back in Firefox, I enter username1 in the Username field and password1234 in the Password field and click login.

![](/assets/images/101_wireshark1/step4.png)

**Step 5:** I stop Wireshark from capturing packets by clicking on the red square in the top left corner.

![](/assets/images/101_wireshark1/step5.png)

**Step 6:** I save the captured packets in a pcap file for later analysis by going to File > Save As and naming the file.

**Step 7:** To make it easier to find the login credentials, I type ```http.request.method == "POST"``` into the filter box to filter packets by http POST requests. The resulting packets are highlighted in green, indicating that they are either HTTP or TCP packets. 

![](/assets/images/101_wireshark1/step7.png)

I select the packet that shows POST in the Info column. The second window shows important information about the source and destination of this packet: MAC addresses, IP addresses, and ports.

![](/assets/images/101_wireshark1/step8.png)

**Step 8:** In the second window, I select the HTML Form URL Encoded section to expand it which reveals the login credentials transmitted in cleartext: username1 and password1234.

![](/assets/images/101_wireshark1/step9.png)

<br>
<br>
### 📄 Task 2: Filter packets for DNS traffic

In Wireshark, I use the filter command ```dns.qry.name == "testphp.vulnweb.com"``` so that I’m only shown packets pertaining to testphp.vulnweb.com. These packets are highlighted in blue, indicating that they are DNS packets.

![](/assets/images/101_wireshark1/step10.png)

Packet 1527 shows me the client request to the DNS server with the human-readable address  testphp.vulnweb.com

![](/assets/images/101_wireshark1/step11a.png)

Packet 1529 shows me the DNS server response with the IP address for testphp.vulnweb.com: 44.228.249.3

![](/assets/images/101_wireshark1/step11b.png)