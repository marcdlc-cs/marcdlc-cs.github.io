---
title: VLAN Mismatch
permalink: /vlanmismatch
parent: 🔧 Network Troubleshooting
---
# Troubleshooting a VLAN Mismatch
{: .no_toc }

{: .note }
Network Security, Router Configuration, Access Management, Troubleshooting
{: .fs-3 }

#### Contents
{: .no_toc }
- TOC
{:toc}

## Scenario
In the Packet Tracer lab, I will be troubleshooting a VLAN mismatch between two switches. A VLAN mismatch occurs when there is a discrepancy between the VLAN configurations on two connected network devices, typically switches, that are communicating over a trunk link. This mismatch can lead to various network issues, including connectivity problems, security vulnerabilities, and degraded network performance.

This is the network topology I will be using:

![](/assets/images/101netplus/96_vlanmismatch/topology.png)

## Objectives

1. Create a VLAN mismatch in Switch0
2. Verify the native VLAN on Switch0
3. Configure both switches to use the same VLAN

## Results
### 📄 Task 1: Create a VLAN mismatch in Switch0

VLAN mismatches occur when two switch communicating over a trunk link utilize different VLANs on either end of the link. Trunk-linked switches must use the same VLAN. To create a VLAN mismatch, I will configure Switch0 to use VLAN 10 instead of the default VLAN 1 as its native VLAN.

![](/assets/images/101netplus/96_vlanmismatch/switch0_mismatch.png)

CDP generates an error message stating that it detects a VLAN mismatch on Switch0's F0/1 interface.

<br>

### 📄 Task 2: Verify the native VLAN on Switch0

I will issue two CiscoIOS commands that will help me find out what native VLAN is assigned to port F0/1 on Swithc0:

```show interfaces trunk```

```show interfaces g0/1 switchport```

![](/assets/images/101netplus/96_vlanmismatch/switch0_vlan10.png)

The output shows that VLAN 10 is assigned to interface F0/1.

<br>

### 📄 Task 3: Configure both switches to use the same VLAN

To resolve the VLAN mismatch, I will configure interface F0/1 of Switch1 to VLAN 10, matching the VLAN used on the interface of Switch0.

![](/assets/images/101netplus/96_vlanmismatch/switch1_vlan10.png)

---

<a href="#top" id="back-to-top">Back to top</a>