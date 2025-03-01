---
title: Common Tasks
permalink: /createuser
parent: 👩‍👧‍👦 Active Directory
has_toc: false
---
# Common Tasks: User and Group Creation, Password Resets, and Disabling Accounts
{: .no_toc }

{: .note }
Active Directory, User Creation, Group Creation, Account Management, Disabling Accounts, Password Resets
{: .fs-3 }

#### Contents
{: .no_toc }
- TOC
{:toc}

## Scenario
In Active Directory, some of the most common tasks are creating users and groups, performing a password reset and disabling accounts. In this project, I will create a user account for Kendrick Morris, a new employee that was just hired. I will then demonstrate all of those common tasks on his account.

## Objectives

1. Create a test OU called "Test OU" and a sub OU called "Domain Users"
2. Create a new User object within Domain Users
3. Login to the new user account
4. Add the new user to a group called "Sales"
5. Perform a password reset
6. Disable the account

## Results
### 📄 Task 1: Create a test OU called "Test OU" and a sub OU called "Domain Users"

In Server Manager, I navigate to Tools > Active Directory Users and Computers. I right-click on the marcdlc.com domain to bring up the context menu and select New > Organizational Unit. I do this twice to create a parent OU and a sub OU called "Test OU" and "Domain Users", respectively. 

![](/assets/images/activedirectory/create_user/createuser/step1.png)

<br>

### 📄 Task 2: Create a new User object within Domain Users

Within Domain Users, I right-click and select New > User. This creates a User object which I configure with the Kendrick's information and login credentials. His username will be: kendrick.morris.

![](/assets/images/activedirectory/create_user/createuser/step2.png)  
![](/assets/images/activedirectory/create_user/createuser/step3.png)
![](/assets/images/activedirectory/create_user/createuser/step3a.png)

Kendrick Morris' account appears within the Domain Users OU.


<br>

### 📄 Task 3: Login to the new user account

To confirm that the new account is working, I log in to Kendrick's account on a domain-joined workstation using the user name and password that I set for his account.

![](/assets/images/activedirectory/create_user/createuser/step4.png)
![](/assets/images/activedirectory/create_user/createuser/step4a.png)

I am able to successfully log in to his account.

<br>

### 📄 Task 4: Add the new user to a group called "Sales"

Kendrick is part of the Sales department, so I will add him to a group called "Sales". To create the Sales group, I right-click in the Domain Users OU and select New > Group.

![](/assets/images/activedirectory/create_user/creategroup/step1.png)
![](/assets/images/activedirectory/create_user/creategroup/step2.png)

To add Kendrick to the Sales group, I right-click on the Sales group and select Properties. In the Members tab I select Add and I search for Kendrick's account to add it to the group.

![](/assets/images/activedirectory/create_user/creategroup/step3.png)


<br>

### 📄 Task 5: Perform a password reset

People will inevitably forget their account passwords and it is the job of the IT support person to perform a password reset so that users can regain access to their accounts. Kendrick forgets his password and requires a password reset. To do this, I right-click on his user object and select Reset Password.

![](/assets/images/activedirectory/create_user/createuser/pwreset1.png)

In the Reset Password panel, I set a temporary password that I will give to Kendrick and I make sure to check "User must change password at next logon". After logging in with the temporary password, Kendrick will be prompted to reset his password. 

![](/assets/images/activedirectory/create_user/createuser/pwreset2.png)


<br>

### 📄 Task 6: Disable the account

Kendrick leaves the company and as a security measure, his account is disabled. In some companies, there may be a policy  in place that states that user accounts must be disabled for a certain period of time (30 days, for example) before being deleted. This is so that if the employee comes back to the company for whatever reason, their account can be easily enabled. 

First, within Test OU I create create a sub OU called "Disabled Users". This allows me to separate disabled accounts from active accounts.

![](/assets/images/activedirectory/create_user/disableaccount/step1.png)

Next, I right-click on the Kendrick's user object and select Disable Account.

![](/assets/images/activedirectory/create_user/disableaccount/step2.png)
![](/assets/images/activedirectory/create_user/disableaccount/step3.png)

Then I move his account to the Disabled Users OU.

![](/assets/images/activedirectory/create_user/disableaccount/step4.png)

To verify that his account is disabled, I attempt to log in to his account from another workstation. I am unable to log in because his account is disabled.

![](/assets/images/activedirectory/create_user/disableaccount/step5.png)


---

<a href="#top" id="back-to-top">Back to top</a>