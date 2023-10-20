---
title: SQL Queries and Filters
permalink: /sql/
---
# Applying Filters to SQL Queries
{: .no_toc }

{: .note }
Incident Investigation, Data Analysis, Security Event Monitoring, Basic SQL Proficiency
{: .fs-3 }

#### Contents
{: .no_toc }
- TOC
{:toc}

## Scenario
I work as a security professional at a large organization where I investigate security concerns to ensure system safety. Lately, I've come across potential security problems related to login attempts and employee devices. My task involves analyzing data within the employees and log_in_attempts tables. To do this, I'll utilize SQL filters to extract information from various datasets, enabling me to delve into the possible security threats.

## Goals & Objectives
Use SQL filters to retrieve records from different datasets and investigate the potential security issues

## Results
### 📄 Task 1: Retrieve after hours failed login attempts

I need to investigate a potential security incident that occured after business hours. To query the relevant data, I used the following commands:
```sql
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00' AND success = 0
ORDER BY login_time;
```

{: .note2 }
> SELECT with an asterisk returns all columns in the table. FROM specifies which table is being queried. WHERE, along with the proper comparison (>) and logical (AND) operators, filters the displayed results by limiting them to failed login times after 6PM. 
>
> "login_time > 18:00" limits the data to only login times greater than 18:00 (6PM).
>
> In the "success" column of the table, a failed login attempt has a value of 0, and so "success = 0" limits data to only failed login attempts.
>
> ORDER BY organizes the results by login time in descending order.


Terminal output:
{: .fs-3 }
![](/assets/images/sql/step3.png)
<br>
<br>
<br>
### 📄 Task 2: Retrieve login attempts on specific dates
A suspicious event occured on 2022-05-09. To investigate this, I review all login attempts which occured on this day and the day before:
```sql
SELECT *
FROM log_in_attempts
WHERE login_date = '2022-05-09' OR login_date = '2022-05-08';
```

{: .note2 }
WHERE and the OR operator limits the data from the login_date column to either 2022-05-09 or 2022-05-08. With the OR operator, either condition can be met.

Terminal output:
{: .fs-3 }
![](/assets/images/sql/step4.png)