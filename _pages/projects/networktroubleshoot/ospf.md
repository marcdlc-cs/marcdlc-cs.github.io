---
title: Troubleshooting OSPF
permalink: /ospf
parent: 🔧 Network Troubleshooting
---
# Troubleshooting OSPF Network Configuration
{: .no_toc }

{: .note }
Router Configuration, Network Diagnositcs, Troubleshooting
{: .fs-3 }

#### Contents
{: .no_toc }
- TOC
{:toc}

## Scenario
In this Packet Tracer lab, I will be configuring OSPF on two routers and troubleshooting an incorrect network configuration.

OSPF (Open Shortest Path First) is a link-state routing protocol used in IP networks to determine the best path for packets by dynamically updating routes, prioritizing the shortest path to the destination. 

A wildcard mask specifies which IP addresses or networks should participate in OSPF. An incorrect wildcard mask or network configuration can affect OSPF advertisements, causing routers to have incorrect routing information.

This is the network topology I will be using:

![](/assets/images/101netplus/97_ospf/topology.png)

## Objectives

1. Configure OSPF on both routers
2. Verify incorrect network configuration
3. Fix the OSPF configuration
4. Verify the OSPF configuration is correct

## Results
### 📄 Task 1: Configure OSPF on both routers

The routers will be assigned the IP addresses 192.168.1.5 and 192.168.1.6.

![](/assets/images/101netplus/97_ospf/R2_ospfconfig_wrong.png)

![](/assets/images/101netplus/97_ospf/R1_ospfconfig_wrong.png)

Notice that the incorrect network is configured. With a network of 192.168.1.0 and a wildcard mask 0.0.0.3, only the range of IP addresses 192.168.1.0 through 192.168.1.3 will be included. What is needed is a network that includes IP addresses 192.168.1.5 and 192.168.1.6.

<br>

### 📄 Task 2: Verify incorrect network configuration

To check OSPF functionality, I will be issuing the ```show ip ospf neighbor``` command. It is used to display information about OSPF neighbors or adjacent routers that have formed neighbor relationships.

![](/assets/images/101netplus/97_ospf/R0_show_noneighbor.png)   
![](/assets/images/101netplus/97_ospf/R1_show_noneighbor.png)


As expected, the command returns no output, which means no neighbors have been identified (due to the incorrect network configuration).

<br>

### 📄 Task 3: Fix the OSPF configuration

To resolve the issue, I will remove the incorrect network (192.168.1.0) and configure the correct network (192.168.1.4) on both routers.

![](/assets/images/101netplus/97_ospf/router_correctnetwork.png)

By inputting the 192.168.1.4 network with a wildcard mask of 0.0.0.3, both routers know that 192.168.1.5 and 192.168.1.6 are configured for OSPF.

<br>

### 📄 Task 4: Verify the OSPF configuration is correct

Issuing the ```show ip ospf neighbor``` once more on each router shows that each router has successfully discovered their neighbor.

![](/assets/images/101netplus/97_ospf/R0_showneighbor.png)
![](/assets/images/101netplus/97_ospf/R1_showneighbor.png)

---

<a href="#top" id="back-to-top">Back to top</a>