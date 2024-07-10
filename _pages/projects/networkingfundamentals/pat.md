---
title: Configuring PAT
permalink: /pat
parent: Networking Fundamentals
---
# Configuring Port Address Translation
{: .no_toc }

{: .note }
Networking Fundamentals, Router Configuration, Documentation and Planning, Troubleshooting, Cisco IOS
{: .fs-3 }

#### Contents
{: .no_toc }
- TOC
{:toc}

## Scenario
In this Packet Tracer Lab, I will configure port address translation (PAT) on a router. PAT is a type of Network Address Translation (NAT) that allows multiple devices on a local network to be mapped to a single public IP address (or a range of public IP addresses) using different ports. Router0 will be performing all of the address translations.

This is the network topology I will be using:

![](/assets/images/101netplus/25_pat/topology.png)

## Objectives

1. Set the IP configuration for the hosts
2. Configure IP addressing for the routers
3. Add a static route on Router1
4. Add PAT configuration to Router0
5. Test the PAT configuration by pinging Router1

## Results
### 📄 Task 1: Set the IP configuration for the hosts

The two PCs will belong to the 172.16.1.0/16 network. They will be assigned the IP addresses 172.16.1.2 and 172.16.1.3. Their default gateway on Router0 will be 172.16.1.1.

<br>

### 📄 Task 2: Configure IP addressing for the routers

First, I’ll assign IP addresses to Router0. Interface G0/0 is the default gateway for the 172.16.1.0/24 network and will be assigned 172.16.1.1. Interface G0/1 connects Router0 to Router1, so it will belong to the 192.168.1.0/24 network and will be assigned 192.168.1.1.

![](/assets/images/101netplus/25_pat/R0_configure.png)

Next, I’ll assign an IP address to Router1. Its G0/1 interface will be assigned 192.168.1.2.

![](/assets/images/101netplus/25_pat/R1_configure.png)

<br>

### 📄 Task 3: Add a static route on Router1

I use the following command to set a static route on Router1:

```ip route 0.0.0.0 0.0.0.0 192.168.1.1```

This tells Router1 to forward all incoming traffic to 192.168.1.1, which is the interface on Router0 where the port address translations will begin.

<br>

### 📄 Task 4: Add PAT configuration to Router0

I use the following Cisco IOS commands to configure PAT on Router0:

![](/assets/images/101netplus/25_pat/R0_PAT_configuration.png)

Addresses from the 172.16.0.0/16 network will be translated to an address pool (named “marcdlc”) consisting of a single address: 10.0.0.1.  The keyword “overload” enables PAT, allowing multiple addresses from 172.16.0.0/16 to share the single IP address 10.0.0.1 by tagging packets with unique port numbers.

I create an access list that tells Router0 to translate addresses from the 172.16.0.0/16 network. On Router0, I designate the G0/0 interface as the inside NAT interface and the G0/1 interface as the outside NAT interface. This allows the router to know in which direction to apply the correct address translations.

<br>

### 📄 Task 5: Test the PAT configuration by pinging Router1

To test the PAT configuration on Router0, I ping Router1 from a host in the 172.16.0.0/16 network. I then check the NAT table on Router0 using the command: ```show ip nat tran```

![](/assets/images/101netplus/25_pat/showipnattran.png)

The Inside Global column shows that each host is being translate to the IP addresses 10.0.0.1. Also note that each translation is being tagged with a unique port number. 

---

<a href="#top" id="back-to-top">Back to top</a>