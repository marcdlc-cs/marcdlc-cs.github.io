---
title: Switch MAC Filtering
permalink: /macfilter
parent: 🔒 Network Security
has_toc: false
---
# Configuring MAC Filtering on a Switch
{: .no_toc }

{: .note }
Network Security, Wireless Networking, Router Configuration, Encryption, Authentication, Troubleshooting
{: .fs-3 }

#### Contents
{: .no_toc }
- TOC
{:toc}

## Scenario
In this Packet Tracer lab, I will be configuring MAC filtering on a switch. In this case, MAC filtering will be used to limit the amount of MAC addresses that can be learned on a single port. I will be configuring the switch port to only learn a single specific MAC address. If this rule is violated, the switch will shut down the port. 

MAC filtering prevents unauthorized devices from connecting to the network. This ensures that only trusted devices can access network resources. MAC filtering can also help mitigate on-path attacks by ensuring that only devices with known MAC addresses can connect to the network. This reduces the risk of attackers inserting themselves between legitimate devices and the network.

This is the network topology I will be using:

![](/assets/images/101netplus/72_macfilter/topology.png)

## Objectives

1. Configure IP addresses on the hosts
2. Configure MAC address filtering on the switch
3. Perform a ping test to trigger MAC filtering
4. Check that the switch port has shut down

## Results
### 📄 Task 1: Configure IP address on the hosts

The hosts PC0 and PC1 will be given the IP addresses 192.168.1.1 and 192.168.1.2. Note the MAC address of PC1, as it will be used in the MAC filtering for the switch. The MAC address for PC1 is 000C.85D9.8EC3.

![](/assets/images/101netplus/72_macfilter/PC0_ipconfig.png)
![](/assets/images/101netplus/72_macfilter/PC1_ipconfig.png)

<br>

### 📄 Task 2: Configure MAC address filtering on the switch

I configure MAC address 000C.85D9.8EC3 as the only MAC address that the port can learn.

![](/assets/images/101netplus/72_macfilter/switch_confmacaddress_pc1.png)

Issuing the ```show port-security``` command on the switch confirms that port security and MAC filtering is enabled:

![](/assets/images/101netplus/72_macfilter/switch_showportsec.png)

<br>

### 📄 Task 3: Perform a ping test to trigger MAC filtering

PC0 will ping PC1. This will trigger the switch port to shut down as it violates the MAC filtering rule. The switch sees that traffic is coming from PC0 which does not match the MAC address of PC1, forcing it to shut down the its port.

![](/assets/images/101netplus/72_macfilter/PC0_pingPC1.png)

<br>

### 📄 Task 4: Check that the switch port has shut down

![](/assets/images/101netplus/72_macfilter/switch_portsec_shutdown.png)

Observe that the Port Status has been changed to "Secure-shutdown", rendering the port inoperable. 

---

<a href="#top" id="back-to-top">Back to top</a>