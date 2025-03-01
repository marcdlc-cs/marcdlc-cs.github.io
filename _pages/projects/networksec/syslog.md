---
title: Configuring a Syslog Server
permalink: /syslog
parent: 🔒 Network Security
has_toc: false
---
# Configuring a Syslog Server
{: .no_toc }

{: .note }
Network Security, Server Administration, Log Management, Troubleshooting
{: .fs-3 }

#### Contents
{: .no_toc }
- TOC
{:toc}

## Scenario
In this Packet Tracer lab, I will be configuring a syslog server. Syslog is a standard protocol used for logging system messages and events from various devices, like routers, switches, and firewalls. It allows centralized collection of logs from multiple devices.

Centralizing logs from various devices allows security teams to aggregate data, making it easier to analyze and correlate events across the network. Continuous monitoring of log data helps in early detection of security incidents and abnormal activities.

This is the network topology I will be using:

![](/assets/images/101netplus/56_syslog/topology.png)

## Objectives

1. Ensure that the syslog service is turned on
2. Add the IP address of the syslog server to the router
3. Set logging trap debugging
4. Ping the syslog server
5. Observe the logged events

## Results
### 📄 Task 1: Ensure that the syslog service is turned on

In the configuration settings of the server, I make sure the syslog service is turned on.

![](/assets/images/101netplus/56_syslog/syslog_on.png)

<br>

### 📄 Task 2: Add the IP address of the syslog server to the router

In the router, I specify the IP address of the syslog server so that the router knows which server will be creating logs. I used the following command:

```logging host 192.168.1.2```

"Logging host" is referring to the syslog server.

<br>

### 📄 Task 3: Set the logging level

The logging level specifies which logging messages are sent to the syslog server. Cisco Packet Tracer is limited in that it only allows me log debugging events.

To set the logging level, I use the following command:

```logging trap debugging```

<br>

### 📄 Task 4: Ping the syslog server

I ping the syslog server to test its logging functionality.

![](/assets/images/101netplus/56_syslog/router_ping.png)

<br>

### 📄 Task 5: Observe the logged events

Back in the syslog server, each ICMP packet is logged.

![](/assets/images/101netplus/56_syslog/syslog_pinglog.png)

---

<a href="#top" id="back-to-top">Back to top</a>