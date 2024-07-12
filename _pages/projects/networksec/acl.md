---
title: Configure Access Control Lists
permalink: /disableserv
parent: 🔒 Network Security
---
# Configure Access Control Lists
{: .no_toc }

{: .note }
Network Security, Router Configuration, Access Management, Troubleshooting
{: .fs-3 }

#### Contents
{: .no_toc }
- TOC
{:toc}

## Scenario
In this Packet Tracer lab, I will configure an extended access control list (ACL) on a router. ACLs are a series of rules applied to a router’s interface which determine if traffic is allowed into or blocked from your network. These rules are used to permit or deny traffic based on various criteria such as IP addresses, protocol types, and port numbers.

ACLs help filter harmful traffic from entering or leaving a network, enforces access control policies, and creates network segments that can isolate and contain network breaches.

This is the network topology I will be using:

![](/assets/images/101netplus/28_eacl/topology.png)

## Objectives

1. Set the IP configuration for the hosts
2. Set the IP configuration for the routers
3. Add static routes to both routers
4. Configure an ACL on Router0
5. Test the ACL

## Results
### 📄 Task 1: Set the IP configuration for the hosts

The 172.16.1.0/16 network will have two PCs and will be configured in this manner:

- IP Addresses: 172.16.1.2, 172.16.1.3
- Subnet Mask: 255.255.0.0
- Default Gateway: 172.16.1.1

The 10.0.0.0/8 network will have a single PC and will be configured in this manner:

- IP Address: 10.0.0.2
- Subnet Mask: 255.0.0.0
- Default Gateway: 10.0.0.1 

<br>

### 📄 Task 2: Set the IP configuration for the routers

The 192.168.1.0/30 network will consist of two routers, and will be configured in this manner:

Router (R0):
- Interface G0/1, 172.16.1.1, 255.255.0.0
- Interface G0/0, 192.168.1.1, 255.255.255.252

Router (R1)
- Interface G0/1, 10.0.0.1, 255.0.0.0
- Interface G0/0, 192.168.1.2, 255.255.255.252

<br>

### 📄 Task 3: Add static routes to both routers

I will configure static routes on both routers so that each router can reach the network on the other side. Then I will test connectivity with the ping command. 

On Router0, I use the following command to configure a static route so that all incoming traffic goes to 192.168.1.2:

```R0(config)#ip route 0.0.0.0 0.0.0.0 192.168.1.2```

Next, I configure a static route on Router1 so that all incoming traffic goes to 192.168.1.1:

```R1(config)#ip route 0.0.0.0 0.0.0.0 192.168.1.1```

Here are the results after using the ping command to test the static routes:

![](/assets/images/101netplus/28_eacl/R0_pingtest.png)
![](/assets/images/101netplus/28_eacl/R1_pingtest.png)

Both routers can reach the networks at the end of their static routes.

<br>

### 📄 Task 4: Configure an ACL on Router0

I will configure an ACL on Router0 that blocks traffic from 10.0.0.2 if it tries to access the 172.16.0.0/16 network. Any other traffic from this or another host will be permitted.

![](/assets/images/101netplus/28_eacl/eACL.png)

These rules are applied to inbound traffic coming to the interface G0/0 on Router0.

<br>

### 📄 Task 5: Test the ACL

I ping 172.16.1.2 from 10.0.0.2. The ping fails.

![](/assets/images/101netplus/28_eacl/PC2_pingtest_acltest.png)

I check to see if the ACL was triggered on Router0.

![](/assets/images/101netplus/28_eacl/R0_accesslisthits.png)

The command ```show ip access-list``` shows that the rules of the ACL were activated and that 10.0.0.2 was denied connectivity to 172.16.1.2.

---

<a href="#top" id="back-to-top">Back to top</a>