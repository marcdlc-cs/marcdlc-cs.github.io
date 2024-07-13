---
title: Unresponsive DHCP Server
permalink: /unresponsedhcp
parent: 🔧 Network Troubleshooting
---
# Troubleshooting an Unresponsive DHCP Server
{: .no_toc }

{: .note }
Network Diagnostics, Server Management, Router Configuration, Troubleshooting
{: .fs-3 }

#### Contents
{: .no_toc }
- TOC
{:toc}

## Scenario
In this Packet Tracer lab, I will be troubleshooting an unresponsive DHCP server. 

This is the network topology I will be using:

![](/assets/images/101netplus/101_unresponsedhcp/topology.png)

## Objectives

1. Confirm connectivity between the router and server
2. Create a DHCP address pool
3. Attempt DHCP discovery on PC0
4. Configure the router as DHCP relay agent
5. Configure PC0 to receive IP addressing from the DHCP server

## Results
### 📄 Task 1: Confirm connectivity between the router and server

To check for connectivity between the router and the server, I ping the router from the server. I also ping the server from the router.

![](/assets/images/101netplus/101_unresponsedhcp/server_pingrouter.png)

![](/assets/images/101netplus/101_unresponsedhcp/router_pingserver.png)

Connectivity between the server and router is confirmed.

<br>

### 📄 Task 2: Create a DHCP address pool

In the DHCP server, I will configure an address pool for the 192.168.1.0/16 network. The starting address will be 192.168.1.2 and the default gateway will be 192.168.1.1.

![](/assets/images/101netplus/101_unresponsedhcp/dhcp_pool.png)

### 📄 Task 3: Attempt DHCP discover on PC0

When requesting an IP address from the DHCP server, PC0 broadcasts a DHCP Discover packet to the network. This packet is sent to the broadcast address (255.255.255.255). However, the router drops this packet because routers do not forward broadcast packets. This is an issue because the DHCP server is located in another LAN, and so PC0's request for an IP address fails.

![](/assets/images/101netplus/101_unresponsedhcp/PC0_dhcpfail.png)

Below is a graphical depiction of the DHCP discover packet (the yellow envelope) being dropped at the 172.16.1.1 interface of the router.

![](/assets/images/101netplus/101_unresponsedhcp/router_blockDHCPdiscover.png)

When DHCP discovery fails, PC0 assigns itself with an APIPA address starting with 169.254.x.x. Automatic Private IP Addressing (APIPA) allows devices on a local network to automatically assign themselves an IP address when a DHCP server is unavailable, ensuring basic network communication within the local subnet.

However, there are limitations to APIPA which include:

- APIPA addresses are not routable on the internet. Access to the internet is impossible without a valid IP address from a DHCP server
- Devices using APIPA can only communicate with devices within the same local network that also have APIPA addresses assigned.

<br>

### 📄 Task 4: Configure the router as DHCP relay agent

To resolve the issue, I will configure the router to forward DHCP requests to the DHCP server (172.16.1.2) as unicast packets. This turns the router into a DHCP relay agent. A DHCP relay agent is a network device configured to forward DHCP packets between clients and servers when they are not on the same LAN. 

![](/assets/images/101netplus/101_unresponsedhcp/router_helper.png)

With this configuration, the router will forward DHCP Discover packets to the DHCP server (172.16.1.2).

<br>

### 📄 Task 5: Configure PC0 to receive IP addressing from the DHCP server

![](/assets/images/101netplus/101_unresponsedhcp/PC0_dhcpsuccess.png)

PC0 successfully receives an IP address from the DHCP server.

---

<a href="#top" id="back-to-top">Back to top</a>