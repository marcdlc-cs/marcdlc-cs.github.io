---
title: Desktop Background GPO
permalink: /gpo_desktopbg
parent: 👩‍👧‍👦 Active Directory
has_toc: false
---
# Applying a Desktop Background GPO to a Domain
{: .no_toc }

{: .note }
Active Directory, Group Policy Management, Group Policy Creation, File Shares
{: .fs-3 }

#### Contents
{: .no_toc }
- TOC
{:toc}

## Scenario
A group policy is a feature used to centrally manage and configure settings for users and computers within an AD domain. It enables administrators to enforce specific policies across the network, ensuring consistency and compliance. In this project, I will create a group policy that configures a desktop background consistently across all user workstations. This group policy will be linked to the domain so that it applies to all users within that domain.

I will be using the following desktop background:

![](/assets/images/activedirectory/gpo_desktopbg/desktopbg_sm.png)

## Objectives

1. Create a file share that contains the desktop background
2. Verify that the file share is accessible
3. Create a Desktop Background GPO and link it to the domain
4. Configure the GPO
5. Update all group policy settings
6. Verify that the GPO is working as intended

## Results
### 📄 Task 1: Create a file share that contains the desktop background

First, I create a file share that contains the desktop background image. This allows all workstations within the domain to access the image file from a centralized location. I create a folder named "Desktop Backgrounds" and I place the image file inside of it. To make it a file share, I right-click on the folder and select Properties > Sharing > Advanced Sharing. In Advanced Sharing, I check "Share this folder" and I name it "Desktop Backgrounds".

![](/assets/images/activedirectory/gpo_desktopbg/step1.png)

I only want this file share to be accessible by authenticated users. To do this, in the Advanced Sharing panel, I press the Permissions button. I add the Authenticated Users group object and I make sure that it only has Read permissions. 

![](/assets/images/activedirectory/gpo_desktopbg/step2.png)


<br>

### 📄 Task 2: Verify that the file share is accessible

I need to verify that the file share is accessible by authenticated users. To do this, I log in to a user's account from another workstation. I open File Explorer and type in the UNC for the file share: \\\\ADUD01MARCDLC\

![](/assets/images/activedirectory/gpo_desktopbg/step3.png)

I can see that the file share is accessible. 


<br>

### 📄 Task 3: Create a Desktop Background GPO and link it to the domain

In Server Manager, I navigate to Tools > Group Policy Management. I right-click the marcdlc.com to create a GPO and link it to the domain. This allows me to apply the GPO to all users in the marcdlc.com domain. I name it "Desktop Background".

![](/assets/images/activedirectory/gpo_desktopbg/step4.png)  

![](/assets/images/activedirectory/gpo_desktopbg/step5.png)


<br>

### 📄 Task 4: Configure the GPO

To set the specific policies in the Desktop Background GPO, I right-click it and select Edit. This brings up the Group Policy Management Editor. I navigate to User Configuration > Policies > Administrative Templates > Desktop > Desktop > Desktop Wallpaper. I right-click Desktop Wallpaper and select Edit. 

![](/assets/images/activedirectory/gpo_desktopbg/step6.png)

In the Desktop Wallpaper settings, I make sure that Enabled is selected. Then, I enter the UNC for the desktop background image file: \\\\ADUD01MARCDLC\Desktop Backgrounds\bg_nature.jpg

![](/assets/images/activedirectory/gpo_desktopbg/step7.png)


<br>

### 📄 Task 5: Update all group policy settings

To update the group policy settings, I open a command prompt and use the command ``gpupdate /force``.

![](/assets/images/activedirectory/gpo_desktopbg/step8.png)

To verify that the GPO has been applied, I run the command ``gpresult /r`` which outputs all of the applied GPOs. I see that the Desktop Background GPO appears under "Applied Group Policy Objects".

![](/assets/images/activedirectory/gpo_desktopbg/step9.png)


<br>

### 📄 Task 6: Verify that the GPO is working as intended

I log in to another workstation to check if the desktop background has been changed.

![](/assets/images/activedirectory/gpo_desktopbg/step10.png)


---

<a href="#top" id="back-to-top">Back to top</a>