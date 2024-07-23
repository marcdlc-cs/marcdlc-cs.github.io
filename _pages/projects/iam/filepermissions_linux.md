---
title: File Permissions in Linux
permalink: /permissions
parent: 🗝️ Identity & Access Mgmt
---
# Managing File Permissions in Linux
{: .no_toc }

{: .note }
Access Control, Authorization Assessment, Permission Modification, User Account Management
{: .fs-3 }

#### Contents
{: .no_toc }
- TOC
{:toc}

## Scenario
I am a security professional at a large organization. I mainly work with their research team. Part of my job is to ensure users on this team are authorized with the appropriate permissions. This helps keep the system secure. 

My task is to examine existing permissions on the file system. I’ll need to determine if the permissions match the authorization that should be given. If they do not match, I’ll need to modify the permissions to authorize the appropriate users and remove any unauthorized access.

## Objectives
Modify the permissions to authorize the appropriate users and remove any unauthorized access.

## Results
### 📄 Task 1: Check file and directory details

The ```ls``` command along with the ```-la``` option allowed me to check permissions for all files, including hidden files, and subdirectories. In the output, if a file or directory has “.” in front of it, it means that it is hidden.

Terminal output:
{: .fs-3 }
![](/assets/images/permissions/perm_step3.png)

**Permissions for drafts**
{: .no_toc }

The permissions string for the drafts directory is as follows:

```shell
drwx--x---
```

The permissions string conveys the permissions of each type of user of a file or directory, and whether the item is a directory or a file.

The first character of the string is ```d```, indicating it is a directory and not a file.

The first set of three characters ```rwx``` conveys the permissions for the user, or owner of the file. The first character ```r``` indicates that the user has read permissions. The second character ```w``` indicates that the user has write permissions. The third character ```x``` indicates that the user has execute permissions, or the ability to access the directory and its files.

The second set of three character ```--x``` conveys the permissions for the group. The first two characters are dashes, indicating the group does not have read or write permissions. The last character is an ```x```, indicating that the group has access to the drafts directory.

The last set of three characters ```---``` conveys the permission for all other users on the system. The characters are all dashes which indicates that all other users do not have read, write, or execute permissions for this directory.

<br>
<br>
### 📄 Task 2: Change file permissions

To modify existing permission for a type of user, the ```chmod``` command can be used. 


To remove write permissions for other users from the project_k.txt file, I used the following command: ```chmod o-w project_k.txt```

Terminal output:
{: .fs-3 }
![](/assets/images/permissions/perm_step5.png)

After executing the above command, the permissions string for the project_k.txt file changes to: ```-rw-rw-r--```. The last set of three characters ```r--``` conveys the permissions for other users. The first character ```r``` indicates that other users have read permissions, while the last two dash characters indicate that other users do not have write or execute permissions.

<br>
<br>
### 📄 Task 3: Change file permissions on a hidden file

The hidden file project_x.txt should be readable by both the user and group, but should not be writeable by anyone. To accomplish this, I used the command: ```chmod u-w,g+r,g-w .project_x.txt```. For reference, the initial permissions string for project_x.txt is: ```-rw—w----```

Terminal output:
{: .fs-3 }
![](/assets/images/permissions/perm_step6.png)

In the chmod command, ```u-w``` removes write permissions for the user, ```g+r``` adds read permissions for the group while ```g-w``` removes write permissions for the group. 

The modified permissions string is now: ```-r--r-----```

<br>
<br>
### 📄 Task 4: Change directory permissions

The drafts directory belongs to the researcher2 user. Only researcher2 should be allowed to access the drafts directory and its contents. To display the current permissions string for the directory, the command ```ls -ld drafts``` can be used. The outputted permissions string is: ```drwx--x---```

The ```x``` in the group permissions indicates the group has access to the drafts directory. This permission must be removed. To do this, I used the command ```chmod g-x drafts```. The new permissions string for the drafts directory is: ```drwx------```

Terminal output:
{: .fs-3 }
![](/assets/images/permissions/perm_step7.png)

<br>
<br>
### Summary

To get an overview of the initial permissions of a user on the research team, I used the ```ls``` command and its appropriate options. By utilizing the ```ls``` and ```chmod``` commands throughout this task, I was able grant the correct authorizations to the user, thus strengthening the overall security posture of the organization. 

---

<a href="#top" id="back-to-top">Back to top</a>