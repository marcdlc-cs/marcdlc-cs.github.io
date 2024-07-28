---
title: Disable Unused Services/Ports
permalink: /disableserv
parent: 🔒 Network Security
---
# Disable Unused Services and Ports
{: .no_toc }

{: .note }
Network Security, Switch Configuration, Network Protocols and Services, Troubleshooting
{: .fs-3 }

#### Contents
{: .no_toc }
- TOC
{:toc}

## Scenario
In this Packet Tracer lab, I will be disabling unused services on a router and unused ports on a switch. Each running service on a network device represents a potential entry point for attackers. By disabling services that are not needed, you minimize the number of vulnerabilities that could be exploited, thus reducing the overall attack surface of the network. I will be focusing on disabling the CDP (Cisco Discovery Protocol) service. It is used by Cisco devices to share information about other directly connected Cisco equipment, helping to manage and troubleshoot networks. 

Lastly, it is a good idea to disable unused ports. Disabling unused switch ports is a common cybersecurity practice that enhances network security by reducing potential attack vectors. An attacker could connect a rogue device to an unused port to eavesdrop on network traffic, launch attacks, or gain unauthorized access to network resources. Disabling unused ports reduces the risk of such threats.

This is the network topology I will be using:

![](/assets/images/101netplus/7475_disable/topology.png)

## Objectives

1. Issue the ```show cdp neighbors``` command
2. Add an IP address to Router1
3. Disable CDP and Telnet/SSH on Router0
4. Shutdown unused switch port F0/3

## Results
### 📄 Task 1: Issue the ```show cdp neighbors``` command

Issuing the ```show cdp neighbors``` command along with the ```show cdp neighbors command``` reveals information about nearby network devices such as the type of device, which of its interfaces are active, and the version of Cisco IOS that it is running. This type of information can aid threat actors in gaining access to a network. 

![](/assets/images/101netplus/7475_disable/R0_showcdp.png)

<br>

### 📄 Task 2: Add an IP address to Router1

While CDP is running, network devices can learn the IP addresses of its neighbor devices. To demonstrate, Router1 is given an IP address.  

![](/assets/images/101netplus/7475_disable/R1_addip.png)

Then, Router0's CDP table is cleared to remove any information about Router1.

![](/assets/images/101netplus/7475_disable/R0_R1_cdpdisabled.png)

After some time, Router0 automatically learns the newly assigned IP address of Router1.

![](/assets/images/101netplus/7475_disable/R0_showR1ip.png)

While CDP is useful for network management and troubleshooting, it can also be exploited by threat actors to gather intelligence about the network, aiding in unauthorized access and other malicious activities.

<br>

### 📄 Task 3: Disable CDP and Telnet/SSH on Router0

In order to disable CDP, I issue the ```no cdp run``` command. And just in case, I also disable remote access to Router0 by removing Telnet and SSH using the ```transport input none``` command.

![](/assets/images/101netplus/7475_disable/R0_disable_cdptelnetssh.png)

<br>

### 📄 Task 4: Shutdown unused switch port F0/3

On the switch, port F0/3 is not being used and so I decide to disable it to enhance network security. Then I assign that port to an unused VLAN. By assigning disabled ports to an unused VLAN, I create an additional layer of isolation. If someone re-enables a port without authorization, the device connected to it will be placed in VLAN 888 with no access to the production network.


![](/assets/images/101netplus/7475_disable/switch_shutdownport.png)

---

<a href="#top" id="back-to-top">Back to top</a>