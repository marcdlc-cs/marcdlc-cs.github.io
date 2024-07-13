---
title: Configuring AAA
permalink: /aaa
parent: 🗝️ Identity & Access Mgmt
---
# Configuring AAA
{: .no_toc }

{: .note }
Network Security, Network Configuration and Management, Identity & Access Management, Database Management, Server Configuration, Authentication, Authorization, and Accounting
{: .fs-3 }

#### Contents
{: .no_toc }
- TOC
{:toc}

## Scenario
In this Packet Tracer lab, I will configure authentication and authorization for services within an enterprise network. These services include a RADIUS AAA server, wireless network access, email, and FTP services. 

Authentication and authorization are distinct security processes in the world of identity and access management (IAM). Authentication uses passwords and other identification methods to confirm that users are who they say they are. By contrast, authorization assigns user permissions to the resources that the user is allowed access. 

This configuration will take place on a AAA (Authentication, Authorization, and Accounting) RADIUS (Remote Authentication Dial-In User Service) server. 

Here is an isometric view of the physical office where user endpoints are located:

![](/assets/images/101netplus/aaa_radius/office_isometricview.png)

Note: To keep this lab simple, the passwords for each user account are intentionally weak.

## Objectives

1. Configure user accounts on the RADIUS server 
2. Set up user credentials on employee laptops
3. Activate email services and configure email user accounts
4. Configure the email clients on each employees’s computer
5. Send a test email from PC 1-1
6. Activate the FTP service and conigure FTP user accounts
7. Test FTP server connectivity
8. Verify FTP user privileges are working as configured

## Results
### 📄 Task 1: Set the IP configuration for the hosts

In the wiring closet, I head into the interface of the AAA server. In the configuration panel, I make sure the AAA service is turned on, and then I set up two user accounts with the following credentials:

user1:PASSuser1!

user2:PASSuser2!

![](/assets/images/101netplus/aaa_radius/step1.png)

<br>

### 📄 Task 2: Set up user credentials on employee laptops

Back in the main building, User1 and User2 need to be able to access the wireless network through their laptops. In the wireless configuration panel for each of their laptops, I set up the following:

- SSID: HQ-INT
- Authentication: WPA2
- Username and passwords (from Task 1)
- IP Configuration: DHCP

![](/assets/images/101netplus/aaa_radius/step2.png)

After a few minutes the DHCP server assigns the IP address 192.168.50.4 to HQ-Laptop1 and IP address 192.168.50.2 to HQ-Laptop-2.

<br>

### 📄 Task 3: Activate email services and configure email user accounts

Back in the wiring closet, I access the email server and navigate to the email configuration panel. I make sure that the SMTP and POP3 services are turned on. I setup the email domain to: mail.cyberhq.com. I then setup the following usernames and passwords:

- HQuser1:Cisco123!
- HQuser2:Cisco123~
- BRuser1:Cisco123-
- BRuser2:Cisco123+

![](/assets/images/101netplus/aaa_radius/step3.png)

POP3 (Post Office Protocol version 3) is a protocol used by email clients to retrieve messages from a mail server. It allows users to download their emails from the server to their local devices and then read them offline. SMTP (Simple Mail Transfer Protocol) handles the delivery of emails from the sender's email client to the recipient's email server and then routes them to the recipient's mailbox.
Enabling POP3 and SMTP when setting up an email server for a small business ensures that employees can reliably send and receive emails.

<br>

### 📄 Task 4: Configure the email clients on each employees’s computer

Next, I go to each user’s computer and configure their email clients so they can send and receive emails. For one user’s PC (PC 1-1), I setup the following information in their email client:

- Name: Suk-Yi
- Email Address: HQuser1@mail.cyberhq.com
- Incoming & Outgoing Email Server(s): mail.cyberhq.com
- Username: HQuser1
- Password: Cisco123!

![](/assets/images/101netplus/aaa_radius/step4.png)

I similarly setup the email clients on three additional employee computers.

<br>

### 📄 Task 5: Send a test email from PC 1-1

To confirm that the email clients were setup properly, I send a test email from Suk-Yi’s (HQUser1) computer to another user’s computer (Ajulo) at BRuser1@mail.cyberhq.com. 

![](/assets/images/101netplus/aaa_radius/testemail.png)

Ajulo uses PC 2-3 and I can see that the email from Suk-Yi has been successfully received.

<br>

### 📄 Task 6: Activate the FTP service and conigure FTP user accounts

Back in the wiring closet, I go to the FTP server and navigate the configuration panel. I make sure the FTP service is turned on and I configure the following FTP user accounts, passwords and user privileges:

- Sukyi:cisco123, RWDNL
- Ajulo:cisco321, RWDNL
- Malia:cisco456, RWNL

R = Read, W = Write, D = Delete, N = Rename, L = List

![](/assets/images/101netplus/aaa_radius/ftp_server_config.png)

Suk-Yi and Ajulo will have full user privileges on the FTP server, however, Malia will not be able to delete files from the FTP server.

FTP (File Transfer Protocol) is a standard network protocol used to transfer files between a client and a server over the internet or a local network. It allows users to upload, download, and manage files on a server, making it a critical tool for sharing large files or managing website content.

<br>

### 📄 Task 7: Test FTP server connectivity

To check if I have setup the FTP server properly, I will attempt to download a test file from the FTP server onto Suk-Yi’s computer. From the network administrator’s computer, I connect to the FTP server using the following command:

```ftp 192.168.75.2```

I then login with Suk-Yi’s credentials. I list the files on the FTP server using the dir command. I locate a file called "aMessage.txt" and download it onto Suk-Yi’s computer using the get command.

![](/assets/images/101netplus/aaa_radius/ftp_test_complete.png)

<br>

### 📄 Task 8: Verify FTP user privileges are working as configured

To test if I setup the user privleges on the FTP server properly, I will login using Malia’s account to see if I can delete and rename files. 

First, I  login to the FTP server (192.168.75.2) with Malia’s login credentials. I attempt to delete the aMessage.txt file, but I am unsuccessful. Next, I try to rename aMessage.txt to aMessage_rename.txt and I am successful.

![](/assets/images/101netplus/aaa_radius/ftp_test_privileges.png)

Malia's user privileges on the FTP server are configured correctly.

---

<a href="#top" id="back-to-top">Back to top</a>