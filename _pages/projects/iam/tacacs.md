---
title: Configuring a TACACS+ Server
permalink: /tacacs
parent: 🔒 Network Security
---
# Configuring a TACACS+ Server
{: .no_toc }

{: .note }
Network Security, Network Configuration and Management, Identity & Access Management, Switch Configuration, Server Configuration, Authentication, Authorization, and Accounting
{: .fs-3 }

#### Contents
{: .no_toc }
- TOC
{:toc}

## Scenario
In this Packet Tracer lab, I will configure a AAA server to use TACACS+ to control user access to network equipment. The TACACS+ server will be used to authenticate a user to connect to a multilayer switch. 

TACACS+ (Terminal Access Controller Access-Control System Plus) is a security protocol used in computer networking to provide centralized authentication, authorization, and accounting (AAA) services for users who access a network. It is an enhancement of the earlier TACACS protocol and is primarily used for managing and controlling access to network devices like routers, switches, and firewalls.

TACACS+ was developed by Cisco Systems, and it is closely associated with Cisco's network equipment. It differs from RADIUS in that it offers enhanced network security, allows for more granular control and flexibility over AAA processes, and is widely used in managing network devices.

This is the network topology I will be using:

![](/assets/images/101netplus/69_tacacs/topology.png)

## Objectives

1. Configure IP information for the PC, VLAN 1, and TACACS+ server
2. Configure AAA on the switch
3. Create a key string called "marcdlckey"
4. Enable the AAA service on the TACACS+ server
5. Specify which tasks are allowed on the switch
6. Enable AAA debugging and then Telnet into the switch

## Results
### 📄 Task 1: Configure IP information for the PC, VLAN 1, and TACACS+ server

I set the IP address of the PC to 10.1.1.1, subnet mask to 255.0.0.0, and default gateway to 10.1.1.20. 

![](/assets/images/101netplus/69_tacacs/pc_ipconfig.png)

On the switch, I configure the IP address 10.1.1.20 for VLAN 1. 

![](/assets/images/101netplus/69_tacacs/switch_vlan1_ipconfig.png)

On the AAA server, I assign the IP address 10.1.1.10 and subnet mask of 255.0.0.0.

![](/assets/images/101netplus/69_tacacs/server_ipconfig.png)

<br>

### 📄 Task 2: Configure AAA on the switch

I use the following CiscoIOS commands to configure AAA on the switch:

![](/assets/images/101netplus/69_tacacs/aaa_config_switch.png)

I create a local username and password of "marcdlc" as a fallback in case the TACACS+ server is not available. I then set the password to go into privileged EXEC mode for the switch to "mycisco".

Next, I specify that authentication for remote login attempts to the switch should first try TACACS+ (using the tacacs+ group), and if TACACS+ is unavailable, it falls back to the local database (local). 

For virtual terminal lines 0 through 15 (which control remote access to the switch), I apply the "myauth" authentication method list which uses the TACACS+ server.


<br>

### 📄 Task 3: Create a key string called "marcdlckey"

The key string is used to authenticate and authorize communication between the client (switch) and the TACACS+ server. When the client sends authentication requests to the TACACS+ server, it includes this key string as part of the authentication process. This ensures that only authorized clients (those with the correct key string configured) can communicate with the TACACS+ server.

![](/assets/images/101netplus/69_tacacs/createkey.png)

The key string also serves to encrypt communication between the switch and the server, adding another layer of security.

<br>

### 📄 Task 4: Enable the AAA service on the TACACS+ server

On the server, I make sure that the AAA service is turned on. I also add the client information for the switch which includes its IP address, server type (TACACS+) and key. Then, I add the username and password of "marcdlc" so that the switch can authenticate users against it.

![](/assets/images/101netplus/69_tacacs/server_tacacsconfig.png)

<br>

### 📄 Task 5: Specify which tasks are allowed on the switch

The user should be allowed to go into EXEC mode. The following commands tell the switch to authorize executive level access using the TACACS+ server. If the server fails to respond, the switch should fall back to local authorization using the locally configured credentials (marcdlc:marcdlc) on the switch itself.

![](/assets/images/101netplus/69_tacacs/switch_allowedtasks.png)

<br>

### 📄 Task 6: Enable AAA debugging and then Telnet into the switch

To enable AAA debugging on the switch, I use the command:

![](/assets/images/101netplus/69_tacacs/switch_aaadebug.png)

The switch will start to generate verbose output regarding AAA processes. This output includes detailed information about authentication attempts, authorization decisions, and accounting activities.

Next, I attempt to Telnet into the switch from the PC:

![](/assets/images/101netplus/69_tacacs/pc_telnet.png)

My login attempt is successfully authenticated by the TACACS+ server and I am allowed to go into privileged EXEC mode.


---

<a href="#top" id="back-to-top">Back to top</a>