---
title: Switch Port Security
permalink: /portsec
parent: 🔒 Network Security
has_toc: false
---
# Configuring Switch Port Security
{: .no_toc }

{: .note }
Network Security, Switch Configuration and Management, MAC Address Management, Troubleshooting
{: .fs-3 }

#### Contents
{: .no_toc }
- TOC
{:toc}

## Scenario
In this Packet Tracer lab, I will be configuring port security on a switch. In particular, I will prevent a threat actor from plugging in a rogue hub to a network by permitting only one host to use it at a time.

This is the starting network topology I will be using:

![](/assets/images/101netplus/70_portsec/topology_1.png)

I will eventually add two more hosts to demonstrate the port security functionality of the switch.

## Objectives

1. Configure port security on the switch
2. Add two hosts to the network
3. Check port security status for interface F0/1

## Results
### 📄 Task 1: Configure port security on the switch

I am going to configure port security on the switch by permitting only one host to use switch interface F0/1. By default, the port will shut down if it detects another host trying to access the same port.

![](/assets/images/101netplus/70_portsec/switch_securityenabled.png)

The command ```switchport port-security maximum 1``` sets the maximum number of MAC addresses that can be dynamically learned or statically configured on that particular port to only one.

<br>

### 📄 Task 2: Add two hosts to the network

![](/assets/images/101netplus/70_portsec/topology_2.png)

Adding one host (00:06:2A:39:A3:B9) to the network does not cause the switch port to shutdown. However, adding the second host (00:0D:BD:15:D4:38) does trigger the port security functionality of the switch, causing the port to shut down. This happens because the switch detects two MAC addresses using the same port. 

<br>

### 📄 Task 3: Check port security status for interface F0/1

Bringing up the port security status of the switch, I can see the port status is in "secure-shutdown". In secure-shutdown mode, the interface F0/1 is inoperable. I can also see the last source MAC address of the offending host: 00:0D:BD:15:D4:38.

![](/assets/images/101netplus/70_portsec/switch_portshutdown.png)
![](/assets/images/101netplus/70_portsec/pc2_macaddress.png)

---

<a href="#top" id="back-to-top">Back to top</a>