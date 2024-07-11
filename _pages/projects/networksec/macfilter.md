---
title: Switch MAC Filtering
permalink: /macfilter
parent: 🔒 Network Security
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
In this Packet Tracer lab, I will be configuring WPA2 and AES on a wireless access point (WAP). WPA2 (Wi-Fi Protected Access 2) and AES (Advanced Encryption Standard) are security protocols used in wireless computer networking to protect data transmitted over Wi-Fi networks. WPA2 is a security protocol that can use AES as its encryption standard.

This is the network topology I will be using:

![](/assets/images/101netplus/71_wpa2aes/topology.png)

## Objectives

1. Configure IP address 192.168.1.1 on the router interface
2. Set the security and wireless settings on the WAP
3. Configure the wireless card settings on the laptop
4. Add the default gateway to the laptop
5. Ping the router from the laptop

## Results
### 📄 Task 1: Configure IP address 192.168.1.1 on the router interface

![](/assets/images/101netplus/71_wpa2aes/router_ipconfig.png)

Interface G0/0 will be assigned the IP address 192.168.1.1. This interface will also serve as the default gateway.

<br>

### 📄 Task 2: Set the security and wireless settings on the WAP

On the WAP, the SSID, pass phrase, authentication method (WPA2), and encryption method (AES) will be set.

![](/assets/images/101netplus/71_wpa2aes/wap_wireless_settings.png)

<br>

### 📄 Task 3: Configure the wireless card settings on the laptop

The wireless card settings on the laptop will match the security and wireless settings of the WAP. If they do not match, the laptop and WAP will not be able to authenticate or communicate with each other.

![](/assets/images/101netplus/71_wpa2aes/laptop_wireless_settings.png)

<br>

### 📄 Task 4: Add the default gateway to the laptop

The laptop is assigned the IP address 192.168.1.2. The default gateway is 192.168.1.1.

![](/assets/images/101netplus/71_wpa2aes/laptop_ipconfig.png)

<br>

### 📄 Task 5: Ping the router from the laptop

To test wireless connectivity, I ping the router from the laptop. 

![](/assets/images/101netplus/71_wpa2aes/laptop_routerping.png)

---

<a href="#top" id="back-to-top">Back to top</a>